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
