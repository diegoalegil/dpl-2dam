# Git, GitHub, issues y PR

## Conceptos

- **Git**: control de versiones. Guarda el historial de cambios del proyecto en tu ordenador.
- **GitHub**: donde se suben los repos para trabajar con más gente.
- **Fork**: copia de un repo ajeno en tu cuenta. Trabajas en tu copia sin tocar el original.
- **origin**: el remoto de donde clonaste (tu repo o tu fork).
- **upstream**: el remoto del repo original (el del profesor), cuando trabajas con fork.
- **Rama**: línea de trabajo independiente. Nunca se trabaja directamente en `main`.
- **Commit**: una "foto" de los cambios, guardada solo en local.
- **Push**: subir los commits a GitHub.
- **Pull Request (PR)**: pedir que los cambios de tu rama se unan a `main` del repo original.
- **Merge**: unir una rama con otra.

## Dos formas de trabajar en gitanddocs

**A) Con fork** (la que explica `docs/trabajando-con-git.md`):

```bash
# 1. Fork desde la web de GitHub (botón Fork)
# 2. Clonar tu fork
git clone https://github.com/diegoalegil/gitanddocs.git
cd gitanddocs

# 3. Añadir el repo del profesor como upstream
git remote add upstream https://github.com/monium/gitanddocs.git
git remote -v

# 4. Traer los cambios del profesor a tu main
git switch main
git fetch upstream
git merge upstream/main

# 5. Crear tu rama de trabajo y subirla
git switch -c diego/nombre-tarea
git push -u origin diego/nombre-tarea
```

**B) Sin fork, con rama en el repo de la organización.** Como soy miembro de monium tengo permiso de escritura (push y triage) en gitanddocs, así que también puedo hacerlo así:

```bash
git clone https://github.com/monium/gitanddocs.git
cd gitanddocs
git switch -c diego/nombre-tarea
git push -u origin diego/nombre-tarea
```

Antes de elegir una, mejor preguntar al profesor cuál prefiere.

## Día a día

```bash
git status                    # qué ha cambiado
git add archivo.md            # preparar un archivo (git add . para todos)
git commit -m "Mensaje claro"  # guardar en local
git push                      # subir a GitHub
git log --oneline --graph     # ver el historial
git branch                    # ver en qué rama estoy
git switch otra-rama          # cambiar de rama
git pull                      # traer cambios del remoto y unirlos
```

Recordatorios:
- `fetch` solo descarga los cambios. `merge` los une a tu rama. `pull` hace las dos cosas.
- Antes de hacer `merge upstream/main` hay que estar en `main`.
- Un `commit` no sube nada. Hasta que no haces `push`, solo está en tu ordenador.

## Conflictos

Pasan cuando dos personas tocan las mismas líneas. Git marca el archivo así:

```text
<<<<<<< HEAD
lo que tienes tú
=======
lo que viene de la otra rama
>>>>>>> main
```

Para resolverlo: dejas el texto correcto, borras las marcas y luego haces `git add` + `git commit` + `git push`. Ojo al resolverlos, que es fácil borrar trabajo de otro. En este repo ya pasó: en un merge se perdió la explicación de `source ~/.bashrc` que había añadido el PR #6.

## Issues

Una issue es una ficha de trabajo: un fallo, una tarea, una mejora o una duda.

Partes de una issue:
- **Título**: corto y que se entienda sin abrirla.
- **Descripción**: en Markdown, siguiendo la plantilla.
- **Labels**: `bug`, `documentation`, `enhancement`, `question`, `duplicate`, `good first issue`, `help wanted`, `invalid`, `wontfix`.
- **Assignees**: quién se encarga.
- **Sub-issues**: tareas hijas. Por ejemplo, #16 tiene como hijas a #17 y #19.
- **Project**: añadirla al tablero DPL para que salga en el Kanban.

Crear una desde la web:
1. Pestaña **Issues** → **New issue**.
2. Elegir plantilla.
3. Rellenar el título y las secciones (las listas `- [ ]` se marcan con `- [x]`).
4. A la derecha: labels, assignees y project.
5. **Create**.

Desde terminal con `gh`:

```bash
gh issue list -R monium/gitanddocs
gh issue view 10 -R monium/gitanddocs
gh issue create -R monium/gitanddocs --title "Título" --body "Descripción" --label bug
gh issue comment 10 -R monium/gitanddocs --body "Comentario"
```

Para referenciar issues en cualquier texto de GitHub basta con escribir `#10`.

## Pull Requests

1. Haz `push` de tu rama.
2. En GitHub sale el botón **Compare & pull request**.
3. Revisa que sea **base: monium/gitanddocs main ← compare: tu rama**.
4. Rellena la plantilla y pon `Closes #N` para que la issue se cierre sola al hacer merge.
5. Pide revisión y atiende los comentarios. Si piden cambios, haces más commits en la misma rama y el PR se actualiza solo.

Palabras clave que cierran issues: `Closes #N`, `Fixes #N`, `Resolves #N`.

Con `gh`:

```bash
gh pr create -R monium/gitanddocs --base main --title "Título" --body "Closes #N"
gh pr list -R monium/gitanddocs
gh pr checkout 7 -R monium/gitanddocs   # probar en local el PR de otro
```

## Buenas prácticas

- Una rama por tarea, con un nombre claro: `docs/gitea-instalacion`, `fix/config-plantillas`...
- Commits pequeños con mensajes que digan qué hacen.
- Actualizar `main` antes de crear la rama, para tener menos conflictos.
- No subir credenciales, `.venv/` ni `site/` (ya están en el `.gitignore`).
