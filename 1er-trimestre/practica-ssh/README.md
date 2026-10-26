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
