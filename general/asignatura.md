# La asignatura

DPL de 2º DAM, curso 2026-2027. La asignatura va de desplegar aplicaciones: coger un proyecto, generarlo y ponerlo a funcionar en un servidor. Para practicarlo trabajamos como si fuéramos un equipo de una empresa.

## Cómo se trabaja

- Todo pasa por GitHub, en la organización **monium**. Somos unas 17 personas.
- El profesor es **@modiael**. Es quien crea las tareas como issues y quien da el visto bueno a los PR.
- El proyecto de clase es el repo **monium/gitanddocs**: una web de documentación hecha con Markdown, uv y Zensical. Cada tema que damos acaba como una página de esa documentación.
- Las tareas se organizan en un tablero Kanban (GitHub Projects) llamado **DPL**.
- Los compañeros también revisan los PR de los demás. Por ejemplo, en el PR #7 un compañero pidió cambios antes de aprobarlo.

Ciclo de cada tarea:

```text
Issue -> rama -> commits -> push -> Pull Request (Closes #N) -> revisión -> merge -> la web se publica sola
```

## Normas que ha dado el profesor

- La documentación va en la carpeta `docs/`, no en el `README.md`. Zensical solo usa `docs/` para generar la web.
- Hay que organizar los ficheros y carpetas de `docs/` como veamos mejor y añadirlos a la navegación (`nav`) de `zensical.toml`.
- Si un PR tiene conflictos, quien lo hizo tiene que resolverlos (y refactorizar si hace falta) antes de que se apruebe.
- Para tareas grandes se usan **sub-issues**. La issue "madre" se da por resuelta cuando están resueltas todas sus hijas.

## Herramientas

| Herramienta | Para qué |
|---|---|
| Git | Control de versiones en local |
| GitHub | Repos, issues, PR, revisiones |
| GitHub Projects | Tablero Kanban de tareas |
| GitHub Actions | Automatizar el despliegue |
| GitHub Pages | Hosting de la web generada |
| uv | Gestor de paquetes y entornos de Python |
| Zensical | Generador de webs estáticas a partir de Markdown |
| Markdown | Formato en el que se escribe toda la documentación |
| Docker / Docker Compose | Contenedores (NGINX, Gitea) |
| NGINX | Servidor web para servir la web generada |
| Gitea | Servidor Git propio, como un GitHub pero instalado por nosotros |

## Temas vistos hasta ahora

Del 25/09/2026 al 06/10/2026:

1. Instalar uv y crear un proyecto con `uv init`.
2. Añadir Zensical, levantar el servidor local y ver la recarga en vivo.
3. Escribir documentación en Markdown.
4. Generar el site (`zensical build`) para poder desplegarlo.
5. Trabajar con Git y GitHub en equipo: fork, upstream, ramas, commits y PR.
6. Plantillas automáticas de issues y de PR.
7. Personalizar el tema visual de Zensical.
8. Despliegue automático en GitHub Pages con GitHub Actions.
9. Gestión de tareas con issues, labels, sub-issues y el tablero Kanban.

## Lo que viene

Según las issues abiertas:

- Desplegar el site en un contenedor con NGINX (#4).
- Instalar, configurar y usar Gitea con Docker para un entorno de empresa (#16). La clase doble del viernes 02/10/2026 fue sobre esto.
- Clonar y enviar cambios a Gitea cuando hemos cambiado los puertos por defecto (#17).
