# Novedades en GitHub

## Del 06/10 al 26/10/2026

### Cambios que han entrado en `main` de gitanddocs

| Fecha | PR | Qué cambió |
|---|---|---|
| 06/10 | #23 (cierra #20) | El profe quitó `src/2dam_dpl/` y el `[build-system]` del `pyproject.toml`. Con Zensical todo va en `docs/` y no hace falta la estructura de paquete que crea `uv init` |
| 08/10 | #26 (cierra #25) | Demo del profe de cómo un PR cierra una issue. Solo añade `ejemplo.md` |
| 13/10 | #31 (cierra #28) | La guía de uv + Zensical del README pasa a `docs/index.md` |
| 14/10 | #29 (para #19) | Guía "Instalar Gitea con Docker" en `docs/gitea/Install-Gitea-with-docker.md` y nueva sección "Gitea" en el menú |
| 21/10 | #38 (cierra #33) | Arreglados los avisos "anchor does not exist" de `docs/index.md` |

Después de `git pull` hice `uv sync` y `zensical build`: todo bien y sin avisos ("No issues found").

### Contenido nuevo para estudiar

**Gitea con Docker** (`docs/gitea/Install-Gitea-with-docker.md`):
- Qué es Gitea y qué es Docker: imagen, contenedor, volumen, puerto.
- Instalar Docker y Docker Compose, y por qué hace falta `sudo`.
- Elegir base de datos: SQLite3 o PostgreSQL.
- Carpeta del proyecto, permisos y `docker-compose.yml` para cada opción.
- Arrancar con `docker compose up -d` y el asistente web de instalación.
- Comprobar que funciona: contenedores y logs.

**NGINX** (`docs/nginx/install-nginx.md`, de momento solo en la rama `jorgeMRama`):
- Instalar NGINX y servir dos webs: una hecha con Zensical (`trabajando.local`) y un blog hecho con Jekyll.
- Un archivo de configuración por sitio, activarlo y recargar NGINX.
- Poner los nombres en `/etc/hosts` para entrar por nombre.
- Gestionar el servicio y actualizar el contenido de una web.

**SSH a una máquina remota** (issue #32 y PR #34):
- Conectarse a un servidor con clave SSH.
- Desactivar el login con contraseña en `sshd_config`.

### Issues nuevas

| # | Qué | Estado |
|---|---|---|
| 20 | La plantilla con `src/2dam_dpl` no es adecuada | Cerrada |
| 21 | Las issues no aparecían en el tablero | Cerrada (era solo retraso) |
| 22 | Mover el README a `docs/` | Cerrada |
| 24 y 25 | Unificar los textos del menú lateral (duplicada) | Cerradas |
| 27 | Configuración e instalación de NGINX | Abierta |
| 28 | Mover la documentación de uv y Zensical a `docs/` | Cerrada |
| 30 | Apartado propio para Docker y Compose | Abierta |
| 32 | Conectar a una máquina remota por SSH | Abierta |
| 33 | Arreglar los warnings de anchor (asignada a mí y a dos más) | Cerrada |
| 35 | Añadir hosts | Abierta |

La #30 la creó el profe a partir de un comentario en la revisión del PR #29. Desde un comentario se puede crear una issue directamente ("Reference in new issue").

### PR que no salieron bien (para aprender)

- **#39**: se abrió con la base y la rama al revés (`base: jorgeMRama ← compare: main`). Se aprobó y se hizo merge, pero lo que pasó fue que `main` entró en la rama de Jorge, y la guía de NGINX nunca llegó a `main`. Antes de crear un PR hay que mirar siempre que sea **base: main ← compare: mi-rama**.
- **#29**: la plantilla tenía `- Closes #` y el número en la línea de abajo, así que la #19 no se cerró sola. Tiene que ir junto: `Closes #19`.
- **#34**: un compañero hizo la documentación de SSH mientras el profe ya trabajaba en ella en la rama `issue-32`, y ahora está duplicada. Antes de empezar, mirar si alguien ya tiene una rama o un PR de esa tarea.
- **#36 y #37**: un blog con Jekyll que se cerró sin merge. Subía también la carpeta generada `_site/`, y lo generado no se sube al repo.

### Normas nuevas del profe

- Después de hacer merge de un PR, **borrar la rama** para que no se queden ramas sueltas.
- Los compañeros revisan y aprueban los PR ("LGTM" significa "looks good to me").
- Si un documento es muy largo, se divide en varios. En la revisión del #29 se propuso partir la guía de Gitea en tres.

### Organización

Ahora hay tres equipos en monium:

| Equipo | Repo | Quién |
|---|---|---|
| **limos** | gitanddocs | Mi grupo (17, con el profe) |
| bolero | gitanddocs | El otro grupo de DPL (19, con el profe) |
| mojojojo | bae-docs | Otro grupo, con documentación de SQLite. No es de DPL |

### Repo nuevo: monium/task-api (21/10)

API de tareas del profe. Seguramente es lo próximo que vamos a desplegar.

- **App**: FastAPI + SQLAlchemy + SQLite. Hace un CRUD de tareas (`/tasks`) y tiene `/health` y `/up` para comprobar que está viva.
- **Dockerfile**: parte de `python:3.14-slim`. Instala primero las dependencias para aprovechar la caché de capas, copia solo `app/` y arranca con un usuario sin privilegios.
- **justfile**: atajos con `just`: `run`, `test`, `docker-build`, `docker-run`, `config`...
- **Kamal**: herramienta para desplegar contenedores en servidores por SSH.
  - `config/deploy.yml` es la configuración común: imagen en `ghcr.io`, usuario `ubuntu`, puerto 8000.
  - Hay dos entornos: `staging` (servidor "pirita") y `production` (servidor "galena").
- **scripts/deploy.sh**: exporta `requirements.txt` desde `uv.lock` y ejecuta `kamal setup|deploy -d staging|production`.

Detalles que me he fijado:
- `config/deploy.production.yml` tiene `APP_ENV: staging`, seguramente copiado del de staging.
- `tasks.db` está subido al repo.
