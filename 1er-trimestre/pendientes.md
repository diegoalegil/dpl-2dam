# Tareas pendientes

Situación a 26/10/2026. Lo que ha pasado desde el 06/10 está en [novedades.md](novedades.md).

## Lo mío

- **#33 "Arreglar los warnings de anchor"**: me la asignaron junto a @Jorghdez18 y @Atthemyg. Ya está cerrada: la resolvió @Atthemyg con el PR #38 (merge el 21/10).
- **Todavía no he creado ninguna issue.** La #10 ("Aprender a crear una Issue") se cerró el 26/10, pero el criterio era que cada alumno creara al menos una. Me conviene crear una cuanto antes (ideas abajo).
- Mi equipo en la organización es **limos** (17 personas). El otro grupo que trabaja en gitanddocs es **bolero**.

## Issues abiertas en gitanddocs

| # | Tarea | Asignada a | Situación |
|---|---|---|---|
| 4 | Desplegar site en un contenedor con NGINX | @albertocarher | El PR #7 se cerró sin merge |
| 16 | Configuración y uso de Gitea (madre) | @somilvd | Pendiente de sus hijas |
| 17 | Clonar y enviar cambios con los puertos cambiados | @IvnMD | Sin PR |
| 19 | Documentación de la instalación de Gitea | @jmesmarrero | Hecha con el PR #29, pero la issue sigue abierta (el PR no puso bien `Closes #19`) |
| 27 | Configuración e instalación de NGINX | @jmesmarrero | El PR #39 se hizo al revés y la guía no está en `main` (ver novedades) |
| 30 | Refactorizar la documentación para tener un apartado de Docker y Compose | @jreyper | Sin PR |
| 32 | Conectar a una máquina remota por SSH | @modiael, @Jose-Glez-Hdez | El profe trabaja en la rama `issue-32` y hay un PR duplicado (#34) |
| 35 | Añadir hosts (`/etc/hosts` para ver la documentación desde otra máquina) | @juanpsuaa | Sin PR |

## PR abiertos

| # | Qué | Situación |
|---|---|---|
| 34 | Proteger las conexiones SSH con clave (`docs/seguridad-servidor/`) | Duplica lo que hace el profe en `issue-32`. Hay que fusionar ambos |
| 40 | Guía para crear una issue (`docs/creando-isue.md`) | Aprobado por @IvnMD, falta el merge |

## Fallos que siguen sin arreglar (ideas para mi issue)

Comprobados de nuevo el 26/10:

1. **`.github/ISSUE_TEMPLATE/config.yml` sigue roto.** Empieza por `cat > .github/ISSUE_TEMPLATE/config.yml << 'EOF'` y acaba con `EOF`, así que no es YAML válido y GitHub no lo aplica. Plantilla: Reporte de Bug.
2. **Faltan las labels `task` y `security`** que usan las plantillas "Tarea General" y "Vulnerabilidad de Seguridad". Plantilla: Reporte de Bug.
3. **`ejemplo.md` en la raíz del repo** con texto basura (`iiqerigfberiugz...`). Lo metió el profe con el PR #26 ("ya termine"), que parece una demo de cómo cerrar una issue con un PR (cerró la #25). Se puede proponer borrarlo. Plantilla: Tarea General. Es la más fácil de resolver con un PR.
4. **Los textos del menú lateral siguen en inglés** ("Get started", "Markdown in 5min", "Using Git & Github"...). Las issues #24 y #25 pedían unificarlos, pero se cerraron con el PR de demo, que no los cambió.
5. **La guía de NGINX no está en `main`.** El PR #39 tenía la base y la rama cambiadas (`jorgeMRama ← main`), así que se mezcló `main` dentro de la rama de Jorge y no al revés. `docs/nginx/install-nginx.md` solo existe en `jorgeMRama`. Antes de abrir nada, mejor comentarlo con @jmesmarrero.
6. **Sigue perdida la explicación de `source ~/.bashrc`** para usar uv sin reiniciar la terminal (ahora la guía está en `docs/index.md`). Plantilla: Reporte de Bug.
7. **Faltas en `docs/trabajando-con-git.md`**: "alamcenar", "trabajaar", "persoans", "lcoal"... Plantilla: Tarea General.
8. **`zensical.toml` sin personalizar**: `site_name = "Documentation"`, `site_url` de ejemplo y `language = "en"`. Plantilla: Tarea General.

Ya arreglado: `docs/tema-visual.md` ya tiene icono.

Antes de crear una, mirar que nadie la haya abierto ya.
