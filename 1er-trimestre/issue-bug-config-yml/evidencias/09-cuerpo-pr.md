## Descripción
Arreglo `.github/ISSUE_TEMPLATE/config.yml`. Tenía dentro el comando de la terminal con el que se creó (`cat > .github/ISSUE_TEMPLATE/config.yml << 'EOF'` en la primera línea y `EOF` en la última), así que no era YAML válido y GitHub no aplicaba la configuración de las plantillas de issue.

- Quito la primera y la última línea para que quede solo el YAML.
- Cambio la url del enlace de ayuda "Pregunta general", que llevaba al foro general de GitHub (`github.com/orgs/community/discussions`), por la web de la documentación de la clase: https://monium.github.io/gitanddocs/

## Issue Relacionado
- Closes #41

## Tipo de Cambio
- [ ] Nueva funcionalidad (feature)
- [x] Corrección de errores (bugfix)
- [ ] Refactorización o limpieza de código
- [ ] Tests
- [ ] Documentación
- [x] Configuración / infraestructura
- [ ] Seguridad

## ¿Cómo se ha probado?
- [x] Pruebas manuales en local
- [ ] Tests unitarios ejecutados (`mvn test` / `npm test` / etc.)
- [ ] Tests de integración
- [ ] No requiere prueba (solo documentación o config)

Con el repo clonado y `uv sync --locked`, compruebo el archivo con PyYAML:

```bash
uv run python -c "import yaml,sys; yaml.safe_load(open(sys.argv[1]))" .github/ISSUE_TEMPLATE/config.yml
```

En `main` da este error:

```text
yaml.scanner.ScannerError: mapping values are not allowed here
  in ".github/ISSUE_TEMPLATE/config.yml", line 2, column 21
```

En `issue-41` no da ningún error y el archivo se lee bien:

```text
{'blank_issues_enabled': False, 'contact_links': [{'name': 'Pregunta general', 'url': 'https://monium.github.io/gitanddocs/', 'about': 'Si no sabes qué tipo de issue crear, consulta aquí primero.'}]}
```

También he pasado `uv run zensical build --clean`: "No issues found".

GitHub solo aplica `config.yml` cuando está en `main`, así que el resultado final se verá después del merge, en el menú de **New issue**:
- Sale el enlace "Pregunta general", que lleva a la web de la documentación.
- Quien no tiene permiso de escritura ya no ve la opción de issue en blanco. Quien sí lo tiene la sigue viendo, marcada como "Maintainers only".

## Lista de Verificación (Checklist)
- [x] El código funciona correctamente en mi entorno local.
- [x] He añadido o actualizado tests si era necesario. (No hace falta, es un archivo de configuración.)
- [x] La documentación está actualizada si era necesario. (No hace falta.)
- [x] No he subido credenciales, claves ni archivos temporales.
- [x] He vinculado este PR al issue correspondiente usando `Closes #ID`.

## Proyecto y Automatización
La issue #41 está en el Project DPL.

## Capturas de Pantalla (Opcional)
No aplica: el cambio solo se ve en el menú de New issue cuando esté en `main`.
