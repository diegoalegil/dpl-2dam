# Práctica guiada: acceso remoto por SSH con claves

En esta práctica configuro desde cero el acceso remoto por SSH a una máquina Linux recién instalada. Primero me conecto con contraseña, después con un par de claves y al final dejo deshabilitada la contraseña, de forma que solo se pueda entrar con clave.

Voy documentando cada paso con los comandos que ejecuto y su salida real, y hago un commit por cada paso. Cuando algo falla, lo apunto con la causa y cómo lo he solucionado.

## Documentación de referencia

- [PR #34](https://github.com/monium/gitanddocs/pull/34): "Acceso SSH solo con clave (sin contraseña) en un servidor" (`docs/seguridad-servidor/conexion-ssh.md`).
- [Issue #32](https://github.com/monium/gitanddocs/issues/32): práctica guiada del profe, en la rama `issue-32` (`docs/ssh/connect-to-machine.md` y `docs/ssh/create-ssh-key.md`).

## Entorno

| Papel | Máquina | Detalles |
|---|---|---|
| Cliente | Mi equipo | Linux Mint 22.3 (máquina virtual de VirtualBox), OpenSSH 9.6p1 |
| Servidor | Contenedor Docker `servidor-ssh` | Debian 13 (trixie), imagen oficial `debian:trixie` recién descargada |
| | Docker | 29.1.3 |

**Por qué un contenedor y no una máquina virtual:** mi Linux Mint ya es una máquina virtual de VirtualBox y no tiene la virtualización anidada activada (`systemd-detect-virt` dice `oracle` y no existe `/dev/kvm`). Una máquina virtual dentro de otra con QEMU sin aceleración iría lentísima. Un contenedor con la imagen oficial de Debian es un sistema mínimo recién instalado: no trae ni SSH ni `sudo`, y hay que instalarlo y configurarlo todo a mano. La guía del profe de la rama `issue-32` también lo hace así.

Diferencias con una máquina real que tengo que tener en cuenta:
- En el contenedor no hay `systemd`, así que los servicios se manejan con `service` en vez de `systemctl`.
- No me conecto a una IP en el puerto 22, sino a `127.0.0.1` en el puerto `2222`, que Docker redirige al 22 del contenedor.

## Datos que uso

| Dato | Valor |
|---|---|
| Nombre del contenedor y hostname | `servidor-ssh` |
| Usuario en el servidor | `usuario` |
| Conexión | `127.0.0.1`, puerto `2222` |
| Clave de la práctica | `~/.ssh/id_ed25519_dpl` |

Para la práctica uso una clave nueva y no la `~/.ssh/id_ed25519` que ya tengo, porque esa es la que uso con GitHub y no quiero mezclarlas.

## Pasos

1. Crear la máquina recién instalada
2. Instalar el servidor SSH
3. Arrancar el servicio y comprobar que escucha
4. Crear el usuario y primera conexión con contraseña
5. Generar el par de claves en el cliente
6. Copiar la clave pública al servidor
7. Comprobar el acceso con clave
8. Deshabilitar la autenticación por contraseña
9. Verificación final

Después: análisis de errores, errores típicos provocados a propósito, comparación con la documentación de referencia y conclusiones.

## Organización

- `README.md`: este informe.
- `evidencias/`: la salida completa de los comandos de cada paso, tal cual salió en la terminal.

---

## Paso 1: Crear la máquina recién instalada

Descargo la imagen oficial de Debian 13 y arranco el contenedor que hará de servidor:

```bash
docker pull debian:trixie
docker run -d --name servidor-ssh --hostname servidor-ssh -p 2222:22 debian:trixie sleep infinity
```

| Parte | Para qué |
|---|---|
| `-d` | Arranca en segundo plano |
| `--name servidor-ssh` | Nombre del contenedor para referirme a él |
| `--hostname servidor-ssh` | Nombre de la máquina por dentro. Así en la terminal sé en qué máquina estoy |
| `-p 2222:22` | El puerto 2222 de mi equipo va al 22 del contenedor, que es el de SSH |
| `sleep infinity` | Proceso que no hace nada pero mantiene el contenedor encendido |

Compruebo que está encendido y que el puerto está publicado:

```text
$ docker port servidor-ssh
22/tcp -> 0.0.0.0:2222
22/tcp -> [::]:2222
```

Entro en la consola de la máquina, que es como estar sentado delante de ella. Esta terminal la dejo abierta durante toda la práctica, porque si rompo el SSH es mi forma de entrar a arreglarlo:

```bash
docker exec -it servidor-ssh bash
```

Dentro compruebo qué sistema es y que de verdad está "recién instalado":

```text
root@servidor-ssh:/# cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 13 (trixie)"
...
root@servidor-ssh:/# which ssh sshd sudo
root@servidor-ssh:/# sudo apt update
bash: line 1: sudo: command not found
root@servidor-ssh:/# ls /etc/ssh
ls: cannot access '/etc/ssh': No such file or directory
```

- `which` no devuelve nada: no hay ni cliente ni servidor SSH.
- No existe `sudo`. En la consola soy `root`, así que de momento no me hace falta.
- No existe `/etc/ssh`, así que todavía no hay ninguna configuración de SSH.
- Solo hay 78 paquetes instalados (`dpkg -l | grep -c '^ii'`).

Para tener una referencia de cómo falla, intento conectarme desde mi equipo antes de instalar nada:

```text
diego@diego:~$ ssh -p 2222 usuario@127.0.0.1
kex_exchange_identification: read: Connection reset by peer
Connection reset by 127.0.0.1 port 2222
```

**Primer error y por qué sale este y no otro:** esperaba un `Connection refused`, que es lo que pone en la guía de referencia cuando el servidor SSH no está arrancado. Pero sale `Connection reset by peer`. La causa es que el puerto 2222 de mi equipo sí está abierto, porque lo abre Docker para redirigirlo. Docker acepta la conexión, intenta pasarla al puerto 22 del contenedor, ahí no escucha nadie y corta. En una máquina real sin SSH sí saldría `Connection refused`. Esto me sirve luego para reconocer el fallo: si veo `kex_exchange_identification` justo al conectar, el problema está en el servidor y no en mis claves.

Evidencia completa: [evidencias/01-maquina-recien-instalada.txt](evidencias/01-maquina-recien-instalada.txt)

---

## Paso 2: Instalar el servidor SSH

Desde la consola de la máquina actualizo la lista de paquetes e instalo el servidor SSH y `sudo`:

```bash
apt update
apt install -y openssh-server sudo
```

- `openssh-server` es el servidor (`sshd`), el programa que atiende las conexiones.
- `sudo` lo instalo porque en Debian, si al instalar se pone contraseña a root, no viene. Lo voy a necesitar para administrar la máquina desde mi usuario normal cuando entre por SSH.

`apt` instala 58 paquetes, porque `openssh-server` arrastra dependencias, entre ellas `systemd`:

```text
Summary:
  Upgrading: 0, Installing: 58, Removing: 0, Not Upgrading: 1
  Download size: 15.9 MB
  Space needed: 55.4 MB / 80.7 GB available
```

Durante la instalación salen estas líneas:

```text
invoke-rc.d: could not determine current runlevel
invoke-rc.d: policy-rc.d denied execution of start.
```

No es un fallo de la instalación. Las imágenes de Docker traen un script, `/usr/sbin/policy-rc.d`, que termina con `exit 101` y le prohíbe a `apt` arrancar servicios al instalarlos. En una máquina Debian normal, el servicio SSH se quedaría arrancado nada más instalarlo. Aquí lo tendré que arrancar a mano en el paso 3.

Compruebo qué ha dejado la instalación:

```text
root@servidor-ssh:/# which ssh sshd sudo
/usr/bin/ssh
/usr/sbin/sshd
/usr/bin/sudo

root@servidor-ssh:/# ls -l /etc/ssh
-rw-r--r-- 1 root root 592383 May  6 12:33 moduli
-rw-r--r-- 1 root root   1668 May  6 12:33 ssh_config
drwxr-xr-x 2 root root   4096 Oct 26 19:09 ssh_config.d
-rw------- 1 root root    513 Oct 26 19:09 ssh_host_ecdsa_key
-rw-r--r-- 1 root root    179 Oct 26 19:09 ssh_host_ecdsa_key.pub
-rw------- 1 root root    411 Oct 26 19:09 ssh_host_ed25519_key
-rw-r--r-- 1 root root     99 Oct 26 19:09 ssh_host_ed25519_key.pub
-rw------- 1 root root   2602 Oct 26 19:09 ssh_host_rsa_key
-rw-r--r-- 1 root root    571 Oct 26 19:09 ssh_host_rsa_key.pub
-rw-r--r-- 1 root root   3424 May  6 12:33 sshd_config
drwxr-xr-x 2 root root   4096 May  6 12:33 sshd_config.d
```

| Archivo | Qué es |
|---|---|
| `sshd_config` | Configuración del servidor |
| `sshd_config.d/` | Carpeta para añadir configuración en archivos aparte. Ahora está vacía |
| `ssh_config` | Configuración del cliente `ssh` de esta máquina (no la del servidor) |
| `ssh_host_*_key` y `.pub` | Las claves propias de la máquina. Son como su DNI: el cliente las usa para comprobar que se conecta siempre a la misma máquina. Se han creado al instalar (19:09). Las privadas tienen permisos `600` y solo las puede leer root |

En `sshd_config` me fijo en lo que voy a tocar más adelante:

```text
12:Include /etc/ssh/sshd_config.d/*.conf
33:#PermitRootLogin prohibit-password
38:#PubkeyAuthentication yes
57:#PasswordAuthentication yes
64:KbdInteractiveAuthentication no
87:UsePAM yes
```

- Las líneas con `#` están comentadas y muestran el valor por defecto. Por defecto **se permite la contraseña** (`PasswordAuthentication yes`) y también la clave pública.
- `PermitRootLogin prohibit-password`: root solo podría entrar con clave, nunca con contraseña.
- El `Include` de la línea 12 está **al principio**. Esto es importante para el paso 8: lo que ponga en `sshd_config.d/` se lee antes que el resto del archivo, y en `sshd_config` gana el primer valor que se lee de cada opción.

También se crea el usuario del sistema `sshd`, que no puede iniciar sesión (`/usr/sbin/nologin`). El servidor lo usa para aislar la parte que habla con la red y no hacerlo todo como root.

La versión del servidor es `OpenSSH_10.0p2 Debian-7+deb13u4`, más nueva que la de mi cliente (`OpenSSH_9.6p1`).

Evidencia completa (con la salida entera de `apt`): [evidencias/02-instalar-ssh.txt](evidencias/02-instalar-ssh.txt)

---

## Paso 3: Arrancar el servicio y comprobar que escucha

En una máquina normal se arranca con `systemctl`, que es lo que pone el PR #34. Lo pruebo:

```text
root@servidor-ssh:/# systemctl start ssh
System has not been booted with systemd as init system (PID 1). Can't operate.
Failed to connect to system scope bus via local transport: Host is down
```

**Error:** `systemctl` habla con `systemd`, pero en el contenedor el proceso número 1 es `sleep infinity` y no `systemd`. Aunque `systemd` se instaló como dependencia en el paso 2, no está funcionando. **Solución:** usar `service`, que llama directamente al script de arranque `/etc/init.d/ssh`:

```text
root@servidor-ssh:/# service ssh status
sshd is not running ... failed!

root@servidor-ssh:/# service ssh start
Starting OpenBSD Secure Shell server: sshd.

root@servidor-ssh:/# service ssh status
sshd is running.
```

Equivalencias que voy a usar en toda la práctica:

| Acción | Máquina real (systemd) | Contenedor |
|---|---|---|
| Arrancar | `sudo systemctl start ssh` | `service ssh start` |
| Estado | `sudo systemctl status ssh` | `service ssh status` |
| Recargar configuración | `sudo systemctl reload ssh` | `service ssh reload` |
| Reiniciar | `sudo systemctl restart ssh` | `service ssh restart` |
| Que arranque al encender | `sudo systemctl enable ssh` | No aplica: el contenedor no tiene arranque del sistema |

Compruebo que el proceso está en marcha y en qué puerto escucha. `ss` no viene instalado (`bash: line 1: ss: command not found`), así que instalo `iproute2`:

```text
root@servidor-ssh:/# ps -ef | grep [s]shd
root        1064       1  0 19:16 ?        00:00:00 sshd: /usr/sbin/sshd [listener] 0 of 10-100 startups

root@servidor-ssh:/# apt install -y iproute2
root@servidor-ssh:/# ss -tlnp
State  Recv-Q Send-Q Local Address:Port Peer Address:PortProcess
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=1064,fd=6))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=1064,fd=7))
```

`sshd` escucha en el puerto 22 en todas las interfaces, tanto IPv4 (`0.0.0.0`) como IPv6 (`[::]`).

### Logs del servidor

En una máquina real los logs de SSH se ven con `sudo journalctl -u ssh`. Aquí no hay `journald` ni `rsyslog` funcionando, así que los mensajes de `sshd` se perderían. Para poder ver qué pasa cuando algo falle, hago que `sshd` escriba sus logs en un fichero con la opción `-E`. El script de arranque lee las opciones de `/etc/default/ssh`:

```text
root@servidor-ssh:/# sed -i 's|^SSHD_OPTS=.*|SSHD_OPTS="-E /var/log/sshd.log"|' /etc/default/ssh
root@servidor-ssh:/# service ssh restart
Restarting OpenBSD Secure Shell server: sshd.
root@servidor-ssh:/# cat /var/log/sshd.log
Server listening on 0.0.0.0 port 22.
Server listening on :: port 22.
```

### Prueba desde mi equipo

Ahora desde mi equipo, el puerto 2222 ya contesta con el saludo del servidor SSH. Antes la conexión se cortaba:

```text
diego@diego:~$ nc -w 2 127.0.0.1 2222
SSH-2.0-OpenSSH_10.0p2 Debian-7+deb13u4
```

Con `ssh-keyscan` veo las claves públicas que me enseña la máquina, las mismas `ssh_host_*_key.pub` del paso 2:

```text
diego@diego:~$ ssh-keyscan -p 2222 127.0.0.1
[127.0.0.1]:2222 ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCVKV5z4a4I...
[127.0.0.1]:2222 ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAI...
[127.0.0.1]:2222 ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAILPy7SFFAEGUtca9bnGrTwgP0c608q3SMZ9ECAnlGKyI
```

Evidencia completa: [evidencias/03-arrancar-servicio.txt](evidencias/03-arrancar-servicio.txt)

---

## Paso 4: Crear el usuario y primera conexión con contraseña

No me voy a conectar como root. Debian ya lo bloquea por defecto (`PermitRootLogin prohibit-password`, visto en el paso 2) y, además, lo correcto es entrar con un usuario normal y usar `sudo` solo cuando haga falta. En la consola creo el usuario:

```text
root@servidor-ssh:/# adduser usuario
New password:
Retype new password:
passwd: password updated successfully
Changing the user information for usuario
Enter the new value, or press ENTER for the default
	Full Name []:
	...
Is the information correct? [Y/n] Y
```

Le pongo una contraseña (no la apunto aquí) y dejo el resto de datos en blanco. Después lo meto en el grupo `sudo` para que pueda administrar la máquina:

```text
root@servidor-ssh:/# adduser usuario sudo
root@servidor-ssh:/# id usuario
uid=1000(usuario) gid=1000(usuario) groups=1000(usuario),27(sudo),100(users)
```

Antes de conectarme apunto la huella de la clave ED25519 de la máquina. Así, cuando el cliente me pregunte si me fío, puedo comprobar que es la misma y que no me está suplantando nadie:

```text
root@servidor-ssh:/# ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub
256 SHA256:R+jid5pFW9XZePboDEaB5rfDJjD43xGFiQPnwOT67ws root@servidor-ssh (ED25519)
```

Desde mi equipo, en otra terminal, hago la primera conexión:

```text
diego@diego:~$ ssh -p 2222 usuario@127.0.0.1
The authenticity of host '[127.0.0.1]:2222 ([127.0.0.1]:2222)' can't be established.
ED25519 key fingerprint is SHA256:R+jid5pFW9XZePboDEaB5rfDJjD43xGFiQPnwOT67ws.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[127.0.0.1]:2222' (ED25519) to the list of known hosts.
usuario@127.0.0.1's password:
Linux servidor-ssh 7.0.0-38-generic #38~24.04.4-Ubuntu SMP PREEMPT_DYNAMIC Mon Sep 14 16:37:11 UTC 2 x86_64
...
usuario@servidor-ssh:~$ whoami; hostname; pwd
usuario
servidor-ssh
/home/usuario
usuario@servidor-ssh:~$ exit
logout
Connection to 127.0.0.1 closed.
```

- La huella que me enseña (`SHA256:i5CZ...JMM`) es la misma que he visto en la consola, así que respondo `yes`.
- Me pide la contraseña del usuario del servidor y entro.
- El kernel que sale es el de mi Linux Mint (`7.0.0-38-generic ... Ubuntu`). Es normal: un contenedor usa el kernel del equipo anfitrión. Lo que es Debian es todo lo demás.

En el log del servidor queda registrado que he entrado **con contraseña**:

```text
Accepted password for usuario from 172.17.0.1 port 59022 ssh2
```

La IP `172.17.0.1` es la de mi equipo vista desde la red de Docker.

### Dónde se guarda la huella: known_hosts

Al responder `yes`, el cliente guarda la clave de la máquina en `~/.ssh/known_hosts`. Las próximas veces la compara y, si cambia, avisa (lo provoco en el apartado de errores). Quise comprobarlo con `grep`, pero no lo encuentra:

```text
diego@diego:~$ grep -c '\[127.0.0.1\]:2222' ~/.ssh/known_hosts
0
```

**Por qué:** en Linux Mint (igual que en Ubuntu) el cliente tiene `HashKnownHosts yes`, así que en `known_hosts` no se guarda el nombre del servidor en claro, sino un hash. Así, si alguien me roba el archivo, no sabe a qué servidores me conecto. La forma correcta de buscarlo es con `ssh-keygen -F`:

```text
diego@diego:~$ ssh-keygen -F '[127.0.0.1]:2222' -l
# Host [127.0.0.1]:2222 found: line 4
[127.0.0.1]:2222 ED25519 SHA256:R+jid5pFW9XZePboDEaB5rfDJjD43xGFiQPnwOT67ws
# Host [127.0.0.1]:2222 found: line 5
[127.0.0.1]:2222 RSA SHA256:JjDCW/CBPtUgknu7pB5MHjjl+aqDRSei/WUfTQ9d/2M
# Host [127.0.0.1]:2222 found: line 6
[127.0.0.1]:2222 ECDSA SHA256:J+HWctrnxVx5uIWS0MMiI8tSQZfwg1mSxkbx6mwNd3U
```

Aunque solo acepté la ED25519, el cliente ha guardado también la RSA y la ECDSA. Lo hace la opción `UpdateHostKeys`: cuando la conexión ya es de confianza, el servidor le pasa el resto de sus claves.

Evidencia completa: [evidencias/04-usuario-y-contrasena.txt](evidencias/04-usuario-y-contrasena.txt)

---

## Paso 5: Generar el par de claves en el cliente

Esto se hace **en mi equipo**, no en el servidor. La clave privada nunca tiene que salir de la máquina desde la que me conecto.

Antes miro qué tengo en `~/.ssh` para no pisar nada:

```text
diego@diego:~$ ls -l ~/.ssh
-rw------- 1 diego diego  411 oct  6 16:00 id_ed25519
-rw-r--r-- 1 diego diego  103 oct  6 16:00 id_ed25519.pub
-rw------- 1 diego diego 1956 oct 26 19:23 known_hosts
-rw------- 1 diego diego 1120 oct 26 19:23 known_hosts.old
```

Ya tengo una `id_ed25519`, la de GitHub. Si ejecutara `ssh-keygen` sin más, me preguntaría si quiero sobrescribirla y, si dijera que sí, dejaría de funcionarme GitHub. Por eso genero la de la práctica con otro nombre usando `-f`:

```text
diego@diego:~$ ssh-keygen -t ed25519 -C "diego@practica-ssh" -f ~/.ssh/id_ed25519_dpl
Generating public/private ed25519 key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/diego/.ssh/id_ed25519_dpl
Your public key has been saved in /home/diego/.ssh/id_ed25519_dpl.pub
The key fingerprint is:
SHA256:v6WT/8kWeX9+c57VmgxQuErEwTm2t8mvZwLTltUo/14 diego@practica-ssh
The key's randomart image is:
+--[ED25519 256]--+
|       ...       |
|       .=. .     |
|       .oo. .o   |
|       .. ooo .  |
|        S+oB   . |
|       .ooB.. o o|
|        .+.oo. oE|
|          ++++o*B|
|          +B.+O+B|
+----[SHA256]-----+
```

| Opción | Para qué |
|---|---|
| `-t ed25519` | Tipo de clave. ED25519 es la recomendada hoy: segura, rápida y corta. RSA solo si hay que conectar con equipos muy antiguos (y entonces `-b 4096`) |
| `-C "diego@practica-ssh"` | Comentario que va al final de la clave pública. Sirve para saber de quién es cuando en el servidor haya varias |
| `-f ~/.ssh/id_ed25519_dpl` | Dónde guardarla. Así no piso la clave que ya tengo |

**Le pongo passphrase.** Es una contraseña que cifra la clave privada dentro del archivo. Si alguien me copia `id_ed25519_dpl`, sin la passphrase no le sirve. Se nota en el tamaño: mi clave de GitHub (sin passphrase) ocupa 411 bytes y esta 464, porque va cifrada. Ojo: esta passphrase no es la contraseña del usuario del servidor. Es solo para desbloquear mi clave en mi equipo.

Resultado:

```text
diego@diego:~$ ls -l ~/.ssh
-rw------- 1 diego diego  464 oct 26 19:29 id_ed25519_dpl
-rw-r--r-- 1 diego diego  100 oct 26 19:29 id_ed25519_dpl.pub
...
diego@diego:~$ cat ~/.ssh/id_ed25519_dpl.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAID1cLOG0rlW8cgerCMLxkr20hMuX2luRs4fGpo3sz1gf diego@practica-ssh
```

| Archivo | Qué es | Permisos |
|---|---|---|
| `id_ed25519_dpl` | Clave **privada**. No se comparte nunca | `600`: solo yo la puedo leer. `ssh-keygen` ya la crea así |
| `id_ed25519_dpl.pub` | Clave **pública**. Es la que va al servidor y se puede enseñar sin problema | `644` |

Apunto la huella de mi clave para luego comprobar en el servidor que la que ha llegado es esta:

```text
diego@diego:~$ ssh-keygen -lf ~/.ssh/id_ed25519_dpl.pub
256 SHA256:v6WT/8kWeX9+c57VmgxQuErEwTm2t8mvZwLTltUo/14 diego@practica-ssh (ED25519)
```

Evidencia completa: [evidencias/05-generar-claves.txt](evidencias/05-generar-claves.txt)

---

## Paso 6: Copiar la clave pública al servidor

Para que el servidor me deje entrar con mi clave, la clave **pública** tiene que estar en el archivo `~/.ssh/authorized_keys` del usuario con el que entro (`/home/usuario/.ssh/authorized_keys`). La forma más cómoda es `ssh-copy-id`, que se conecta con contraseña una última vez y la añade:

```text
diego@diego:~$ ssh-copy-id -i ~/.ssh/id_ed25519_dpl.pub -p 2222 usuario@127.0.0.1
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/diego/.ssh/id_ed25519_dpl.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
usuario@127.0.0.1's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh -p 2222 'usuario@127.0.0.1'"
and check to make sure that only the key(s) you wanted were added.
```

Qué hace por dentro:
1. Primero intenta entrar con la clave para ver si ya estaba instalada y no duplicarla. En el log del servidor sale como `Connection closed by authenticating user usuario ... [preauth]`, que es ese intento fallido.
2. Como no estaba, entra con la contraseña del usuario.
3. Crea `~/.ssh` si no existe, añade la clave a `authorized_keys` y pone los permisos bien.

**Ojo con el `-i`:** le paso la `.pub` de la práctica. Sin `-i`, `ssh-copy-id` copia todas las claves que tenga cargadas el agente (`ssh-add -L`) y, si no hay ninguna, la `~/.ssh/id*.pub` más reciente (lo pone en `man ssh-copy-id`). Con dos claves en `~/.ssh` es fácil acabar copiando al servidor la que no toca, por ejemplo la de GitHub. Con `-i` no hay dudas.

Compruebo en la consola del servidor que ha quedado bien:

```text
root@servidor-ssh:/# ls -la /home/usuario/.ssh
drwx------ 2 usuario usuario 4096 Oct 26 19:36 .
drwx------ 3 usuario usuario 4096 Oct 26 19:36 ..
-rw------- 1 usuario usuario  100 Oct 26 19:36 authorized_keys

root@servidor-ssh:/# cat /home/usuario/.ssh/authorized_keys
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAID1cLOG0rlW8cgerCMLxkr20hMuX2luRs4fGpo3sz1gf diego@practica-ssh

root@servidor-ssh:/# ssh-keygen -lf /home/usuario/.ssh/authorized_keys
256 SHA256:v6WT/8kWeX9+c57VmgxQuErEwTm2t8mvZwLTltUo/14 diego@practica-ssh (ED25519)
```

- La huella (`SHA256:pRyv...qBY`) es la misma que me dio `ssh-keygen` en mi equipo en el paso 5, así que ha llegado mi clave y entera.
- Permisos: `~/.ssh` en `700` y `authorized_keys` en `600`, y los dos del usuario `usuario`. Esto es importante: si `sshd` ve que otros pueden escribir en esa carpeta o en ese archivo, ignora la clave (`StrictModes yes`, que viene por defecto). Lo provoco en el apartado de errores.

### Si no hay ssh-copy-id (por ejemplo en Windows)

Se puede hacer lo mismo a mano en una sola línea, que es lo que hace `ssh-copy-id`:

```bash
cat ~/.ssh/id_ed25519_dpl.pub | ssh -p 2222 usuario@127.0.0.1 \
  "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```

Es importante usar `>>` (añadir) y no `>` (sobrescribir), o se borrarían las claves que ya hubiera.

Evidencia completa: [evidencias/06-copiar-clave.txt](evidencias/06-copiar-clave.txt)

---

## Paso 7: Comprobar el acceso con clave

Me conecto indicando la clave de la práctica con `-i`:

```text
diego@diego:~$ ssh -i ~/.ssh/id_ed25519_dpl -p 2222 usuario@127.0.0.1
Enter passphrase for key '/home/diego/.ssh/id_ed25519_dpl':
Linux servidor-ssh 7.0.0-38-generic #38~24.04.4-Ubuntu SMP PREEMPT_DYNAMIC Mon Sep 14 16:37:11 UTC 2 x86_64
...
Last login: Mon Oct 26 19:23:23 2026 from 172.17.0.1
usuario@servidor-ssh:~$ whoami; hostname
usuario
servidor-ssh
usuario@servidor-ssh:~$ exit
```

Ahora **ya no me pide la contraseña del usuario del servidor**, sino la passphrase de mi clave. Es la diferencia que hay que saber distinguir:
- `usuario@127.0.0.1's password:` es la contraseña del usuario en el servidor y viaja al servidor (cifrada).
- `Enter passphrase for key '...'` es la passphrase de mi clave privada. Se queda en mi equipo y solo sirve para descifrar la clave.

Para estar seguro de que ha entrado con la clave y no con otra cosa, lo miro con `-v` (modo detallado):

```text
diego@diego:~$ ssh -v -i ~/.ssh/id_ed25519_dpl -p 2222 usuario@127.0.0.1 exit 2>&1 | grep -E 'Will attempt|Offering|Server accepts|Authenticated|Authentications that can continue'
debug1: Authentications that can continue: publickey,password
debug1: Will attempt key: /home/diego/.ssh/id_ed25519_dpl ED25519 SHA256:v6WT/8kWeX9+c57VmgxQuErEwTm2t8mvZwLTltUo/14 explicit
debug1: Offering public key: /home/diego/.ssh/id_ed25519_dpl ED25519 SHA256:v6WT/8kWeX9+c57VmgxQuErEwTm2t8mvZwLTltUo/14 explicit
debug1: Server accepts key: /home/diego/.ssh/id_ed25519_dpl ED25519 SHA256:v6WT/8kWeX9+c57VmgxQuErEwTm2t8mvZwLTltUo/14 explicit
Authenticated to 127.0.0.1 ([127.0.0.1]:2222) using "publickey".
```

- `Authentications that can continue: publickey,password`: de momento el servidor acepta las dos formas. En el paso 8 quitaré `password`.
- `Offering` / `Server accepts`: mi cliente ofrece la clave y el servidor la reconoce porque está en `authorized_keys`.
- `using "publickey"`: ha entrado con clave.

En el servidor queda registrado igual, con la huella de mi clave:

```text
Accepted publickey for usuario from 172.17.0.1 port 60028 ssh2: ED25519 SHA256:v6WT/8kWeX9+c57VmgxQuErEwTm2t8mvZwLTltUo/14
```

### No escribir la passphrase cada vez: ssh-agent

Escribir la passphrase en cada conexión es pesado. El agente SSH guarda la clave desbloqueada en memoria durante la sesión. En Linux Mint ya hay uno en marcha, así que solo añado la clave. Con `-t 2h` hago que la olvide a las 2 horas:

```text
diego@diego:~$ ssh-add -t 2h ~/.ssh/id_ed25519_dpl
Enter passphrase for /home/diego/.ssh/id_ed25519_dpl:
Identity added: /home/diego/.ssh/id_ed25519_dpl (diego@practica-ssh)
Lifetime set to 7200 seconds

diego@diego:~$ ssh-add -l
256 SHA256:v6WT/8kWeX9+c57VmgxQuErEwTm2t8mvZwLTltUo/14 diego@practica-ssh (ED25519)
```

### No escribir el puerto, el usuario y la clave cada vez: ~/.ssh/config

Creo un alias en `~/.ssh/config` (no existía) con todos los datos de la conexión:

```text
Host servidor-ssh
    HostName 127.0.0.1
    Port 2222
    User usuario
    IdentityFile ~/.ssh/id_ed25519_dpl
    IdentitiesOnly yes
```

- `IdentitiesOnly yes` hace que solo pruebe la clave de `IdentityFile`. Sin esto, el cliente iría probando todas las claves que tenga, también la de GitHub. Con muchas claves, el servidor puede cortar con `Too many authentication failures` antes de llegar a la buena.
- Le pongo permisos `600` (`chmod 600 ~/.ssh/config`), porque el cliente se niega a usarlo si otros pueden escribir en él.

Ahora basta con el nombre, y gracias al agente no me pide nada:

```text
diego@diego:~$ ssh servidor-ssh 'whoami; hostname; uptime'
usuario
servidor-ssh
 19:42:27 up  1:56,  0 users,  load average: 0.00, 0.04, 0.07
```

Evidencia completa: [evidencias/07-acceso-con-clave.txt](evidencias/07-acceso-con-clave.txt)

---

## Paso 8: Deshabilitar la autenticación por contraseña

Ahora que la clave funciona, quito la contraseña. Lo hago entrando por SSH con mi usuario y usando `sudo`, que es como se administra un servidor de verdad. **Antes de tocar nada me aseguro de tener dos accesos abiertos:** la consola del contenedor (`docker exec -it servidor-ssh bash`) y una sesión SSH. Si me equivoco en la configuración y el SSH deja de funcionar, puedo arreglarlo desde la consola. En un servidor real, sería no cerrar la sesión SSH que ya tengo abierta.

### Dónde poner la configuración

Hay dos opciones:
- **Editar `/etc/ssh/sshd_config`** y cambiar las líneas a mano. Es lo que dice el PR #34.
- **Crear un archivo nuevo en `/etc/ssh/sshd_config.d/`.** Es lo que hace la guía del profe y lo que elijo yo.

Elijo la segunda porque:
1. No toco el archivo original del paquete. Si una actualización de `openssh-server` trae un `sshd_config` nuevo, no hay conflicto con mis cambios.
2. Todos mis cambios están juntos en un archivo pequeño y se ve enseguida qué he cambiado.
3. Como vi en el paso 2, el `Include` de `sshd_config.d/*.conf` está **al principio** de `sshd_config`, y en la configuración de `sshd` **gana el primer valor que se lee**. Así que lo que ponga aquí manda sobre lo que diga `sshd_config` más abajo. Además, los archivos de la carpeta se leen por orden alfabético. Lo llamo `00-solo-claves.conf` para que sea el primero aunque luego aparezcan otros (en muchas VPS viene un `50-cloud-init.conf` con `PasswordAuthentication yes`).

### Errores al comprobar la sintaxis sin sudo

Antes de cambiar nada quise probar el comando de comprobación de sintaxis, y me dio dos errores seguidos:

```text
usuario@servidor-ssh:~$ ls -l /etc/ssh/sshd_config.d/
total 0
usuario@servidor-ssh:~$ sshd -t
-bash: sshd: command not found
usuario@servidor-ssh:~$ /usr/sbin/sshd -t
sshd: no hostkeys available -- exiting.
```

1. **`sshd: command not found`**: `sshd` está instalado (lo vi en el paso 2), pero en `/usr/sbin`. En Debian, el `PATH` de un usuario normal no incluye `/usr/sbin`, que es donde van los programas de administración. Con `sudo` sí funciona, porque `sudo` usa su propio `PATH` (`secure_path`), que incluye `/usr/sbin`.
2. **`no hostkeys available -- exiting`**: con la ruta completa sí lo encuentra, pero no puede leer las claves privadas de la máquina (`ssh_host_*_key` tienen permisos `600` y son de root). El mensaje despista, porque las claves sí existen; lo que pasa es que no tengo permiso. **Solución:** todo lo relacionado con `sshd` se ejecuta con `sudo`.

### Crear el archivo

```text
usuario@servidor-ssh:~$ sudo tee /etc/ssh/sshd_config.d/00-solo-claves.conf > /dev/null <<'EOF'
> PubkeyAuthentication yes
> PasswordAuthentication no
> KbdInteractiveAuthentication no
> PermitRootLogin no
> EOF
[sudo] password for usuario:
```

Uso `sudo tee` en vez de `sudo echo ... > archivo` porque la redirección `>` la hace mi shell sin permisos de root, y daría `Permission denied`. `tee` sí se ejecuta como root y escribe el archivo.

| Directiva | Qué hace |
|---|---|
| `PubkeyAuthentication yes` | Deja entrar con clave pública. Ya era así por defecto, pero lo dejo escrito para que quede claro |
| `PasswordAuthentication no` | **No deja entrar con contraseña** |
| `KbdInteractiveAuthentication no` | Cierra la autenticación "teclado interactivo", que con PAM es otra forma de pedir la contraseña. En Debian ya venía a `no`, pero lo fijo por si cambia |
| `PermitRootLogin no` | Root no puede entrar por SSH de ninguna forma, ni con clave. Para administrar ya tengo `usuario` con `sudo` |

No pongo `ChallengeResponseAuthentication no`, que sale en algunas guías, porque es el nombre antiguo de `KbdInteractiveAuthentication` y en OpenSSH 10 solo se mantiene por compatibilidad.

**Ojo:** `sudo` me sigue pidiendo la contraseña de `usuario`. Quitar la contraseña en SSH no quita la contraseña del usuario. Solo impide usarla para entrar por SSH. Por eso no hay que borrarla: hace falta para `sudo`.

### Comprobar antes de aplicar

```text
usuario@servidor-ssh:~$ sudo sshd -t && echo 'sintaxis OK'
sintaxis OK
```

`sshd -t` no dice nada si todo está bien. Le añado el `echo` para verlo claro. Si hubiera un error y recargara el servicio, `sshd` podría no volver a arrancar y me quedaría sin acceso. Por eso siempre `sshd -t` antes de recargar.

Con `sshd -T` (en mayúscula) veo la configuración **efectiva**, la que resulta de juntar todos los archivos y los valores por defecto:

```text
usuario@servidor-ssh:~$ sudo sshd -T | grep -E '^(pubkeyauthentication|passwordauthentication|kbdinteractiveauthentication|permitrootlogin|permitemptypasswords|usepam) '
usepam yes
permitrootlogin no
pubkeyauthentication yes
passwordauthentication no
kbdinteractiveauthentication no
permitemptypasswords no
```

Esto es mejor que mirar los archivos uno a uno, porque te dice el valor que gana de verdad.

### Aplicar

```text
usuario@servidor-ssh:~$ sudo service ssh reload
Reloading OpenBSD Secure Shell server's configuration: sshd.
```

Uso `reload` y no `restart`: `reload` hace que `sshd` relea la configuración sin cortar las conexiones abiertas, y la sesión en la que estoy sigue viva. En una máquina real: `sudo systemctl reload ssh`.

Evidencia completa: [evidencias/08-deshabilitar-contrasena.txt](evidencias/08-deshabilitar-contrasena.txt)
