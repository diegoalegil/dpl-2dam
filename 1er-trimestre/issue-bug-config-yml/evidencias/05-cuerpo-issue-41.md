## Descripción del Bug
El archivo `.github/ISSUE_TEMPLATE/config.yml` tiene dentro el comando de la terminal con el que se creó: la primera línea es `cat > .github/ISSUE_TEMPLATE/config.yml << 'EOF'` y la última es `EOF`. Esas dos líneas no son YAML, así que el archivo no es válido y GitHub no aplica la configuración. El archivo llegó con el PR #11.

## Pasos para Reproducir
1. Abrir [`.github/ISSUE_TEMPLATE/config.yml`](https://github.com/monium/gitanddocs/blob/main/.github/ISSUE_TEMPLATE/config.yml) y mirar las líneas 1 y 7.
2. En la pestaña Issues, pulsar **New issue**: sale "Blank issue" sin ninguna marca y no sale el enlace "Pregunta general".
3. En local, después de clonar el repo y hacer `uv sync --locked`, comprobar el archivo con PyYAML:
   `uv run python -c "import yaml,sys; yaml.safe_load(open(sys.argv[1]))" .github/ISSUE_TEMPLATE/config.yml`

##  Comportamiento Esperado
Que GitHub lea el archivo y aplique lo que pide:
- `blank_issues_enabled: false`: la issue en blanco solo la ve quien tiene permiso de escritura, marcada como "Maintainers only". El resto solo ve las plantillas.
- `contact_links`: en el menú de New issue sale el enlace de ayuda.

##  Comportamiento Actual
PyYAML no puede leer el archivo:

```text
yaml.scanner.ScannerError: mapping values are not allowed here
  in ".github/ISSUE_TEMPLATE/config.yml", line 2, column 21
```

La línea 1 no es `clave: valor`, así que YAML la toma como un texto y cree que la línea 2 sigue ese texto. Al llegar al `:` de `blank_issues_enabled:` (columna 21) da el error. GitHub no avisa de nada, simplemente ignora el archivo: "Blank issue" lo ve cualquiera y el enlace de ayuda no aparece.

##  Evidencia

Menú de New issue: sale "Blank issue" sin marca y no sale el enlace "Pregunta general".

<img width="1061" height="563" alt="Image" src="https://github.com/user-attachments/assets/c4f010c3-5b37-457a-bf8a-469876e04bbc" />

El archivo en GitHub, con las líneas 1 y 7 que sobran.

<img width="1522" height="418" alt="Image" src="https://github.com/user-attachments/assets/75a29ab4-af52-41b3-b5ff-6cf2a792b3ed" />

##  Entorno
| Campo        | Valor |
|-------------|-------|
| OS          | macOS (Apple Silicon) |
| Versión app | `main` en el commit `dbcb5e1` |
| Navegador   | Safari |
| Java / JDK  | No aplica |

##  Severidad
- [ ] 🔴 Crítica — el sistema no funciona
- [ ] 🟠 Alta — funcionalidad importante rota
- [x] 🟡 Media — funcionalidad parcialmente afectada
- [ ] 🟢 Baja — molestia menor o cosmética

## Solución propuesta
- Quitar las líneas 1 y 7 para que quede solo el YAML.
- Cambiar la url del enlace "Pregunta general", que ahora lleva al foro general de GitHub (`github.com/orgs/community/discussions`) y no sirve para la clase, por la web de la documentación: https://monium.github.io/gitanddocs/. Hasta ahora no se veía por el fallo, pero con el arreglo empezará a salir en el menú.

Me encargo yo del arreglo.

##  Proyecto
Añadida al Project DPL.
