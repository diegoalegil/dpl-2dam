# Repo de clase: monium/gitanddocs

- URL: https://github.com/monium/gitanddocs (público)
- Web publicada: https://monium.github.io/gitanddocs/
- Rama principal: `main`
- Lo creó el profesor el 25/09/2026 y desde entonces cada alumno va añadiendo cosas mediante PR.

## Estructura

```text
gitanddocs/
├── .github/
│   ├── ISSUE_TEMPLATE/         plantillas de issues
│   │   ├── bug_report.md
│   │   ├── feature_request.md
│   │   ├── question.md
│   │   ├── security.md
│   │   ├── tarea_general.md
│   │   └── config.yml
│   ├── pull_request_template.md
│   └── workflows/
│       └── docs.yml            despliegue automático a GitHub Pages
├── docs/                       las páginas de la web (Markdown)
│   ├── index.md
│   ├── markdown.md
│   ├── get-site.md
│   ├── trabajando-con-git.md
│   └── tema-visual.md
├── src/2dam_dpl/__init__.py    paquete Python vacío que crea uv init
├── .gitignore
├── .python-version             3.14
├── pyproject.toml              proyecto y dependencias (uv)
├── uv.lock                     versiones exactas de las dependencias
├── zensical.toml               configuración de la web
└── README.md                   guía de uv + Zensical
```

## Qué hace cada archivo importante

**pyproject.toml**: define el proyecto `2dam-dpl`. Pide Python 3.14 o superior y tiene a Zensical como dependencia de desarrollo (`[dependency-groups] dev = ["zensical>=0.0.65"]`). Con `uv sync` se instala todo.

**uv.lock**: guarda las versiones exactas de todo lo instalado, para que a todos nos funcione igual. Se sube al repo y no se toca a mano.

**zensical.toml**: configuración de la web. Lo más importante:
- `nav`: el menú lateral. Si creas una página nueva en `docs/` hay que añadirla aquí.
- `[project.theme]`: idioma, funcionalidades, paleta de colores (claro, oscuro o según el sistema).
- `[project.markdown_extensions]`: extensiones de Markdown activadas (avisos, pestañas, Mermaid, emojis, fórmulas...).

Menú actual:

| Título | Archivo |
|---|---|
| Get started | `index.md` |
| Markdown in 5min | `markdown.md` |
| Obtener site | `get-site.md` |
| Using Git & Github | `trabajando-con-git.md` |
| Tema Visual | `tema-visual.md` |

**.github/workflows/docs.yml**: GitHub Action que se ejecuta con cada push a `main`. Hace esto:
1. Descarga el repo.
2. Instala Python y Zensical con pip.
3. Ejecuta `zensical build --clean`, que genera la web en `site/`.
4. Sube `site/` y la publica en GitHub Pages.

Por eso, en cuanto se acepta un PR, la web se actualiza sola.

## Páginas de la documentación

- **index.md** y **markdown.md**: las páginas de ejemplo que trae Zensical, en inglés. Enseñan los avisos (admonitions), el código y la sintaxis de Markdown.
- **get-site.md**: cómo convertir los `.md` en una web HTML/CSS/JS. Se edita el Markdown, `uv run zensical build` lo genera en `site/` y `uv run zensical serve` sirve la vista previa en `http://localhost:8000` (con `-a localhost:8001` se cambia el puerto).
- **trabajando-con-git.md**: guía de fork, clone, upstream, fetch/merge, ramas, commits y PR. Está resumida en [02-git-github.md](02-git-github.md).
- **tema-visual.md**: cómo personalizar la web desde `zensical.toml`: colores, botón claro/oscuro, tipografías, idioma, logo y favicon, cabecera, pie de página y enlace al repo. Está resumida en [03-uv-zensical.md](03-uv-zensical.md).

## README

Es la guía principal de uv + Zensical:
1. Instalar uv.
2. Crear el proyecto con `uv init`.
3. `uv add --dev zensical`.
4. `uv run zensical serve`.
5. Live reload: guardas un `.md` y el navegador se actualiza solo.

Además trae una tabla de comandos, la estructura del proyecto y la solución de problemas típicos: uv no encontrado, puerto ocupado y que no detecte cambios.

## Plantillas

Al pulsar **New issue** sale un selector con estas plantillas:

| Plantilla | Label que pone | Para qué |
|---|---|---|
| Reporte de Bug | `bug` | Algo no funciona |
| Solicitud de Funcionalidad | `enhancement` | Proponer algo nuevo o una mejora |
| Pregunta / Duda | `question` | Dudas técnicas o de proceso |
| Vulnerabilidad de Seguridad | `security` | Problemas de seguridad |
| Tarea General | `task` | Docs, refactor, tests, config... |

La plantilla de PR pide: descripción, issue relacionada con `Closes #N`, tipo de cambio, cómo se ha probado y una checklist (no subir credenciales, enlazar la issue, etc.).

## Historial de issues y PR (hasta el 06/10/2026)

Issues:

| # | Título | Estado |
|---|---|---|
| 2 | Explicar en el README cómo obtener el site | Cerrada |
| 3 | Explicar cómo usar uv sin recargar el terminal | Cerrada |
| 4 | Desplegar site en un contenedor con NGINX | Abierta, en progreso |
| 10 | Aprender a crear una Issue | Abierta |
| 13 | Documentar personalización del tema visual | Cerrada |
| 15 | Crear guía de instalación de Gitea | Cerrada (duplicada) |
| 16 | Instalación, configuración y uso de Gitea | Abierta (madre) |
| 17 | Clonar y enviar cambios con los puertos cambiados | Abierta (hija de #16) |
| 18 | prueba | Cerrada |
| 19 | Crear documentación para la instalación de Gitea | Abierta (hija de #16) |

Pull requests:

| # | Título | Estado |
|---|---|---|
| 1 | Readme con la documentación de uv y Zensical | Merge |
| 5 | Actualización README.md | Merge |
| 6 | Cómo usar uv sin recargar el terminal | Merge |
| 7 | Desplegar site en un contenedor con NGINX | Abierto, con cambios pedidos |
| 8 | Contexto sobre qué son ambas herramientas | Cerrado sin merge |
| 9 | Guía para obtener el site con Zensical | Merge |
| 11 | Plantillas para issues y PR automáticas | Merge |
| 12 | Cómo trabajar con git | Merge |
| 14 | Guía de personalización del tema visual | Merge |

Del PR #7 se aprende bastante. El profesor pidió llevar el contenido a `docs/` en vez de meterlo en el README, organizar la navegación y resolver conflictos. Un compañero pidió quitar la parte de WordPress.

## Tablero Kanban (Project "DPL")

Está en https://github.com/orgs/monium/projects/2 y es privado de la organización.

Columnas:

| Columna | Significado |
|---|---|
| Sin asignar | Tareas sin empezar ni asignar (límite de 5) |
| Asignadas | Alguien la tiene, pero no ha empezado |
| En progreso | Se está trabajando (límite de 3) |
| En revisión | PR abierto esperando revisión (límite de 5) |
| Terminado | Hecho y con merge |

- Vistas: Backlog (el tablero), Priority board, Team items, Roadmap y My items.
- Cada tarjeta tiene un campo **Estimate** para estimar el esfuerzo.
- Hay **7 workflows** de automatización: las tarjetas se mueven solas, por ejemplo a Terminado cuando se cierra la issue o se hace merge del PR. Por eso la plantilla de PR insiste en poner `Closes #N`.
