# uv y Zensical

## uv

Gestor de paquetes y entornos de Python escrito en Rust. Hace en una sola herramienta lo que antes hacían `pip`, `pip-tools`, `virtualenv` y `pyenv`, y además puede descargar la versión de Python que pida el proyecto.

### Instalar

Linux / macOS:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Windows (PowerShell):

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Para usarlo sin cerrar la terminal hay que recargar la configuración:

```bash
source ~/.bashrc
uv --version
which uv        # normalmente ~/.local/bin/uv
```

### Comandos

| Comando | Qué hace |
|---|---|
| `uv init` | Crea un proyecto nuevo (`pyproject.toml`, `.python-version`...) |
| `uv add paquete` | Añade una dependencia |
| `uv add --dev paquete` | Añade una dependencia solo de desarrollo |
| `uv remove paquete` | Quita una dependencia |
| `uv sync` | Instala todo lo del `pyproject.toml` / `uv.lock` en `.venv` |
| `uv run comando` | Ejecuta un comando dentro del entorno del proyecto |
| `uv python install 3.14` | Instala una versión de Python |
| `uv python list` | Lista las versiones de Python disponibles |

Lo normal al clonar un proyecto que ya existe es `uv sync` y después `uv run ...`. No hace falta activar el entorno virtual a mano.

## Zensical

Generador de webs estáticas para documentación. Lo hace el mismo equipo de Material for MkDocs. Escribes en Markdown dentro de `docs/` y genera una web HTML/CSS/JS con buscador, modo oscuro, menú, etc.

### Comandos

| Comando | Qué hace |
|---|---|
| `uv run zensical serve` | Servidor local en `http://127.0.0.1:8000` con recarga en vivo |
| `uv run zensical serve -a localhost:8001` | Lo mismo en otro puerto |
| `uv run zensical build` | Genera la web en la carpeta `site/` |
| `uv run zensical build --clean` | Borra `site/` antes de generarla |
| `uv run zensical --help` | Ayuda |

La carpeta `site/` es lo que se despliega en un servidor (NGINX, GitHub Pages...). No se sube al repo.

### Añadir una página

1. Crear `docs/mi-pagina.md`.
2. Opcional: poner un icono arriba del todo:
   ```markdown
   ---
   icon: lucide/server
   ---
   ```
3. Añadirla a `nav` en `zensical.toml`:
   ```toml
   nav = [
     { "Get started" = "index.md" },
     { "Mi página" = "mi-pagina.md" },
   ]
   ```
4. Comprobarla con `uv run zensical serve`.

### Markdown extra que admite

Avisos:

```markdown
!!! note
    Texto de la nota.

!!! warning
    Texto del aviso.
```

Pestañas:

```markdown
=== "Linux"
    comando linux

=== "Windows"
    comando windows
```

También diagramas Mermaid (bloque de código con `mermaid`), listas de tareas, emojis, fórmulas y teclas (`++ctrl+c++`).

### Personalizar el tema (zensical.toml)

```toml
[project]
site_name = "Nombre de la web"
repo_url = "https://github.com/monium/gitanddocs"
repo_name = "monium/gitanddocs"
copyright = "Copyright &copy; 2026 Nombre"

[project.theme]
language = "es"
logo = "images/logo.png"       # dentro de docs/
favicon = "images/favicon.png"
features = ["navigation.footer", "header.autohide", "content.code.copy"]

[project.theme.font]
text = "Inter"
code = "Jetbrains Mono"
```

- Colores: `[project.theme.palette]` con `scheme` (`default` es claro, `slate` es oscuro), `primary` y `accent`.
- Botón claro/oscuro: varios bloques `[[project.theme.palette]]` con `media` y `toggle`.
- `font = false` usa las fuentes del sistema y no carga Google Fonts.
- `[[project.extra.social]]` añade iconos con enlaces en el pie de página.
- `[project.extra] generator = false` quita el "Hecho con Zensical".

## Despliegue automático (GitHub Actions + Pages)

El archivo `.github/workflows/docs.yml` hace esto con cada push a `main`:

```yaml
- uses: actions/checkout       # descarga el repo
- uses: actions/setup-python   # instala Python
- run: pip install zensical
- run: zensical build --clean  # genera site/
- uses: actions/upload-pages-artifact   # sube site/
- uses: actions/deploy-pages            # lo publica
```

Necesita los permisos `pages: write` e `id-token: write`, y que en Settings > Pages del repo la fuente sea "GitHub Actions".
