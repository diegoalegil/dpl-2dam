# Tareas pendientes

Situación a 06/10/2026.

## Mi tarea ahora: issue #10 "Aprender a crear una Issue"

Criterio de aceptación: cada alumno tiene que haber creado al menos una issue o haber participado en alguna.

Pasos:
1. Crear una issue con la plantilla que toque.
2. Ponerle label y añadirla al Project DPL.
3. Si se puede, resolverla yo con una rama y un PR que lleve `Closes #N`, para practicar el ciclo entero.

## Issues abiertas del repo

| # | Tarea | Situación |
|---|---|---|
| 4 | Desplegar site en un contenedor con NGINX | En progreso. El PR #7 está abierto con cambios pedidos |
| 10 | Aprender a crear una Issue | Asignada, la tenemos que hacer todos |
| 16 | Instalación, configuración y uso de Gitea | Sin asignar. Es la madre de #17 y #19 |
| 17 | Clonar y enviar cambios con los puertos cambiados | Sin asignar |
| 19 | Documentación de la instalación de Gitea | Sin asignar. Debe cubrir la clase doble del 02/10 |

Lo que pide la #19:
- Un `.md` en `docs/` con la instalación de Gitea paso a paso.
- Sin faltas de ortografía, concisa y completa.
- Añadida al `nav` de `zensical.toml`.
- Explicar a fondo Docker y Docker Compose.
- Referencia: https://docs.gitea.com/installation/install-with-docker/

Lo que pide la #17:
- Diferencia entre crear un repo vacío y uno inicializado, y qué implica cada uno.
- Instalación y configuración teniendo en cuenta que hemos cambiado los puertos por defecto (el `git clone` cambia un poco).

## Fallos encontrados en el repo (ideas para issues)

Los he comprobado y son reales:

1. **`.github/ISSUE_TEMPLATE/config.yml` está roto.** Dentro del archivo se coló el comando de terminal con el que se creó: empieza por `cat > .github/ISSUE_TEMPLATE/config.yml << 'EOF'` y acaba con `EOF`. No es YAML válido, así que GitHub no lo aplica (ni `blank_issues_enabled: false` ni el enlace de "Pregunta general"). Arreglo: dejar solo el contenido del medio. Plantilla: Reporte de Bug.

2. **Labels que no existen.** Las plantillas "Tarea General" y "Vulnerabilidad de Seguridad" ponen las labels `task` y `security`, pero en el repo no están creadas, así que no se aplican. Arreglo: crear esas labels o cambiar las plantillas. Plantilla: Reporte de Bug.

3. **Se perdió la explicación de uv sin reiniciar la terminal.** El PR #6 (issue #3) añadió al README cómo usar `source ~/.bashrc`, pero en el merge `9c5819c` ("Merge branch 'main' into rama-atteneri") se perdió al resolver el conflicto. Ahora el README dice que no hace falta reiniciar la terminal, pero no explica cómo. Arreglo: recuperar ese bloque. Plantilla: Reporte de Bug o Tarea General.

4. **Faltas de ortografía en `docs/trabajando-con-git.md`**: "alamcenar", "respositorio(s)", "trabajaar", "persoans", "lcoal". También hay restos sueltos ("En Github", "En Bash"), en el paso 5 pone `tu-rama` cuando el comando usa `nombre-rama`, y en el paso 7 sale "jorgeM". Plantilla: Tarea General (documentación).

5. **Configuración de la web sin personalizar.** En `zensical.toml` siguen `site_name = "Documentation"`, `site_url = "https://www.example.com/"` y `language = "en"`, cuando la documentación está en español y la web real es https://monium.github.io/gitanddocs/. `index.md` y `markdown.md` son las páginas de ejemplo de Zensical en inglés. Plantilla: Solicitud de Funcionalidad o Tarea General.

6. **`docs/tema-visual.md` no tiene icono** en la cabecera, cuando las demás páginas sí (`icon: lucide/...`). Es una tontería, pero sirve como primera issue fácil.

Antes de crear una, mirar que no la haya abierto ya otro compañero.
