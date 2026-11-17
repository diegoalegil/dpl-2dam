# Semana del examen P1 (viernes 6 de noviembre)

Plan de estudio para los cinco días que quedan hasta el primer examen de DPL. Es la versión condensada de mis apuntes 04 a 07: lo imprescindible de la UT1 y la UT2 (las dos primeras unidades del curso), repartido por días y con ejercicios para hacer, no solo para leer.
Los apuntes [05](05-ut1-git-documentacion-cicd.md), [06](06-ut2-arquitecturas-servidores-web.md) y [07](07-plan-de-repaso-p1.md) quedan como consulta: solo los abro cuando este plan me manda a un apartado concreto o cuando algo no me queda claro.
Mi práctica de NGINX ([04](04-practica-nginx.md)) es el ejemplo que uso para casi todo.

## Índice

- [1. Cómo usar esta semana](#1-cómo-usar-esta-semana)
  - [1.1 Las reglas](#11-las-reglas)
  - [1.2 Un bloque de 2 h 30 min por dentro](#12-un-bloque-de-2-h-30-min-por-dentro)
  - [1.3 Si un día no te da tiempo](#13-si-un-día-no-te-da-tiempo)
- [2. Qué entra y qué priorizar](#2-qué-entra-y-qué-priorizar)
  - [2.1 Qué entra](#21-qué-entra)
  - [2.2 Los CE, por día y por prioridad](#22-los-ce-por-día-y-por-prioridad)
- [3. Calendario](#3-calendario)
  - [3.1 Test de diagnóstico (domingo, 15 minutos)](#31-test-de-diagnóstico-domingo-15-minutos)
- [4. Lunes 2/11: Git](#4-lunes-211-git)
  - [4.1 Plan del día](#41-plan-del-día)
  - [4.2 Lo imprescindible](#42-lo-imprescindible)
  - [4.3 Manos a la obra](#43-manos-a-la-obra)
  - [4.4 Comprueba que lo sabes](#44-comprueba-que-lo-sabes)
  - [4.5 Si te atascas](#45-si-te-atascas)
- [5. Martes 3/11: trabajo en equipo, documentación y CI/CD](#5-martes-311-trabajo-en-equipo-documentación-y-cicd)
  - [5.1 Plan del día](#51-plan-del-día)
  - [5.2 Lo imprescindible](#52-lo-imprescindible)
  - [5.3 Manos a la obra](#53-manos-a-la-obra)
  - [5.4 Comprueba que lo sabes](#54-comprueba-que-lo-sabes)
  - [5.5 Si te atascas](#55-si-te-atascas)
- [6. Miércoles 4/11: arquitecturas web y HTTP](#6-miércoles-411-arquitecturas-web-y-http)
  - [6.1 Plan del día](#61-plan-del-día)
  - [6.2 Lo imprescindible](#62-lo-imprescindible)
  - [6.3 Manos a la obra](#63-manos-a-la-obra)
  - [6.4 Comprueba que lo sabes](#64-comprueba-que-lo-sabes)
  - [6.5 Si te atascas](#65-si-te-atascas)
- [7. Jueves 5/11: nginx, servidores de aplicaciones, Docker y nube](#7-jueves-511-nginx-servidores-de-aplicaciones-docker-y-nube)
  - [7.1 Plan del día](#71-plan-del-día)
  - [7.2 Lo imprescindible](#72-lo-imprescindible)
  - [7.3 Manos a la obra](#73-manos-a-la-obra)
  - [7.4 Comprueba que lo sabes](#74-comprueba-que-lo-sabes)
  - [7.5 Si te atascas](#75-si-te-atascas)
- [8. Lo visto en clase que no está en la UT1 y la UT2 (por si acaso)](#8-lo-visto-en-clase-que-no-está-en-la-ut1-y-la-ut2-por-si-acaso)
  - [8.1 Plan del día](#81-plan-del-día)
  - [8.2 Lo imprescindible](#82-lo-imprescindible)
  - [8.3 Manos a la obra](#83-manos-a-la-obra)
  - [8.4 Comprueba que lo sabes](#84-comprueba-que-lo-sabes)
  - [8.5 Si te atascas](#85-si-te-atascas)
- [9. Simulacro 2 (jueves por la tarde, 60 minutos)](#9-simulacro-2-jueves-por-la-tarde-60-minutos)
  - [9.1 Parte A: test (3 puntos)](#91-parte-a-test-3-puntos)
  - [9.2 Parte B: respuesta corta (3 puntos)](#92-parte-b-respuesta-corta-3-puntos)
  - [9.3 Parte C: casos prácticos (4 puntos)](#93-parte-c-casos-prácticos-4-puntos)
  - [9.4 Soluciones](#94-soluciones)
- [10. Repaso de última hora (viernes por la mañana)](#10-repaso-de-última-hora-viernes-por-la-mañana)
  - [10.1 Puertos](#101-puertos)
  - [10.2 Códigos de estado](#102-códigos-de-estado)
  - [10.3 Comandos de Git imprescindibles](#103-comandos-de-git-imprescindibles)
  - [10.4 Claves de un workflow de GitHub Actions](#104-claves-de-un-workflow-de-github-actions)
  - [10.5 Directivas de NGINX](#105-directivas-de-nginx)
  - [10.6 Gunicorn frente a PHP-FPM](#106-gunicorn-frente-a-php-fpm)
  - [10.7 IaaS, PaaS y SaaS](#107-iaas-paas-y-saas)
  - [10.8 Comandos de Docker y Compose](#108-comandos-de-docker-y-compose)
  - [10.9 Estructura del README del profesor](#109-estructura-del-readme-del-profesor)
  - [10.10 Convención de commits del profesor](#1010-convención-de-commits-del-profesor)
  - [10.11 Trampas típicas](#1011-trampas-típicas)
  - [10.12 Durante el examen](#1012-durante-el-examen)
- [11. Registro de fallos](#11-registro-de-fallos)

## 1. Cómo usar esta semana

### 1.1 Las reglas

1. **Un bloque al día de unas 2 h 30 min.** Mejor de una vez y a la misma hora. Si no puedes, parte el bloque en dos mitades, pero hazlo el mismo día.
2. **Leer poco y hacer mucho.** De cada bloque, unos 40 minutos son de lectura activa: con un papel al lado, tapando cada tabla y diciéndola en voz alta. El resto, más de hora y media, es escribir comandos, completar configuraciones y contestar preguntas.
3. **Responder sin mirar y luego corregir.** Lee la pregunta, contesta en un papel o en voz alta y solo entonces abre la respuesta. Marca cada una como bien, a medias o mal. "A medias" cuenta como fallo.
4. **Apuntar cada fallo en el registro.** El registro de fallos (apartado 11) es una tabla donde apuntas lo que fallas, lo correcto y por qué te confundiste. Al empezar el día siguiente repasas sus filas sin marcar: así vuelves a lo difícil cuando ya se te empezaba a olvidar, que es cuando más se fija.
5. **Explicar en voz alta.** Cuenta cada concepto como si se lo explicaras a un amigo que no ha estudiado DPL. Donde te atascas, ahí está el hueco. Vale también para tu práctica: tienes que poder decir qué hace cada línea de tu `compose.yaml`, de tus `.conf` de NGINX y de tu `ci.yml`.
6. **Tandas sin móvil y descansos cortos.** Es la idea de la técnica pomodoro (trabajar concentrado un rato fijo y parar unos minutos), adaptada al bloque: cada fase del apartado 1.2 se hace del tirón y sin móvil, y después de las fases 1, 2 y 3 descansas 5 minutos.
7. **Dormir bien el jueves.** El jueves no estudies después de cenar. Dormir ayuda a fijar lo estudiado; una hora más de repaso a medianoche rinde menos que una noche entera de sueño.

Cuando un ejercicio use Docker (el programa que ejecuta contenedores), abre Docker Desktop al empezar el bloque. Al terminar, para lo que hayas levantado (`docker compose down` dentro de la carpeta de la práctica) y cierra Docker Desktop para no gastar batería ni memoria.

### 1.2 Un bloque de 2 h 30 min por dentro

Los días del lunes al jueves tienen las mismas fases:

| Fase | Qué haces | Tiempo |
|---|---|---|
| 0. Registro de fallos | Contestar las filas sin marcar del registro (apartado 11) tapando "Lo correcto" | 10 min |
| 1. Lo imprescindible | Leer la teoría del día con un papel al lado. Al acabar cada tabla, taparla y decirla en voz alta | 40 a 45 min |
| 2. Manos a la obra | Comandos de verdad y configuraciones escritas a mano. Antes de pulsar Enter, di qué salida esperas | 35 a 45 min |
| 3. Comprueba que lo sabes | Las preguntas del día sin mirar. Corriges al final, no después de cada una | 30 min |
| 4. Apuntar fallos | Apuntar los fallos en el registro, releer su punto y explicar en voz alta los CE del día (los criterios de evaluación, la lista de lo que se comprueba; están en el apartado 2) | 10 a 15 min |
| Descansos | 5 minutos de verdad después de las fases 1, 2 y 3: levántate, bebe agua, nada de pantallas | 15 min |

El reparto exacto de cada día está en su plan (apartados 4.1, 5.1, 6.1 y 7.1) y siempre suma 2 h 30 min.

### 1.3 Si un día no te da tiempo

Recorta en este orden:

1. **Primero, el apartado 8.** Es para el jueves y solo si sobra tiempo.
2. **Después, los bloques "Si te atascas".** Léelos solo si de verdad te has atascado en un ejercicio.
3. **Si aún vas justo**, haz a fondo los CE de prioridad alta (apartado 2) y los de prioridad media déjalos para la chuleta del apartado 10.

Lo que **no** se recorta nunca: los 10 minutos del registro de fallos y las preguntas sin mirar del final del día. Son lo que convierte la lectura en algo que recuerdas.

Si pierdes un día entero, no lo arrastres: al día siguiente haz el apartado que toca y, del día perdido, solo sus preguntas sin mirar. El jueves, si vas justo, el simulacro 2 no se toca: se cae el apartado 8.

## 2. Qué entra y qué priorizar

### 2.1 Qué entra

- **El P1** es el primer examen trimestral. Los tres exámenes (P1, P2 y P3) hacen media y valen el 50 % de la nota final; el otro 50 % es la media de las prácticas. El P1 es, por tanto, un tercio de ese 50 % (algo menos del 17 % de la nota final).
- Entra **todo lo trabajado en el primer trimestre**: la UT1 y la UT2. Una **UT** (unidad de trabajo) es cada tema del curso.
- Dicho con los nombres oficiales, entran el **RA6** (UT1: Git, documentación e integración continua) y el **RA1** (UT2: arquitecturas web, HTTP y HTTPS, estructura de una aplicación web, NGINX, servidores de aplicaciones Gunicorn y PHP-FPM, nube y contenedores). Un **RA** (resultado de aprendizaje) es lo que tienes que saber hacer al acabar; cada RA se divide en **CE** (criterios de evaluación), que son las cosas concretas que se comprueban.
- La web del curso dice que el examen es una **prueba objetiva**: un examen en el que cada pregunta tiene una respuesta correcta fijada de antemano y la nota no depende de la opinión de quien corrige.
- **El formato todavía no está publicado.** Según la web ([Evaluación](https://dpl-f1facc.gitlab.io/introduccion/evaluacion/) y [Preparación de los exámenes](https://dpl-f1facc.gitlab.io/evaluacion/preparacion-examen/)), el número de preguntas, los tipos de ejercicio y la puntuación los publica el profesor en el aula virtual antes de la prueba, y se detallan también en el enunciado del examen. Míralo en el aula virtual cada día de esta semana y, si sale, adapta el simulacro 2 a ese formato.
- Las prácticas 24, 25 y 26 son de ampliación (no cuentan para la nota de prácticas), pero lo que explican está en la teoría y puede salir.

### 2.2 Los CE, por día y por prioridad

La prioridad es **una apuesta mía, no un dato oficial**. La he sacado de cuántas páginas de teoría de la web trabajan cada CE y de cuánto espacio le dedican. "Alta" significa que lo trabajas a fondo en su día. "Media" no significa que no caiga: significa que, si vas justo de tiempo, te basta con la chuleta del apartado 10.

**RA6: documentación, control de versiones e integración continua (UT1)**

| CE | En sencillo | Día | Prioridad |
|---|---|---|---|
| RA6-a | Conozco herramientas que generan documentación: generadores de sitios estáticos (programas que convierten ficheros Markdown en una web HTML), como Zensical, MkDocs o Jekyll, y el propio GitHub, que muestra el Markdown ya formateado. | Martes | Media |
| RA6-b | Sé generar la web de la documentación con el generador de la plataforma: `zensical build` en clase, `mkdocs build --strict` en la práctica 02. | Martes | Media |
| RA6-c | Uso varios formatos de documentación: Markdown (texto plano con marcas sencillas, como `#` para los títulos), el README (la portada de un repositorio), la web HTML generada y los diagramas Mermaid (diagramas escritos como texto). | Martes | Media |
| RA6-d | Documento en equipo con herramientas colaborativas: issues (tareas o incidencias del proyecto), pull requests (peticiones para unir una rama a otra con revisión antes), revisiones y wikis. | Martes | Alta |
| RA6-e | Instalo, configuro y uso Git, el programa que guarda el historial de cambios de una carpeta: identidad, commits (cada foto guardada del proyecto), ramas (líneas de trabajo paralelas), fusiones y remotos (copias del repositorio en un servidor como GitHub). | Lunes | Alta |
| RA6-f | Mantengo el código accesible y seguro: copia en un remoto, claves SSH (un par de claves que te identifica sin escribir contraseña), tokens (credenciales que sustituyen a la contraseña), `.gitignore` (la lista de lo que Git no debe guardar) y ninguna contraseña dentro del repositorio. | Lunes | Alta |
| RA6-g | Documento cómo instalé, configuré y usé Git: README y un historial con commits bien escritos según la convención del profesor. | Lunes | Alta |
| RA6-h | Uso integración continua (CI: comprobar el proyecto de forma automática en cada cambio) con un workflow de GitHub Actions: un fichero YAML (formato de texto que se ordena con sangrías) con los pasos que GitHub ejecuta solo en cada push (subida de commits) o pull request. | Martes | Alta |

**RA1: implantación de arquitecturas web (UT2)**

| CE | En sencillo | Día | Prioridad |
|---|---|---|---|
| RA1-a | Analizo arquitecturas web (cómo se reparten el trabajo el cliente, los servidores y la red): cliente-servidor, capas y alternativas de implantación, con ventajas e inconvenientes. | Miércoles | Alta |
| RA1-b | Explico los protocolos (reglas para que dos programas se entiendan) en los que se apoya un servidor web: HTTP, HTTPS (HTTP cifrado con TLS, el protocolo que cifra la conexión), TCP/IP (los protocolos que llevan los datos por la red), y cómo llega la petición a la aplicación: en PHP, por FastCGI de NGINX a PHP-FPM; en Python, por HTTP de NGINX a Gunicorn y por WSGI de Gunicorn al código. | Miércoles | Alta |
| RA1-c | Instalo y configuro lo básico de un servidor web, el programa que entrega páginas y ficheros a quien los pide: NGINX. | Jueves | Alta |
| RA1-d | Instalo y configuro lo básico de un servidor de aplicaciones, el programa que ejecuta el código que genera la respuesta (Gunicorn para Python o PHP-FPM para PHP), y lo uno a NGINX. | Jueves | Alta |
| RA1-e | Instalo y configuro lo básico de contenedores (Docker: cajas aisladas con todo lo que necesita un programa) y de la nube (servidores alquilados por Internet, como AWS, descritos con Terraform, una herramienta que define la infraestructura en ficheros de texto). | Jueves | Media |
| RA1-f | Pruebo que los servidores funcionan: `curl` (cliente web de la terminal), `nginx -t` (comprueba la configuración), `ps` (lista los procesos en marcha), los logs (ficheros donde un programa apunta lo que hace) y `docker compose ps`. | Jueves | Alta |
| RA1-g | Analizo de qué está hecha una aplicación web: frontend (lo que ve el usuario), backend (la lógica que corre en el servidor) y datos; contenido estático (ficheros que se sirven tal cual) y dinámico (se genera en cada petición). | Miércoles | Media |
| RA1-h | Describo qué hace falta para implantar una aplicación: máquina, sistema operativo, red, IP (la dirección de una máquina en la red), DNS (el sistema que traduce nombres a direcciones IP), disco y permisos. | Miércoles | Media |
| RA1-i | Documento lo que instalo y configuro: README con comandos y salidas reales, y un commit por paso. | Jueves | Media |

Cuando sepas explicar un CE en voz alta sin mirar y con un ejemplo, márcalo como sabido en la tabla de [07, apartado 2](07-plan-de-repaso-p1.md) (cambia `[ ]` por `[x]`). El jueves por la noche deberían estar marcados todos los de prioridad alta.

## 3. Calendario

Cada día empieza igual: **10 minutos con el registro de fallos** (apartado 11), repasando las filas que aún no están marcadas como superadas.

| Día | Primer paso | Qué toca | CE | Tiempo |
|---|---|---|---|---|
| Domingo 1/11 (hoy) | Hoy no hay registro todavía: lo estrenas con el test | Leer los apartados 1 a 3 (15 min) y hacer el test de diagnóstico del apartado 3.1 (15 min). Apuntar sus fallos en el registro | Todos, por encima | 30 min |
| Lunes 2/11 | Registro de fallos: los del test de diagnóstico (10 min) | Apartado 4: Git | RA6-e, RA6-f, RA6-g | 2 h 30 min |
| Martes 3/11 | Registro de fallos: los del lunes y los que sigan sin marcar (10 min) | Apartado 5: documentación, trabajo en equipo con GitHub y CI/CD | RA6-a, RA6-b, RA6-c, RA6-d, RA6-h | 2 h 30 min |
| Miércoles 4/11 | Registro de fallos: los del martes y los que sigan sin marcar (10 min) | Apartado 6: arquitecturas web, HTTP y HTTPS, estructura de una aplicación y requisitos de implantación | RA1-a, RA1-b, RA1-g, RA1-h | 2 h 30 min |
| Jueves 5/11 | Registro de fallos: los del miércoles y los que sigan sin marcar (10 min) | Bloque principal: apartado 7 (NGINX, Gunicorn y PHP-FPM, nube y contenedores). Por la tarde: simulacro 2 del apartado 9 con reloj, y corregirlo. El apartado 8, solo si sobra tiempo. Cenar pronto y a dormir | RA1-c, RA1-d, RA1-e, RA1-f, RA1-i | 2 h 30 min + simulacro |
| Viernes 6/11 | Registro de fallos: solo las filas sin marcar (10 min) | Por la mañana, 30 min con el apartado 10. Nada nuevo. Después, el examen | Todos | 40 min (hasta 55 si el simulacro 2 baja de 8: ver su tabla del apartado 9) |

### 3.1 Test de diagnóstico (domingo, 15 minutos)

Para qué sirve: saber desde dónde partes y qué días te van a costar más. No es para aprobarlo.

Cómo hacerlo:

- Papel y boli, sin mirar nada, 15 minutos con reloj (algo más de un minuto por pregunta).
- Contesta las 12 antes de abrir ninguna respuesta. Si no sabes una, escribe "no lo sé" y pasa a la siguiente.
- Después corrige cada una como bien, a medias o mal, y apunta en el registro (apartado 11) las que no estén bien, con fecha 1/11.

**D1.** Git guarda los cambios pasando por tres zonas. ¿Cuáles son y qué comando lleva un cambio de una zona a la siguiente?

<details>
<summary>Respuesta</summary>

1. **Working directory** (directorio de trabajo): los ficheros tal y como están en tu carpeta. Aquí es donde editas.
2. **Index o staging** (zona de preparación): los cambios que entrarán en el próximo commit. Un cambio llega aquí con `git add fichero`.
3. **Repositorio o HEAD** (la web del curso llama así a esta zona): la historia ya guardada. **HEAD** es el commit en el que estás ahora (el último de tu rama). Se llega aquí con `git commit`.

La regla: editas, preparas (`git add`) y fijas (`git commit`). Solo lo que está en el staging entra en el commit. `git status` te dice en qué zona está cada cambio.

Analogía: preparar un paquete. Metes cosas en la caja (`git add`) y la cierras con su etiqueta (`git commit`). Lo que no metiste en la caja no viaja, aunque esté encima de la mesa.

</details>

Si la fallas: refuerza el lunes (apartado 4).

**D2.** Escribe el comando completo para guardar, con la convención de commits del módulo, el paso "instalar NGINX y comprobar que responde". Los ficheros ya están preparados con `git add`.

<details>
<summary>Respuesta</summary>

```bash
git commit -m "Instalar nginx y verificar el servicio" \
           -m "Instalé nginx con apt-get dentro del contenedor dpl-lab y comprobé con curl -I http://localhost/ que responde 200 OK."
```

- El primer `-m` es el **subject**: una línea corta en imperativo que resume el paso. Puede llevar delante un tipo (`feat:`, `fix:`, `docs:`), pero es opcional.
- El segundo `-m` es el **cuerpo**: explica cómo y por qué, con los comandos y el resultado.
- Un commit por paso. Mensajes como "entrega final" no valen.

</details>

Si la fallas: refuerza el lunes (apartado 4).

**D3.** ¿Qué diferencia hay entre `git fetch` y `git pull`?

<details>
<summary>Respuesta</summary>

- `git fetch` **descarga** los commits nuevos del remoto, pero **no toca tu rama**. Puedes mirarlos antes de decidir: `git log main..origin/main` lista los commits que ya tiene `origin/main` (la copia local de la rama del remoto) y tu `main` todavía no, y `git diff main origin/main` enseña los cambios.
- `git pull` descarga **y además fusiona** en tu rama.

Regla para recordarlo: pull = fetch + merge.

</details>

Si la fallas: refuerza el lunes (apartado 4).

**D4.** Quieres aportar un cambio a un repositorio en el que no tienes permiso de escritura. Ordena estos pasos: abrir el pull request, fork, merge, crear una rama, push a tu fork, revisión, clonar tu fork, hacer commits. Después di qué son `origin` y `upstream` en ese flujo.

<details>
<summary>Respuesta</summary>

1. **Fork**: copia del repositorio original en tu cuenta de GitHub.
2. **Clonar tu fork** en tu ordenador.
3. **Crear una rama** (`git switch -c mi-cambio`). Nunca se trabaja directamente sobre `main`.
4. **Hacer commits**.
5. **Push a tu fork** (`git push -u origin mi-cambio`).
6. **Abrir el pull request** hacia el repositorio original.
7. **Revisión**: comentarios y, si te piden cambios, más commits en la misma rama (el PR se actualiza solo).
8. **Merge**: lo hace quien mantiene el original. Si el PR lleva `Closes #N`, la issue N se cierra sola.

`origin` es **tu fork**. `upstream` es **el repositorio original**. Antes de cada aportación sincronizas tu `main` con el original: `git fetch upstream` y `git merge upstream/main`.

</details>

Si la fallas: refuerza el martes (apartado 5).

**D5.** ¿En qué carpeta del repositorio va un workflow de GitHub Actions? ¿Qué indican las claves `on`, `jobs` y `steps`?

<details>
<summary>Respuesta</summary>

Va en `.github/workflows/`, como fichero `.yml` (en mi práctica, `.github/workflows/ci.yml`).

- `on`: los **eventos** que lo disparan, por ejemplo `push`, `pull_request` o `workflow_dispatch` (lanzarlo a mano).
- `jobs`: los **trabajos**. Cada uno corre en un runner, una máquina virtual que pone GitHub y que eliges con `runs-on`.
- `steps`: los **pasos** de cada trabajo, en orden. Un paso usa una acción ya hecha con `uses` (por ejemplo `actions/checkout@v4`, que descarga el repositorio) o ejecuta comandos con `run`.

</details>

Si la fallas: refuerza el martes (apartado 5).

**D6.** Escribe, sin mirar, una petición HTTP/1.1 mínima para pedir la portada de `www.alumno.local`.

<details>
<summary>Respuesta</summary>

```text
GET / HTTP/1.1
Host: www.alumno.local

```

- **Línea de petición**: método (`GET`), recurso (`/`) y versión (`HTTP/1.1`).
- **Cabeceras**: líneas `Nombre: valor`. `Host` es obligatoria en HTTP/1.1: con ella un mismo servidor sabe cuál de sus sitios le piden.
- **Línea en blanco**: marca el final de las cabeceras. Un GET normal no lleva cuerpo.

</details>

Si la fallas: refuerza el miércoles (apartado 6).

**D7.** ¿Qué significa cada uno de estos códigos de estado: 200, 301, 403, 404 y 500?

<details>
<summary>Respuesta</summary>

| Código | Significado |
|---|---|
| 200 OK | Todo correcto: el servidor ha devuelto lo que pedías |
| 301 Moved Permanently | Se ha movido para siempre a otra URL, que va en la cabecera `Location` |
| 403 Forbidden | El servidor entiende lo que pides, pero no te deja (por ejemplo, permisos de ficheros mal) |
| 404 Not Found | No existe donde el servidor lo busca |
| 500 Internal Server Error | El servidor ha fallado al procesar la petición (por ejemplo, un error en el código de la aplicación) |

Truco: 4xx, la culpa es del cliente; 5xx, la culpa es del servidor.

</details>

Si la fallas: refuerza el miércoles (apartado 6).

**D8.** En una arquitectura de tres capas, ¿qué capas hay y qué programa del curso va en cada una?

<details>
<summary>Respuesta</summary>

Delante de todo está el **cliente** (el navegador o `curl`), que hace la petición. Detrás, las tres capas:

1. **Presentación**: el servidor web, **NGINX**. Sirve lo que ve el cliente (HTML, CSS, imágenes).
2. **Aplicación o lógica de negocio**: el servidor de aplicaciones, **Gunicorn** (Python) o **PHP-FPM** (PHP). Ejecuta el código.
3. **Datos**: la **base de datos** (en el curso, PostgreSQL) o ficheros. Guarda la información que dura.

Mi práctica es más sencilla: solo sirve webs estáticas, así que no tiene capa de aplicación ni de datos. Es cliente y servidor web (dos capas).

Ojo: la web del curso también presenta un modelo de cuatro capas, que cuenta al cliente (el navegador) como una capa más: cliente, presentación, lógica de negocio y datos. Si te preguntan por cuatro capas, es ese.

</details>

Si la fallas: refuerza el miércoles (apartado 6).

**D9.** Has cambiado un fichero `.conf` de NGINX. ¿Qué dos comandos ejecutas, en qué orden y por qué?

<details>
<summary>Respuesta</summary>

1. `nginx -t`: comprueba la sintaxis de toda la configuración. Si está bien dice `syntax is ok` y `test is successful`; si no, te da el fichero y la línea del error.
2. Solo si el paso 1 va bien, `nginx -s reload`: recarga la configuración sin cortar el servicio.

Después compruebas con `curl -I`. El ciclo completo es: editar, `nginx -t`, `nginx -s reload`, `curl -I`.

En mi práctica NGINX va dentro de un contenedor, así que los mismos comandos se lanzan con `docker compose exec nginx nginx -t` y `docker compose exec nginx nginx -s reload` (el primer `nginx` es el nombre del servicio en el `compose.yaml` y el segundo, el programa).

</details>

Si la fallas: refuerza el jueves (apartado 7).

**D10.** NGINX tiene que pasar las peticiones a una aplicación Flask servida por Gunicorn en el puerto 8000 de la misma máquina. ¿Qué directiva escribes? ¿Y si fuera PHP con PHP-FPM?

<details>
<summary>Respuesta</summary>

Con Gunicorn, `proxy_pass` (en la práctica se añaden también las líneas `proxy_set_header`):

```nginx
location / {
    proxy_pass http://127.0.0.1:8000;
}
```

Con PHP-FPM, `fastcgi_pass` dentro de la `location` de los `.php`:

```nginx
location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/run/php/php8.3-fpm.sock;
}
```

- `proxy_pass`: NGINX hace de **proxy inverso** (recibe la petición y la reenvía a otro servidor) y le habla por HTTP a Gunicorn. Gunicorn, a su vez, llama a Flask con WSGI.
- `fastcgi_pass`: NGINX le habla a PHP-FPM con el protocolo FastCGI, por un socket UNIX (un fichero especial, solo vale en la misma máquina) o por TCP (`php-fpm:9000` entre contenedores).
- NGINX no ejecuta ni Python ni PHP: solo pasa la petición.

</details>

Si la fallas: refuerza el jueves (apartado 7).

**D11.** Pides la calculadora y NGINX responde `502 Bad Gateway`. ¿Qué significa y qué compruebas primero?

<details>
<summary>Respuesta</summary>

NGINX funciona, pero **no consigue respuesta del servidor de aplicaciones**: Gunicorn o PHP-FPM están parados, o la dirección de `proxy_pass` o `fastcgi_pass` no es la buena.

Comprueba, en este orden:

1. Que el proceso está vivo: `ps aux | grep gunicorn` (o `grep php-fpm`).
2. Que responde por su cuenta: `curl -I http://127.0.0.1:8000/` con Gunicorn, o `ls /run/php/` para ver que existe el socket de PHP-FPM.
3. El `error.log` de NGINX, que dice a qué dirección intentó conectar.

Si el servidor de aplicaciones estuviera arrancado pero tardara demasiado, el código sería **504** Gateway Timeout.

</details>

Si la fallas: refuerza el jueves (apartado 7).

**D12.** En el `compose.yaml` de mi práctica pone `ports: - "8080:80"`. ¿Cuál es el puerto de mi Mac y cuál el del contenedor? ¿Qué URL abro en el navegador?

<details>
<summary>Respuesta</summary>

- **8080** es el puerto del **anfitrión** (el equipo donde corre Docker, mi Mac).
- **80** es el puerto **dentro del contenedor**, donde escucha NGINX (`listen 80;`).
- El orden siempre es `anfitrión:contenedor`.

La URL es `http://localhost:8080/`. Es como un desvío: lo que llega a la puerta 8080 de mi Mac, Docker lo pasa a la puerta 80 del contenedor.

</details>

Si la fallas: refuerza el jueves (apartado 7).

#### 3.1.1 Cómo leer el resultado

| Bien | Qué significa |
|---|---|
| 0 a 4 | Lo normal hoy: partes casi de cero. El plan está hecho justo para esto |
| 5 a 8 | Tienes base. Fíjate en qué día se concentran los fallos: ese día, ve sin prisa |
| 9 a 12 | Vas bien. Usa el tiempo que te sobre en los CE de prioridad alta y en el apartado 8 |

Fallar muchas hoy **no pasa nada**: el test no cuenta para nada y está pensado para que falles. Lo que importa es la lista que sale de él. Cada fallo apuntado en el registro vuelve el lunes por la mañana y, cuando llegue su día, lo trabajas a fondo. El jueves deberías poder contestar las 12 sin dudar.

## 4. Lunes 2/11: Git

Hoy toca Git en local y en remoto. Al acabar el día sabrás explicar las tres zonas de Git, escribir commits con la convención del profe, trabajar con ramas, resolver un conflicto, etiquetar una versión y subirla sin filtrar nada.
Entra seguro en el P1 porque es el corazón del RA6 (el resultado de aprendizaje de documentación, control de versiones e integración continua). Cubre tres criterios de evaluación (CE): **RA6-e** (instalar, configurar y usar Git), **RA6-f** (que el código guardado esté accesible y seguro) y **RA6-g** (documentar cómo instalaste, configuraste y usaste Git).

### 4.1 Plan del día

| Orden | Bloque | Tiempo | Qué haces | Está hecho cuando... |
|---|---|---|---|---|
| 0 | Registro de fallos | 10 min | Vuelve a contestar las filas sin marcar del registro (apartado 11): hoy, las del test de diagnóstico | Has contestado cada fila tapando "Lo correcto" |
| 1 | Lo imprescindible (4.2) | 40 min | Lee los 14 puntos. En cada tabla, tapa la columna de la derecha y dila en voz alta | Sabes explicar cada punto sin mirar |
| 2 | Manos a la obra (4.3) | 45 min | Haz el laboratorio en `/tmp/ensayo-git` escribiendo tú los comandos, sin copiar y pegar | Tu grafo final se parece al del paso 7 |
| 3 | Comprueba que lo sabes (4.4) | 30 min | Contesta P1 a P14 en papel antes de abrir las respuestas | Las has corregido todas |
| 4 | Apuntar fallos | 10 min | Apunta cada fallo en el registro (apartado 11) y relee su punto de 4.2 | Cada fallo tiene su fila, con "por qué me confundí" |

Después de los bloques 1, 2 y 3, 5 minutos de descanso de verdad (levántate, bebe agua, nada de pantallas). Total: 2 h 15 min de trabajo más 15 min de descansos, 2 h 30 min.

### 4.2 Lo imprescindible

#### 4.2.1 Qué es Git y qué es un repositorio

Un **sistema de control de versiones** (VCS, Version Control System) es un programa que guarda la historia de los cambios de una carpeta: qué cambió, quién lo cambió y cuándo. Te deja volver a cualquier estado anterior. **Git** es el más usado (lo creó Linus Torvalds en 2005).

> Analogía: las partidas guardadas de un videojuego. Cada **commit** (cada punto guardado de la historia, ver 4.2.4) es una partida a la que puedes volver si luego algo sale mal.

- **Repositorio** (repo): los ficheros versionados y su historia. Nada más. Vive en la carpeta oculta `.git` que crea `git init`. Si borras `.git`, pierdes la historia (y una entrega sin `.git` no se valora). Un **proyecto** es más: el repositorio más lo que añade la plataforma (issues o fichas de tareas, control de acceso, wiki, integraciones).
- Git es **distribuido**: cada copia tiene la historia completa, así que commits, ramas y `git log` funcionan sin red. Solo `fetch`, `pull` y `push` hablan con el **remoto** (la copia del repo en un servidor, ver 4.2.11). En un VCS **centralizado** (como Subversion) la historia está solo en el servidor.
- **Git no es GitHub.** La web lo ordena en tres capas: **sistema** (el propio VCS: Git, Subversion, Mercurial, CVS), **cliente** (el programa para usarlo: la terminal, GitHub Desktop, GitKraken, VS Code) y **servicio** (la web que aloja repos y añade colaboración: GitHub, GitLab, Bitbucket, Gitea).

#### 4.2.2 Las tres zonas y los estados de un fichero

| Zona | Otros nombres | Qué hay | Cómo llega algo ahí |
|---|---|---|---|
| Directorio de trabajo | working directory, working tree | Tus ficheros tal como los ves y editas | Editando |
| Área de preparación | staging, index | Lo que has elegido para el próximo commit | `git add` |
| Repositorio | la historia; la web la llama HEAD (tu commit actual, ver 4.2.7) | Los commits guardados dentro de `.git` | `git commit` |

> Analogía: el carrito de la compra. La tienda es el directorio de trabajo, meter cosas en el carrito es `git add` y pagar es `git commit`. Solo te cobran lo que hay en el carrito. Regla mental de la web: **editas, preparas (`add`) y fijas (`commit`)**. Todo esto pasa en tu ordenador hasta que haces `git push`.

| Estado | En español | Qué significa | En `git status -s` |
|---|---|---|---|
| untracked | sin seguimiento | Git lo ve en la carpeta, pero nunca lo has añadido | `??` |
| staged | preparado | Está en el staging y entrará en el próximo commit | `A ` (nuevo) o `M ` (modificado) |
| committed | confirmado | Guardado en la historia, sin cambios pendientes | No sale |
| modified | modificado | Versionado y con cambios sin preparar | ` M` (con un espacio delante) |
| ignored | ignorado | Lo cubre un patrón de `.gitignore`; Git ni lo ofrece para añadir | No sale (con `--ignored` sale `!!`) |

`git status -s` es el estado en corto: la columna de la izquierda es el staging y la de la derecha el directorio de trabajo (`MM` es parte preparada y parte sin preparar). Un conflicto sin resolver sale como `UU`. La web nombra también **tracked** (con seguimiento): cualquier fichero que Git ya conoce, esté confirmado, modificado o preparado. Es lo contrario de untracked.

#### 4.2.3 Instalación e identidad

`git --version` comprueba que Git está instalado y contesta en inglés aunque tengas Git en español (en mi Mac, `git version 2.54.0`; la web pide orientativamente **2.40 o superior**). En macOS se instala con `xcode-select --install` (herramientas de línea de comandos de Xcode) o con `brew install git` (Homebrew, el gestor de paquetes).

Antes del primer commit hay que configurar la **identidad**: el nombre y el correo que Git graba como autor dentro de cada commit. El profe exige `user.name` = tu nombre y apellidos tal como salen en el aula virtual, y `user.email` = el correo de tu cuenta del aula virtual.

| Nivel | Comando | Se guarda en | A qué afecta |
|---|---|---|---|
| `--global` | `git config --global user.name "..."` | `~/.gitconfig` (tu carpeta personal) | Todos tus repos |
| `--local` | `git config --local user.name "..."` (dentro del repo) | `.git/config` del repo | Solo ese repo, y **gana a la global** |

Prioridad: local gana a global, y global gana a system (`--system`, para todos los usuarios del equipo, casi no se usa). La web enseña las dos; en mis entregas uso `--local`, porque `.git/config` viaja dentro del ZIP. Por qué insiste el profe: la entrega es un ZIP **con `.git`** y la identidad viaja dentro de cada commit. La web avisa de que una entrega sin esta configuración **puntuará cero**. Se comprueba así:

```bash
git config --show-origin user.name          # qué nombre se usa y de qué fichero sale (file:.git/config)
git log --format='%an <%ae>' | sort -u      # autores de todos los commits: debe salir UNA línea, la tuya
```

`%an` es el nombre del autor, `%ae` su correo y `sort -u` ordena y quita repetidos. Ojo: si no hay nada configurado, Git **no da error**. Se inventa una identidad con tu usuario del Mac y el nombre del equipo (en el mío, `Diego Gil González <diego@MacBook-Pro-de-Diego.local>`) y solo avisa. Cambiar la configuración después **no arregla** los commits ya hechos. Si solo está mal el último y no lo has subido: corrige la configuración y haz `git commit --amend --reset-author`.

#### 4.2.4 El commit y la convención del profesor

Un **commit** es una foto de lo que hay en el staging, guardada en la historia. Cada commit lleva un **hash** (su identificador: 40 caracteres hexadecimales, de los que `--oneline` enseña unos 7, como `561f839`), el autor, la fecha, el mensaje y un enlace a su commit **padre** (el anterior). Así se forma la cadena de la historia.

Convención obligatoria del módulo, según la web del curso:

- **Subject** (asunto): una línea corta con el verbo en **imperativo** que resume el paso. Ejemplos de la web: `Instalar nginx y verificar el servicio`, `Añade server block HTTPS del despliegue`.
- **Cuerpo**: tras una línea en blanco, **qué** hiciste, **cómo** (comandos y resultados) y **por qué**.
- Los dos se escriben en un solo comando con dos `-m`. Cada `-m` es un párrafo y Git pone él solo la línea en blanco entre los dos:

```bash
git commit -m "Instalar nginx y verificar el servicio" \
           -m "Ejecuté apt-get install nginx dentro del contenedor dpl-lab y comprobé con curl -I http://localhost/ que responde 200 OK."
```

- **Un commit por paso** (un cambio lógico). Nada de diez cosas en un commit.
- Mensajes que no valen: `final`, `entrega final`, `primera entrega`, `cambios`, `nueva funcionalidad`. Un historial así no acredita el trabajo. En cambio, los errores que quedan en la historia **y se arreglan después** se valoran a favor.
- El prefijo de Conventional Commits (un estándar que pone el tipo de cambio delante: `feat:`, `fix:`, `docs:`) es **opcional**.
- `git commit -am "..."` prepara y confirma de golpe lo que ya estaba versionado, pero **no incluye ficheros nuevos** (untracked).
- RA6-g: el historial también es documentación. Junto con el README (la portada del repo, que recoge `git --version`, la configuración y los comandos usados) demuestra cómo instalaste, configuraste y usaste Git.
- En mi práctica los subjects van en primera persona (`Arreglo la redirección...`), no en imperativo. Cómo lo defiendo, en [04, apartado 4](04-practica-nginx.md).

#### 4.2.5 Mirar el historial y los cambios

| Comando | Qué enseña |
|---|---|
| `git status` | En qué rama estás y en qué zona está cada cambio (`-s`, en corto) |
| `git log` | Historia completa: hash entero, autor, fecha y mensaje con su cuerpo |
| `git log --oneline` | Un commit por línea: hash corto y subject |
| `git log --oneline --graph --all` | Además dibuja las ramas, todas (también las remotas) |
| `git diff` | Directorio de trabajo frente a staging: lo que **aún no** has preparado. Trampa: después de `git add` sale **vacío** |
| `git diff --staged` | Staging frente al último commit: lo que **va a entrar** en el commit |
| `git show <hash>` | Qué hizo un commit concreto (mensaje y cambios) |
| `git diff HEAD~1 HEAD` | Qué cambió el último commit respecto al anterior |
| `git shortlog -sn` | Cuántos commits ha hecho cada autor (`git shortlog` a secas los agrupa por autor con sus subjects) |
| `git blame fichero` | Quién y en qué commit cambió cada línea del fichero |

#### 4.2.6 Deshacer

| Situación | Comando | ¿Reescribe la historia? |
|---|---|---|
| Tirar los cambios sin preparar de un fichero | `git restore fichero` | No (y lo tirado **no se recupera**) |
| Sacar un fichero del staging sin perder los cambios | `git restore --staged fichero` | No |
| Dejar de versionar un fichero sin borrarlo del disco | `git rm --cached fichero` y commit | No |
| Corregir el último commit (mensaje o fichero olvidado) | `git commit --amend` | **Sí**: crea otro commit con otro hash |
| Anular un commit que ya está subido | `git revert <hash>` | No: añade un commit nuevo que lo deshace |
| Volver la rama a un commit y tirar todo lo posterior | `git reset --hard <hash>` | **Sí**, y es peligroso |
| Cancelar un merge con conflicto | `git merge --abort` | No |

**Revert frente a reset**: `revert` añade un commit "al revés": la historia solo crece y nadie nota nada raro. `reset --hard` mueve la rama hacia atrás y los commits posteriores desaparecen de ella. **Regla de oro: no reescribas historia compartida.** `--amend`, `reset --hard` y `rebase` (4.2.10) cambian hashes o tiran commits. Si esos commits ya estaban subidos, tu rama deja de descender de la del remoto: GitHub rechaza tu `push`, tendrías que forzarlo (`git push --force`) y romperías la historia de quien ya los tuviera. En local y antes de subir, sin problema. Ya subido, usa `git revert`.

**Guardar el trabajo a medias con `stash`.** Si tienes cambios sin commit y necesitas cambiar de rama con todo limpio, `git stash` los guarda aparte y deja el directorio como en el último commit. Responde `Directorio de trabajo y estado de índice WIP on main: a7a70b4 Fusiona guardados` (salida real; tú verás tu rama, tu hash y tu último subject). Los guardados forman una **pila** (el último que entra es el primero que sale):

| Comando | Qué hace |
|---|---|
| `git stash` | Guarda los cambios de los ficheros **versionados** |
| `git stash -u` | Guarda también los ficheros **sin seguimiento** (*untracked*) |
| `git stash list` | Lista la pila: `stash@{0}` es el más reciente |
| `git stash pop` | Recupera el último y **lo quita** de la pila |
| `git stash apply` | Recupera el último y **lo deja** en la pila |

Dos más de la web que basta con reconocer: `git cherry-pick <hash>` copia un commit concreto de otra rama en la tuya, y `git clean -fd` borra los ficheros y carpetas **sin seguimiento** (lo versionado no lo toca, y lo borrado no se recupera).

#### 4.2.7 Ramas y HEAD

Una **rama** es una línea de trabajo independiente. Por dentro es solo una etiqueta móvil (un **puntero**) que señala un commit y avanza sola con cada commit nuevo. Por eso crear una rama es instantáneo. La principal es `main` (antes se llamaba `master`).

> Analogía: una rama es un borrador. Pruebas en el borrador y, si sale bien, lo pasas a limpio (merge). Si sale mal, lo tiras y el original sigue intacto.

**HEAD** es el puntero que dice **dónde estás tú**: normalmente apunta a tu rama actual. `HEAD~1` es el commit anterior al tuyo y `HEAD~2` el de antes.

| Comando | Qué hace | Forma antigua equivalente |
|---|---|---|
| `git branch` | Lista las ramas locales (la actual con `*`) | |
| `git branch docs` | Crea `docs`, pero **no** te cambia a ella | |
| `git switch docs` | Te cambia a `docs` | `git checkout docs` |
| `git switch -c docs` | Crea `docs` y te cambia a ella | `git checkout -b docs` |
| `git switch -` | Vuelve a la rama anterior | `git checkout -` |
| `git branch -d docs` | Borra `docs` si ya está fusionada (`-D` la borra aunque no lo esté: pierdes sus commits) | |

`git checkout <hash>` te lleva a un commit antiguo y te deja en **HEAD desacoplada** (detached HEAD): HEAD apunta a un commit, no a una rama, y `git status` dice `HEAD desacoplada en cc13d72`. Lo que confirmes ahí no queda en ninguna rama. Para volver: `git switch -`. Para conservar lo hecho: `git switch -c rama-nueva`.

#### 4.2.8 Fusionar: fast-forward frente a `--no-ff`

**Fusionar** (merge) es traer los commits de otra rama a la tuya. Primero te pones en la rama que **recibe** (`git switch main`) y después fusionas (`git merge docs`). Si la rama que recibe no se ha movido, Git hace un **fast-forward** (avance rápido): solo adelanta su puntero.

```text
Antes:                         A---B             main
                                    \
                                     C---D       docs

git merge docs (fast-forward): A---B---C---D     main y docs en el mismo commit
                               no hay commit nuevo: main solo avanza

git merge --no-ff docs:        A---B-------M     main
                                    \     /
                                     C---D       docs
                               M es un commit de fusión con dos padres (B y D)
```

- **Fast-forward**: Git imprime `Fast-forward`, no crea commit y en `--graph` queda todo en línea recta: no se nota que hubo una rama.
- **`--no-ff`**: Git imprime `Merge made by the 'ort' strategy.` (`ort` es el algoritmo de fusión por defecto) y crea el commit de fusión. En `--graph` se ve la "burbuja" de la rama. El curso lo pide para que el grafo muestre que trabajaste por ramas (en mi práctica, `Junto la fase 1 en main` y `Junto la fase 2 en main`).
- Si **las dos ramas han avanzado** (han divergido), el fast-forward es imposible y Git crea siempre un commit de fusión, con o sin `--no-ff`.

#### 4.2.9 Conflictos

Hay **conflicto** cuando las dos ramas cambiaron **las mismas líneas** del mismo fichero y Git no sabe con cuál quedarse. Git para la fusión y deja marcas en el fichero:

```text
<<<<<<< HEAD
Color: naranja
=======
Color: verde
>>>>>>> color
```

Entre `<<<<<<< HEAD` y `=======` está lo de **tu rama actual** (la que recibe). Entre `=======` y `>>>>>>> color` está lo que **llega de la otra rama** (aquí, `color`). Se resuelve así:

1. `git status`: busca `modificados por ambos: README.md` (en corto, `UU README.md`).
2. Abre el fichero, deja el contenido final (una versión, la otra o una mezcla) y **borra las tres líneas de marcas**.
3. `git add README.md` para marcarlo como resuelto. Cuidado: Git **no comprueba** que hayas borrado las marcas; si quedan, se guardan en el commit. `git diff --check` las detecta antes (avisa con `leftover conflict marker`).
4. `git commit` (con sus `-m`) para cerrar la fusión.
5. Si te pierdes: `git merge --abort` lo deja todo como antes del merge.

#### 4.2.10 Rebase: solo la idea

`git rebase main`, hecho desde tu rama, **vuelve a aplicar tus commits encima de `main`**, como si hubieras empezado a trabajar más tarde. La historia queda en línea recta y sin commit de fusión, pero tus commits pasan a ser **commits nuevos con otro hash** (merge, en cambio, conserva los hashes y deja ver la rama). Por eso solo se hace con commits que aún no has subido. En el curso se usa merge: el rebase basta con reconocerlo.

#### 4.2.11 Remotos

Un **remoto** es un nombre corto que apunta a la URL de otra copia del repo (en GitHub, GitLab o Gitea).

- **origin**: el nombre, por convención, del remoto principal. `git clone` lo crea solo.
- **upstream** tiene dos sentidos. (1) Con un **fork** (tu copia de un repo ajeno en tu cuenta), es el remoto del **repositorio original**, mientras que `origin` es tu fork. (2) La **rama upstream** de una rama local es la rama remota a la que está vinculada (`main` sigue a `origin/main`).
- `origin/main` es la **foto** que tu repo guarda de la rama `main` del remoto. Solo se actualiza cuando tu Git habla con el remoto: `fetch`, `pull` o `push`.

| Comando | Qué hace |
|---|---|
| `git clone URL` | Copia el repo entero (con su historia) y crea `origin` |
| `git remote -v` | Lista los remotos y sus URL |
| `git remote add upstream URL` | Añade un remoto (`git remote set-url` le cambia la URL y `git remote remove nombre` lo quita) |
| `git fetch origin` | Descarga los commits nuevos **sin tocar tus ramas** |
| `git pull` | **`fetch` + `merge`**: descarga y fusiona en tu rama |
| `git push origin main` | Sube tus commits de `main` |
| `git push -u origin rama` | Sube una rama nueva y le fija su upstream (solo la primera vez; `-u` es la forma corta de `--set-upstream`). Sin él, el primer `git push` falla con `fatal: La rama actual main no tiene una rama upstream.` |
| `git branch -vv` | A qué rama remota sigue cada rama local |

> Analogía: `fetch` es recoger las cartas del buzón y dejarlas en la mesa sin abrir. `pull` es recogerlas y archivarlas. `push` es mandar las tuyas.

#### 4.2.12 Etiquetas y versionado semántico

Una **etiqueta** (tag) es un nombre fijo para un commit: marca una versión. A diferencia de una rama, **no se mueve**. Hay dos tipos: la **ligera** (`git tag v1.0.0`) es solo un nombre que apunta al commit; la **anotada** (`git tag -a v1.0.0 -m "Primera versión estable"`, la del curso) es un objeto propio con autor, fecha y mensaje. `git cat-file -t v1.0.0` responde `tag` si es anotada y `commit` si es ligera.

| Comando | Qué sube |
|---|---|
| `git push` | Commits, pero **ninguna etiqueta** |
| `git push origin v1.0.0` | Solo esa etiqueta |
| `git push --tags` | Todas las etiquetas locales, también las ligeras (solo etiquetas: no actualiza ninguna rama) |
| `git push --follow-tags` | Los commits y las etiquetas **anotadas** que apuntan a ellos (la que usa la web) |

**Versionado semántico** (SemVer): el número tiene la forma `MAYOR.MENOR.PARCHE`.

| Sube... | Cuando hay... | De `1.4.2` pasa a |
|---|---|---|
| MAYOR | Cambios incompatibles con lo anterior | `2.0.0` |
| MENOR | Funcionalidad nueva compatible | `1.5.0` |
| PARCHE | Solo arreglos de fallos | `1.4.3` |

Al subir una parte, las de su derecha vuelven a 0. `0.x.y` significa "en desarrollo" y `1.0.0` es la primera versión estable. La web etiqueta sin `v` (`0.1.0`); en mi práctica usé `v0.1.0` y `v1.0.0`. La `v` es solo un prefijo habitual: `v1.0.0` y `1.0.0` son la misma versión. Una **release** de GitHub es la publicación de una etiqueta, con notas y ficheros descargables.

#### 4.2.13 El fichero .gitignore

`.gitignore` es un fichero de texto en la raíz del repo con patrones de lo que **no** se versiona: secretos (`.env`, claves), ficheros generados (`site/`, `_site/`), entornos de Python (`.venv/`, `__pycache__/`), logs y basura del sistema (`.DS_Store`). Así no se cuelan por error con un `git add .`. El `.gitignore` sí se versiona, para que todo el equipo ignore lo mismo.

| Patrón | Qué ignora |
|---|---|
| `*.log` | Todos los `.log`, en cualquier carpeta |
| `site/` | Cualquier carpeta llamada `site`, esté donde esté |
| `/site/` | Solo la carpeta `site` de la raíz (la barra inicial ancla a la raíz) |
| `**/output/*.obj` | Todos los `.obj` de cualquier carpeta `output`, a cualquier profundidad (`**` vale por "cualquier número de carpetas") |
| `!logs/importante.log` | Vuelve a incluir ese fichero (la `!` niega un patrón anterior) |

- Solo afecta a ficheros **sin seguimiento**. Si ya estaba versionado: `git rm --cached fichero` y commit.
- La `!` no funciona si la carpeta que lo contiene está ignorada entera (`cache/`): Git ni entra en ella. Y Git no versiona carpetas vacías (truco: un fichero `.gitkeep` dentro).
- `git status --ignored` enseña los ignorados, `git check-ignore -v .env` dice qué línea lo ignora y `git add .env` se niega y te pide `-f`.
- La web propone partir de un `.gitignore` generado con Toptal según tus tecnologías (por ejemplo `curl -o .gitignore https://www.toptal.com/developers/gitignore/api/python,visualstudiocode,virtualenv,pycharm`) y revisarlo antes del primer commit.

#### 4.2.14 Seguridad y accesibilidad del código (RA6-f)

**Accesible**: disponible para quien lo necesita (el remoto es tu copia de seguridad y puede haber varios). **Seguro**: no se filtra nada y no entra quien no debe.

- **Visibilidad**: repo **privado** (solo tú y quien invites) o **público** (lo lee cualquiera, pero solo escriben los colaboradores). En una organización (una cuenta de GitHub compartida por un grupo) como `monium`, la de gitanddocs, cada persona tiene un rol, desde solo lectura (Read) hasta administración (Admin), pasando por escritura (Write).
- **Protección de ramas**: reglas como "a `main` solo se entra por pull request" (PR: petición para fusionar una rama, que otros revisan antes). En gitanddocs, `main` pide 3 aprobaciones.

Para hablar con GitHub hay dos vías: **SSH** (Secure Shell, conexión cifrada que se autentica con un par de claves) y **HTTPS** (la conexión cifrada de la web).

| Vía | URL del remoto | Credencial | Detalle |
|---|---|---|---|
| SSH (la recomendada en el módulo) | `git@github.com:usuario/repo.git` | Par de claves: la **privada** se queda en tu equipo y la **pública** se pega en GitHub | No viaja ninguna contraseña por la red |
| HTTPS | `https://github.com/usuario/repo.git` | **Token personal (PAT)**: una clave larga que genera GitHub y se escribe donde iría la contraseña, que GitHub ya no acepta | Scopes (permisos) mínimos según la web: `repo`, `workflow` y `read:org`. El token solo se ve una vez, al crearlo |

```bash
ssh-keygen -t ed25519 -C "alumno@dpl.local"   # crea el par de claves (ed25519 es el tipo)
cat ~/.ssh/id_ed25519.pub                     # la .pub es la que se pega en GitHub
ssh -T git@github.com                         # comprueba que GitHub te reconoce
```

La **clave de cuenta** (Settings > SSH and GPG keys) vale para todos tus repos. La **deploy key** (Settings > Deploy keys del repo) vale solo para ese repo y es de solo lectura salvo que marques *Allow write access*.

**Nunca van al repo**: contraseñas, claves privadas, tokens ni `.env`. En la documentación, valores de ejemplo (`alumno` / `CAMBIAR_ESTO`). Antes de cada commit, `git status` y `git diff --staged`, y nada de `git add .` a ciegas. Antes de entregar, la web propone `grep -RniE "password|passwd|secret|PRIVATE KEY" .` **Si se te sube un secreto**, por este orden:

1. **Cámbialo ya** (rota la credencial). Una vez publicado, hay que darlo por comprometido.
2. Sácalo del repo: `git rm --cached .env`, añádelo a `.gitignore` y haz commit.
3. Recuerda que **sigue en los commits antiguos** (lo ves con `git log --all -- .env`). Borrarlo de la historia exige reescribirla (por ejemplo con `git filter-repo`) y coordinarse con el equipo. Por eso el paso 1 va primero.

### 4.3 Manos a la obra

Laboratorio de usar y tirar en `/tmp/ensayo-git`. `/tmp` es la carpeta de temporales del sistema: nada de lo que hagas aquí toca tus repos de verdad. Escribe tú los comandos y, antes de pulsar Enter, di qué esperas ver. Los comentarios (`#`) dicen lo que sale; tus hashes serán otros. Mi Git está en español; si el tuyo sale en inglés, cambia el idioma pero no el sentido.

**Paso 1. Repositorio e identidad solo para este repo**

```bash
mkdir /tmp/ensayo-git
cd /tmp/ensayo-git
git init -b main     # -b main: la rama inicial se llama main pase lo que pase
git config --local user.name "Diego Alejandro Gil González"
git config --local user.email "diegogildam@gmail.com"
git config --local --get-regexp user     # sale user.name Diego... y user.email diegogildam@...
```

**Paso 2. De untracked a staged y a committed**

```bash
printf "# Ensayo de Git\n\nColor: azul\n" > README.md   # crea el fichero; \n es un salto de línea
git status -s          # ?? README.md   (sin seguimiento)
git add README.md
git status -s          # A  README.md   (preparado)
git commit -m "Añade el README del ensayo" -m "Creo README.md con un título y la línea Color: azul. La usaré más adelante para provocar un conflicto a propósito."
git log --oneline      # 561f839 Añade el README del ensayo
```

El commit responde `[main (commit-raíz) 561f839]`: `commit-raíz` es el primer commit, el que no tiene padre. Prueba también `git status` (largo) antes y después del `add`, y `git log` a secas, que enseña el cuerpo.

**Paso 3. Modificar, revisar y deshacer**

```bash
echo "Uso: practicar Git sin miedo a romper nada." >> README.md   # >> añade una línea al final
git status -s          #  M README.md   (el espacio delante: aún no está en el staging)
git diff               # enseña el cambio (abajo, sin sus 4 líneas de cabecera)
git add README.md
git diff               # ya no sale nada
git diff --staged      # el mismo cambio: es lo que va a entrar en el commit
git commit -m "Explica para qué sirve el ensayo" -m "Añado al README una línea de uso. Antes de confirmar reviso el cambio con git diff --staged."
```

```text
@@ -1,3 +1,4 @@
 # Ensayo de Git
 
 Color: azul
+Uso: practicar Git sin miedo a romper nada.
```

`@@ -1,3 +1,4 @@` dice que el trozo empieza en la línea 1 y pasa de 3 líneas a 4; la línea con `+` es la añadida (una con `-` sería una quitada). Ahora deshaz un cambio:

```bash
echo "Borrador que no quiero" >> README.md
git add README.md
git restore --staged README.md   # sale del staging: git status -s enseña " M README.md"
git restore README.md            # cambio tirado: git status -s ya no enseña nada
```

**Paso 4. Ignorar un fichero con .gitignore**

```bash
echo "CLAVE_BD=CAMBIAR_ESTO" > .env      # > crea el fichero (o lo machaca si existe)
echo ".env" > .gitignore
git status -s          # solo sale ?? .gitignore: .env ha desaparecido
git status --ignored   # .env sale en "Archivos ignorados"
git add .env           # Git se niega: "Las siguientes rutas son ignoradas..." y sugiere -f
git add .gitignore
git commit -m "Ignora el fichero .env" -m "Creo .gitignore con la línea .env para que el fichero de claves no entre nunca en el repositorio. Lo compruebo con git status --ignored."
```

**Paso 5. Rama nueva y fusión con --no-ff**

```bash
git switch -c docs     # Cambiado a nueva rama 'docs'
printf "# Instalación\n\nComprueba Git con git --version.\n" > INSTALACION.md
git add INSTALACION.md
git commit -m "Añade la guía de instalación" -m "Creo INSTALACION.md en la rama docs con el comando que comprueba la versión de Git."
git switch main
ls                     # solo README.md: INSTALACION.md vive en docs
git merge --no-ff docs -m "Fusiona la rama docs en main"    # Merge made by the 'ort' strategy.
git branch -d docs     # Eliminada la rama docs (era 3f2ea62).
```

Como `main` no había avanzado, sin `--no-ff` habría sido un fast-forward sin "burbuja". El grafo lo ves en el paso 7.

**Paso 6. Provoca un conflicto y resuélvelo**

`sed` cambia un texto por otro dentro de un fichero; en macOS, `-i ''` significa "modifica el fichero sin guardar copia". Si lo prefieres, cambia la palabra a mano con el editor.

```bash
git switch -c color
sed -i '' 's/azul/verde/' README.md
git commit -am "Cambia el color a verde" -m "Propongo el verde en la rama color."
git switch main
sed -i '' 's/azul/naranja/' README.md
git commit -am "Cambia el color a naranja" -m "En main elijo el naranja, en la misma línea que la rama color."
git merge color        # CONFLICTO (contenido): Conflicto de fusión en README.md
git status -s          # UU README.md
cat README.md          # las marcas de 4.2.9, entre el título y la línea de uso
```

Abre `README.md` con tu editor (VS Code o `nano README.md`), quédate con `Color: verde` y borra las tres líneas de marcas. Después:

```bash
git diff --check       # no debe imprimir nada; si quedan marcas, avisa con leftover conflict marker
git add README.md
git status             # Todos los conflictos resueltos pero sigues fusionando.
git commit -m "Resuelve el conflicto del color" -m "main tenía naranja y la rama color traía verde en la misma línea. Me quedo con verde y borro las marcas de conflicto."
git branch -d color
```

**Paso 7. Etiqueta anotada y resultado final**

```bash
git tag -a v1.0.0 -m "Primera versión del ensayo de Git"
git cat-file -t v1.0.0          # tag: es anotada
git log --oneline --graph --all
git log --format='%an <%ae>' | sort -u
```

```text
*   71d9fa2 (HEAD -> main, tag: v1.0.0) Resuelve el conflicto del color
|\
| * c0f025d Cambia el color a verde
* | 4599e95 Cambia el color a naranja
|/
*   05b7734 Fusiona la rama docs en main
|\
| * 3f2ea62 Añade la guía de instalación
|/
* 714ce67 Ignora el fichero .env
* 706cc15 Explica para qué sirve el ensayo
* 561f839 Añade el README del ensayo
Diego Alejandro Gil González <diegogildam@gmail.com>
```

Léelo de abajo arriba: tres commits en línea, la burbuja de `docs` (por el `--no-ff`) y la del conflicto, donde `main` y `color` avanzaron a la vez. `(HEAD -> main, tag: v1.0.0)` dice que estás en `main` y que ese commit lleva la etiqueta. La última línea: una sola identidad, la buena.

**Paso 8 (extra, si te sobra tiempo). Un remoto de mentira en tu disco, para practicar `push` sin Internet**

```bash
git init --bare /tmp/ensayo-remoto.git     # bare (desnudo): repo sin directorio de trabajo, solo la historia
git remote add origin /tmp/ensayo-remoto.git
git push                       # fatal: La rama actual main no tiene una rama upstream.
git push -u origin main        # * [new branch] main -> main y rama 'main' configurada para rastrear 'origin/main'.
git ls-remote --tags origin    # no imprime nada: el push de main no subió la etiqueta
git push --tags                # * [new tag] v1.0.0 -> v1.0.0
git branch -vv                 # * main 71d9fa2 [origin/main] Resuelve el conflicto del color
```

**Limpieza.** `rm -rf` borra una carpeta y todo lo que contiene, sin preguntar y sin pasar por la papelera. Por eso primero sales de ella, miras que es la buena y escribes la ruta completa:

```bash
cd ~
ls /tmp/ensayo-git                # comprueba que es la carpeta del ensayo
rm -rf /tmp/ensayo-git /tmp/ensayo-remoto.git
```

### 4.4 Comprueba que lo sabes

**Reconocer (tipo test, una sola respuesta correcta).** Contesta las cinco y después abre las respuestas.

**P1.** Acabas de hacer `git add README.md` y ejecutas `git diff`. No sale nada. ¿Por qué?

- a) Porque `git add` ya ha guardado el cambio en un commit.
- b) Porque `git diff` compara el directorio de trabajo con el staging, y ahora son iguales.
- c) Porque `README.md` está en `.gitignore`.
- d) Porque `git diff` solo funciona después de un `git push`.

**P2.** ¿Cuál de estas líneas de `git status -s` es un fichero con un conflicto sin resolver?

- a) `?? notas.txt`
- b) ` M index.html`
- c) `A  estilos.css`
- d) `UU README.md`

**P3.** Tienes en local la etiqueta ligera `prueba` y la anotada `v1.0.0`, sin subir. ¿Qué comando sube **las dos**?

- a) `git push`
- b) `git push --follow-tags`
- c) `git push --tags`
- d) `git push origin main`

**P4.** Un servidor de despliegue solo tiene que **descargar** un repositorio privado concreto, sin poder subir nada. ¿Qué es lo más adecuado?

- a) Copiar en el servidor tu clave privada SSH de cuenta.
- b) Una deploy key en ese repo, sin marcar *Allow write access*.
- c) Un token personal con el scope `repo`, apuntado en el README.
- d) Hacer público el repositorio.

**P5.** Has creado `notas.txt` (nunca lo has añadido) y has editado `README.md` (ya versionado). Ejecutas `git commit -am "Actualiza el README"`. ¿Qué entra en el commit?

- a) Los dos ficheros.
- b) Solo `README.md`.
- c) Solo `notas.txt`.
- d) Nada, porque `-a` necesita un `git add` previo.

<details>
<summary>Respuesta</summary>

- **P1: b)** `git diff` enseña lo que aún no has preparado. Tras el `add`, el cambio está en el staging y se mira con `git diff --staged`. La a) es la trampa: `add` prepara, no confirma.
- **P2: d)** `UU` significa "modificado por ambos" en una fusión. `??` es sin seguimiento, ` M` es modificado sin preparar y `A ` es nuevo y ya preparado.
- **P3: c)** `--tags` sube todas las etiquetas locales. `--follow-tags` solo sube las anotadas (se dejaría `prueba`), y un `git push` normal no sube ninguna.
- **P4: b)** La deploy key vale solo para un repo y, sin *Allow write access*, solo lee. La a) daría acceso a todos tus repos, la c) filtra el token y la d) expone el código a todo el mundo.
- **P5: b)** `-a` prepara solo lo que ya estaba versionado. `notas.txt` sigue como `??` después del commit.

</details>

**Respuesta corta o escribir un comando**

**P6.** Escribe un solo comando que cree un commit con el subject `Configura el server block del blog` y un cuerpo que diga cómo lo comprobaste. Después, el comando que enseña solo los 3 últimos commits, uno por línea.

<details>
<summary>Respuesta</summary>

```bash
git commit -m "Configura el server block del blog" \
           -m "Creo nginx/conf.d/blog.conf con server_name blog.local. Lo compruebo con nginx -t y con curl -I -H 'Host: blog.local' http://localhost:8080/, que responde 200."
git log --oneline -3        # -3 limita a los tres últimos
```

</details>

**P7.** Acabas de hacer un commit con el mensaje `arreglos` y **todavía no** has hecho push. a) Escribe el comando que cambia ese mensaje por uno que cumpla la convención. b) ¿Qué harías si ya lo hubieras subido y un compañero lo tuviera?

<details>
<summary>Respuesta</summary>

a) `git commit --amend -m "Corrige la redirección que perdía el puerto 8080" -m "Añado el puerto a la cabecera Location y lo compruebo con curl -I."`

b) No usaría `--amend`: crea un commit con otro hash, el `push` sería rechazado y forzarlo rompería la historia del compañero. Dejo el commit como está y cuido los siguientes. Si lo que estaba mal era el contenido, lo deshago con `git revert <hash>`.

</details>

**P8.** Escribe un `.gitignore` que ignore el fichero `.env`, todos los `.log` salvo `logs/importante.log`, y la carpeta `site/` **solo** de la raíz.

<details>
<summary>Respuesta</summary>

```text
.env
*.log
!logs/importante.log
/site/
```

La `!` funciona porque la carpeta `logs/` no está ignorada (solo sus `.log`). Con `/site/`, una carpeta `docs/site/` seguiría versionándose.

</details>

**P9.** Clonaste el repo de clase `git@github.com:monium/gitanddocs.git`, así que `origin` apunta a él. Ahora tienes tu fork en `git@github.com:diegoalegil/gitanddocs.git`. Escribe los comandos para que `origin` sea tu fork, el de clase se llame `upstream`, y comprobarlo. Añade cómo subirías por primera vez la rama `issue-41` a tu fork.

<details>
<summary>Respuesta</summary>

```bash
git remote set-url origin git@github.com:diegoalegil/gitanddocs.git
git remote add upstream git@github.com:monium/gitanddocs.git
git remote -v
git push -u origin issue-41
```

`set-url` cambia la URL sin borrar el remoto. `git remote -v` debe enseñar `origin` con tu fork y `upstream` con el de clase (cada uno con su línea de fetch y de push). `-u` fija el upstream de la rama, así que los siguientes `git push` ya no necesitan nada más.

</details>

**Razonar o interpretar**

**P10.** Lees esto:

```text
$ git status
En la rama main
Tu rama está actualizada con 'origin/main'.
```

Un compañero jura que subió un commit a `main` hace cinco minutos. ¿Miente alguno de los dos? ¿Qué haces para salir de dudas?

<details>
<summary>Respuesta</summary>

No miente nadie. `git status` compara con la foto `origin/main` que tienes en local, y esa foto no se actualiza hasta que tu Git habla con el remoto. Ejecuto `git fetch origin` y entonces `git status` dice `Tu rama está detrás de 'origin/main' por 1 commit, y puede ser avanzada rápido.` Con `git log --oneline main..origin/main` veo qué ha llegado y con `git pull` lo traigo a mi rama.

</details>

**P11.** Interpreta esta salida:

```text
$ git merge rama-ff
Actualizando cc13d72..18e555f
Fast-forward
 b.txt | 1 +
```

Estás en `main`. a) ¿Se ha creado un commit de fusión? b) ¿Qué sabes de `main` mientras existía `rama-ff`? c) ¿Qué habría que haber escrito para cumplir lo que pide el curso, y qué cambiaría en el grafo?

<details>
<summary>Respuesta</summary>

- a) No. `Fast-forward` y `Actualizando cc13d72..18e555f` dicen que `main` solo ha movido su puntero de un commit a otro.
- b) Que `main` no avanzó desde que nació la rama; si no, el fast-forward sería imposible.
- c) `git merge --no-ff rama-ff -m "Fusiona rama-ff en main"`. Se crearía un commit de fusión con dos padres y en `git log --oneline --graph` se vería la burbuja de la rama.

</details>

**P12.** Antes de entregar ejecutas esto:

```text
$ git log --format='%an <%ae>' | sort -u
Diego Alejandro Gil González <diegogildam@gmail.com>
Diego Gil González <diego@MacBook-Pro-de-Diego.local>
```

¿Qué ha pasado, qué consecuencia tiene y cómo lo habrías evitado?

<details>
<summary>Respuesta</summary>

Algunos commits se hicieron sin identidad configurada y Git se inventó una con el usuario del Mac y el nombre del equipo. Esa segunda identidad no es la del aula virtual, y la web avisa de que una entrega así puntúa cero. Se evita configurando `git config --local user.name` y `user.email` **antes del primer commit** y repasando este comando antes de entregar. Si solo fuera el último commit y no estuviera subido, bastaría `git commit --amend --reset-author`; si son varios, arreglarlo obliga a reescribir la historia.

</details>

**P13.** Hace dos horas subiste a un repo público `config.php` con la contraseña real de la base de datos. Un compañero te dice: "Bórrala del fichero, haz commit y push, y listo". ¿Por qué no basta? Ordena lo que tienes que hacer.

<details>
<summary>Respuesta</summary>

No basta porque la contraseña sigue en el commit anterior: cualquiera puede verla en el historial de GitHub o con `git show <hash>`. Orden:

1. Cambiar la contraseña de la base de datos ya: está comprometida.
2. Quitarla del fichero (valor de ejemplo o variable de entorno), o sacar el fichero con `git rm --cached config.php`, añadirlo a `.gitignore` y hacer commit.
3. Si hay que borrarla de la historia, reescribirla (por ejemplo con `git filter-repo`) avisando al equipo. Aun así, la contraseña vieja se da por perdida.

</details>

**P14.** Con prisa, en mitad de un conflicto haces `git add README.md` y `git commit -m "Resuelve el conflicto"` sin abrir el fichero. Git no se queja. Después, `cat README.md` enseña `<<<<<<< HEAD`. ¿Qué ha pasado y cómo lo arreglas?

<details>
<summary>Respuesta</summary>

Git no revisa si quedan marcas: `git add` solo marca el fichero como resuelto y el commit guarda lo que haya, marcas incluidas. Para arreglarlo, edito el fichero, dejo el contenido final, borro las marcas y hago `git add` y un commit nuevo (por ejemplo `Quita las marcas de conflicto del README`); si no lo había subido, también valdría `git commit --amend`. Para que no vuelva a pasar, antes del commit ejecuto `git diff --check`, que avisa con `leftover conflict marker`.

</details>

### 4.5 Si te atascas

- Qué es Git, zonas, estados, convención e identidad: [05, apartado 2.1](05-ut1-git-documentacion-cicd.md) a [05, apartado 2.5](05-ut1-git-documentacion-cicd.md) y cómo lo hice en mi práctica en [04, apartado 4](04-practica-nginx.md). En la web: https://dpl-f1facc.gitlab.io/ut01/teoria/git/ y la práctica guiada 01: https://dpl-f1facc.gitlab.io/ut01/practicas/guiada-01-git/
- Historial, deshacer, ramas, fusiones, conflictos y rebase: [05, apartado 2.6](05-ut1-git-documentacion-cicd.md) a [05, apartado 2.11](05-ut1-git-documentacion-cicd.md) y las estrategias de ramas en [05, apartado 3](05-ut1-git-documentacion-cicd.md). En la web, la práctica guiada 24: https://dpl-f1facc.gitlab.io/ut01/practicas/guiada-24-git-branching/
- Remotos, fork y etiquetas: [05, apartado 2.12](05-ut1-git-documentacion-cicd.md), [05, apartado 2.13](05-ut1-git-documentacion-cicd.md) y [05, apartado 4](05-ut1-git-documentacion-cicd.md). En la web, la práctica guiada 02: https://dpl-f1facc.gitlab.io/ut01/practicas/guiada-02-colaboracion-git/
- `.gitignore` y seguridad: [05, apartado 2.14](05-ut1-git-documentacion-cicd.md) y [05, apartado 5](05-ut1-git-documentacion-cicd.md). Errores típicos: [05, apartado 12](05-ut1-git-documentacion-cicd.md). Chuleta: https://dpl-f1facc.gitlab.io/recursos/comandos/ y [05, apartado 11](05-ut1-git-documentacion-cicd.md). Más preguntas: [07, apartado 4.1](07-plan-de-repaso-p1.md), [07, apartado 4.2](07-plan-de-repaso-p1.md) y [07, apartado 4.3](07-plan-de-repaso-p1.md). Palabras que no recuerdes: https://dpl-f1facc.gitlab.io/recursos/glosario/

## 5. Martes 3/11: trabajo en equipo, documentación y CI/CD

Hoy cierras la UT1. Al acabar sabrás contar el viaje de una tarea en GitHub (de la issue al merge), qué README pide el profesor, cómo sale una web de documentación de unos ficheros Markdown y cómo se lee un workflow de GitHub Actions, empezando por el de mi práctica. Es la mitad del RA6 y lo usamos cada semana en gitanddocs. Cubre los CE RA6-a, RA6-b, RA6-c, RA6-d y RA6-h (mapa completo en [07, apartado 2](07-plan-de-repaso-p1.md)).

### 5.1 Plan del día

| Bloque | Qué haces | Tiempo |
|---|---|---|
| 0. Registro de fallos | Contesta las filas sin marcar del registro (apartado 11): las del lunes y las que sigan pendientes | 10 min |
| 1. Leer | "Lo imprescindible" (5.2), con un papel al lado: cada término nuevo, apúntalo con tus palabras | 45 min |
| 2. Practicar | "Manos a la obra" (5.3): mi `ci.yml`, la pestaña Actions, `zensical build` y dos ejercicios de memoria en papel | 35 min |
| 3. Comprobar | "Comprueba que lo sabes" (5.4): las 15 preguntas sin mirar y después corriges | 30 min |
| 4. Fallos | Apunta cada fallo en el registro (apartado 11) y vuelve a leer su punto de 5.2 | 15 min |
| Descansos | 5 min de pie, sin pantallas, después de los bloques 1, 2 y 3 | 15 min |
| Total | | 2 h 30 min |

### 5.2 Lo imprescindible

#### 5.2.1 Palabras base

Repaso rápido: un **repositorio** es la carpeta del proyecto con todo su historial; un **remoto**, su copia en un servidor como GitHub; un **commit**, una foto guardada de los cambios con autor, fecha y mensaje; una **rama**, una línea de trabajo paralela (`main` es la principal); **push**, subir tus commits al remoto; y **merge** (fusión), unir los cambios de una rama en otra. Y tres nuevas:

- **Issue**: una ficha de trabajo con número (`#41`): un fallo, una tarea o una mejora. No lleva código.
- **Pull request (PR)**: la petición de unir una rama a otra, que otras personas revisan antes. En GitLab se llama *merge request*. No es un comando de Git: es una herramienta de la plataforma (GitHub, GitLab).
- **Wiki**: páginas de documentación viva dentro del propio proyecto en GitHub o GitLab (un glosario, el manual de un servicio). Con las issues y los PR, es una de las herramientas colaborativas que nombra la web.

#### 5.2.2 Fork y clone, origin y upstream

Analogía: el repositorio original es un libro de la biblioteca. Hacer **fork** es fotocopiarlo y guardar la fotocopia en tu estantería de GitHub. Hacer **clone** es llevarte una copia a casa (tu ordenador) para trabajar con ella.

- **Fork**: la copia queda en GitHub, en tu cuenta. Se hace con el botón **Fork** (o `gh repo fork usuario/repo --clone`, que además clona). Se usa cuando no tienes permiso de escritura en el original.
- **Clone**: la copia queda en tu ordenador, con `git clone URL`. Se usa siempre que quieras trabajar en local.
- **origin**: el nombre que Git pone automáticamente al remoto del que clonaste. Si clonas tu fork, `origin` es tu fork.
- **upstream**: el nombre que se da, por costumbre, al repositorio original. Lo añades tú (`git remote add upstream URL`) y es de solo lectura: sirve para traer novedades antes de empezar cada tarea (`git fetch upstream`, `git switch main`, `git merge upstream/main` y `git push origin main`). A `upstream` no se hace push: lo tuyo le llega por PR.
- En gitanddocs tengo permiso de escritura, así que clono `monium/gitanddocs` directamente y `git remote -v` solo me enseña `origin`. Otros compañeros usan fork: el PR #31 llegó desde `slayaglez/28_move_documentation`.

#### 5.2.3 El ciclo de una tarea

Issue → rama → commits → push → pull request (con `Closes #N`) → revisión → merge → borrar la rama. Y la web se publica sola.

| Paso | Qué haces | Dónde o cómo |
|---|---|---|
| 1. Issue | Antes, busca que nadie tenga ya una issue, rama o PR de lo mismo (el PR #34 duplicó trabajo del profe). Crea la issue con su plantilla | **Issues > New issue** |
| 2. Rama | Una rama por tarea. Nunca se trabaja directamente en `main` | En la issue, **Development > Create a branch** (`issue-41`), o `git switch -c issue-41` |
| 3. Commits | Pequeños, con subject y cuerpo | `git commit -m "subject" -m "cuerpo"` |
| 4. Push | Subir la rama. `-u` la deja vinculada con la del remoto: Git responde `rama 'issue-41' configurada para rastrear 'origin/issue-41'.` | `git push -u origin issue-41` |
| 5. PR | Proponer la rama para `main`, con la plantilla rellena | **Compare & pull request** |
| 6. Revisión | Los compañeros comentan, aprueban o piden cambios. Cada push nuevo a la misma rama actualiza el PR solo | Pestaña **Files changed** |
| 7. Merge | Cuando hay las aprobaciones que exige `main` | **Merge pull request** |
| 8. Borrar la rama | Norma del profe: que no queden ramas sueltas | **Delete branch** en el PR |

#### 5.2.4 base ← compare: el error del PR #39

Al crear un PR, GitHub enseña una línea con dos ramas y una flecha: `base: main ← compare: issue-41`.

- **base**: la rama **destino**, la que recibe los cambios.
- **compare**: la rama **origen**, la que trae tus cambios.
- La flecha apunta adonde van. Como en un sobre: base es el destinatario y compare el remitente. En la URL va primero base y luego compare: `github.com/monium/gitanddocs/compare/main...issue-41`.

El PR #39 se abrió con `base: jorgeMRama ← compare: main`. Se aprobó y se fusionó, pero lo que pasó fue que `main` entró en la rama de Jorge, y la guía de NGINX nunca llegó a `main`. Regla: antes de pulsar **Create pull request**, lee esa línea. Tiene que poner `base: main ← compare: mi-rama`.

#### 5.2.5 Closes #N: el fallo del PR #29

Si la descripción del PR lleva `Closes #41`, al fusionar el PR en la **rama por defecto** (`main`) GitHub cierra sola la issue 41 y su tarjeta pasa a Terminado. También vale en el mensaje de un commit (o del merge), cuando ese commit llega a `main`.

- Palabras válidas: `close`, `closes`, `closed`, `fix`, `fixes`, `fixed`, `resolve`, `resolves` y `resolved` (da igual mayúsculas o minúsculas).
- Palabra y número **juntos, en la misma línea**: `Closes #19`. En el PR #29 la plantilla dejaba `- Closes #` y el número quedó en la línea de abajo, así que la #19 no se cerró. `Relacionado con #19` solo enlaza la issue: no la cierra. Y si el PR va a una rama que no es `main` (como el #39), la palabra no cierra nada.

#### 5.2.6 La revisión

**Revisar** es leer el PR de otra persona (pestaña **Files changed**), probarlo si hace falta y dar tu opinión. Al pulsar **Review changes** eliges una de tres:

| Opción | Qué significa | Efecto |
|---|---|---|
| Comment | Un comentario general, sin aprobar ni bloquear | Ninguno sobre el merge |
| Approve | "Está bien, se puede fusionar". En clase se suele escribir **LGTM** (*looks good to me*, "a mí me parece bien") | Suma una aprobación |
| Request changes | "Así no: cambia esto antes" | Con `main` protegida, bloquea el merge hasta que esa persona apruebe o se descarte su revisión |

También puedes comentar una línea concreta. Desde un comentario se crea una issue nueva con **Reference in new issue** (así nació la #30, en la revisión del #29). El autor **no puede aprobar su propio PR**. Solo cuentan las aprobaciones de quien tiene permiso de escritura en el repo, aunque no estuviera en tu lista de revisores. Y si el PR tiene conflictos, los resuelve quien lo hizo antes de que se apruebe.

#### 5.2.7 Proteger main

Una **regla de protección de rama** impide cambiar `main` sin control. Se crea en **Settings > Branches** o con un *ruleset* (un conjunto de reglas, la forma nueva) en **Settings > Rules > Rulesets**. Las opciones clave:

- **Require a pull request before merging**: nadie hace push directo a `main`; todo entra por PR.
- **Require approvals**: el número mínimo de aprobaciones. Hasta tenerlas, el botón de merge está bloqueado.
- **Require status checks to pass**: además, que las comprobaciones automáticas de la CI (integración continua, la ves más abajo), llamadas *status checks*, estén en verde.
- **Dismiss stale pull request approvals when new commits are pushed**: si subes commits nuevos, las aprobaciones anteriores se anulan.

gitanddocs tiene un ruleset sobre `main`: PR obligatorio con **3 aprobaciones**, prohibido borrar `main` y prohibido el push forzado. No exige status checks ni anula aprobaciones. Por qué importa: el PR #11 se fusionó sin que nadie lo aprobara y metió el fallo de `config.yml` que reporté en la issue #41.

#### 5.2.8 Organizar el trabajo: tablero, labels, sub-issues y plantillas

- **Kanban**: un tablero con columnas que son estados; cada tarea es una tarjeta que avanza de izquierda a derecha. En GitHub se hace con **GitHub Projects**. Nuestro Project **DPL** tiene las columnas Sin asignar, Asignadas, En progreso, En revisión y Terminado, y las tarjetas se mueven solas (a Terminado al cerrarse la issue).
- **Label** (etiqueta): una marca de color para clasificar issues y PR (`bug`, `documentation`, `enhancement`...). Una plantilla puede ponerla sola, pero solo si la label existe en el repo: la #27 y la #35 se crearon con la plantilla "Tarea General", que pide `task`, y se quedaron sin label porque `task` no existe (tampoco `security`).
- **Sub-issues**: una tarea grande se parte en issues hijas dentro de una issue madre (la #16 tiene como hijas la #17 y la #19). La madre se da por resuelta cuando están resueltas todas sus hijas.
- **Plantillas**: texto ya preparado que GitHub pone en el formulario para que todos rellenen lo mismo. Viven en el repo, así que se versionan y se cambian con PR. Su configuración va en **YAML**, un formato con `clave: valor` en el que la sangría (los espacios del principio) marca qué va dentro de qué.

| Fichero | Para qué |
|---|---|
| `.github/ISSUE_TEMPLATE/*.md` | Una plantilla por tipo de issue. Es Markdown con una cabecera YAML entre dos líneas `---` (`name`, `about`, `labels`, `assignees`) |
| `.github/ISSUE_TEMPLATE/config.yml` | Configura el menú de **New issue**: `blank_issues_enabled` (si se permiten issues en blanco) y `contact_links` (enlaces de ayuda). El de gitanddocs no es YAML válido (lleva dentro el `cat > ... << 'EOF'` con el que se creó) y GitHub lo ignora: es mi issue #41 |
| `.github/pull_request_template.md` | El texto con el que empieza cada PR. En gitanddocs: descripción, `- Closes #`, tipo de cambio, cómo se ha probado y checklist |

#### 5.2.9 No subir lo generado

Lo que sale de un *build* (la generación de la web: `site/` de Zensical y MkDocs, `_site/` de Jekyll) **no se sube al repo**:

1. Se vuelve a crear en segundos a partir de las fuentes (`docs/` y la configuración): guardarlo es duplicar.
2. Son muchos ficheros que cambian a la vez (en gitanddocs, `site/` tiene 17): el PR se llena de cambios imposibles de revisar y salen conflictos.
3. Se queda desfasado en cuanto alguien cambia un `.md` y no vuelve a generar. Y ya lo genera la CI: en gitanddocs, el workflow crea `site/` y lo publica.

Se evita con `.gitignore` (gitanddocs tiene `/site`; mi práctica, `site/` y `_site/`). Los PR #36 y #37, un blog con Jekyll, se cerraron sin merge por subir `_site/`.

#### 5.2.10 Flujos de ramas

| Flujo | Ramas | Idea | Encaja cuando |
|---|---|---|---|
| Trunk-based | Solo `main` (y ramas de horas) | Todos integran en `main` a diario. Lo que está a medias se apaga con un *feature flag* (un interruptor en la configuración) | Hay una CI muy fiable y despliegue continuo |
| Feature branches / GitHub Flow | `main` + ramas cortas | Cada tarea en su rama, que entra por PR revisado. GitHub Flow es esto con despliegue frecuente desde `main` | Revisión por PR y despliegues frecuentes (gitanddocs) |
| Git Flow | `main`, `develop`, `feature/*`, `release/*`, `hotfix/*` | `main` solo guarda versiones publicadas; las funcionalidades se juntan en `develop` | Versiones con fecha y varias versiones mantenidas a la vez |

En Git Flow, de dónde nace cada rama y adónde vuelve es pregunta fija:

| Rama | Nace de | Vuelve a | Para qué |
|---|---|---|---|
| `feature/*` | `develop` | `develop` | Una funcionalidad |
| `release/*` | `develop` | `main` y `develop` | Preparar una versión (ajustes finales y número de versión) |
| `hotfix/*` | `main` | `main` y `develop` | Arreglar un fallo urgente de producción sin esperar a la siguiente versión |

Su ventaja es el orden en proyectos con publicaciones planificadas; su inconveniente, que pesa demasiado para un equipo que despliega a diario.

Un PR se fusiona de tres formas: **merge commit** (añade un commit de fusión y se ve la rama), **squash** (aplasta todos los commits del PR en uno) y **rebase** (reaplica los commits sobre `main`, sin commit de fusión). En las prácticas: feature branches y merge commit (en local, `git merge --no-ff`, que obliga a crear el commit de fusión), para que se vea que hubo rama.

#### 5.2.11 Por qué documentar y el README que pide el profesor

Analogía: un servidor sin documentar es una casa sin planos. Cuando quien la hizo se va, nadie sabe por dónde van los cables. Lo mínimo de cualquier despliegue es la **instalación** (qué se instala y con qué comandos), la **configuración** (qué ficheros se tocan), la **comprobación** (cómo se demuestra que funciona) y los **problemas y su solución**. Se documenta **mientras** despliegas, y la documentación se versiona con Git junto al código: tiene autor y fecha, se revisa en PR y cuadra con la versión que describe.

**README.md** es la primera página del repositorio, la que GitHub enseña al abrirlo. Orden (lo escribirás de memoria en 5.3):

1. `# Nombre del proyecto` (el **único** `#` del fichero) y una o dos líneas de qué es.
2. `## Índice`, con enlaces internos a cada apartado.
3. `## Instalación`, `## Configuración`, `## Comprobación` y `## Problemas encontrados y solución`.
4. `## Repositorio remoto`, con la URL de GitHub, GitLab o Gitea.
5. Los RA y CE que trabaja (en mi práctica, `## Relación curricular`).

Normas: los apartados coinciden con los criterios de la rúbrica; comandos reales y copiables en bloques de código; la comprobación, con una salida verificable (`curl`, `git log`, `docker compose ps`); los fallos que tuviste suman; nada de credenciales reales (usuario `alumno`, contraseña `CAMBIAR_ESTO`); no es un copia y pega de los apuntes, sino la historia ordenada de lo que hiciste; si hay mucho detalle, va en `docs/`.

Ojo con los enlaces del índice. Un **ancla** es el `#nombre` que lleva a un apartado de la misma página. La web del curso escribe `#instalacion` sin tilde, que es como lo genera Zensical; GitHub conserva la tilde (`#instalación`). En un README que se lee en GitHub, pon la tilde y pincha el índice para comprobarlo. Por esa diferencia salían los avisos "anchor does not exist" que arregló la issue #33 de gitanddocs.

#### 5.2.12 Markdown y Mermaid

**Markdown**: texto plano con marcas sencillas que GitHub y los generadores convierten en HTML. Se versiona bien (el `diff` enseña la línea exacta que cambió), se lee en crudo y sirve en cualquier sistema, al contrario que un `.docx`. Lo básico:

- `#`, `##` y `###`: títulos de nivel 1, 2 y 3. `**negrita**`, `*cursiva*` y `` `código` `` dentro de una línea.
- `- punto` y `1. punto`: listas. `[texto](otra-pagina.md)`: enlace relativo, que funciona en GitHub y en la copia local.
- Tres comillas invertidas con el lenguaje (` ```bash `): bloque de código con colores. Filas con `|` y debajo de la cabecera `|---|---|`: tabla.

**Mermaid**: un lenguaje para dibujar diagramas escribiendo texto. Va en un bloque de código con la palabra `mermaid` y GitHub y Zensical lo convierten en dibujo. Como es texto, se versiona como lo demás:

````markdown
```mermaid
flowchart LR
    A["docs/*.md"] --> B["zensical build"] --> C["site/"]
```
````

#### 5.2.13 Otros ficheros del repositorio

| Fichero | Para qué |
|---|---|
| `LICENSE` | La licencia: qué puede hacer otra gente con tu código (la guiada 02 usa MIT). Con README y `.gitignore`, es el mínimo de la web |
| `CHANGELOG.md` | Recomendado: los cambios agrupados por versión con el formato *Keep a Changelog* (`## [Unreleased]`, `## [1.0.0] - fecha` y dentro `### Added`, `### Changed`, `### Removed`) |
| `CONTRIBUTING.md` | No sale en la web del curso. Es el fichero estándar de GitHub con las normas para colaborar, y GitHub lo enlaza al abrir una issue o un PR |

#### 5.2.14 Generadores de documentación

Hay dos formas de publicar Markdown: que la **plataforma** lo enseñe tal cual (GitHub y GitLab muestran README y wikis ya formateados, sin instalar nada) o usar un **generador de sitios estáticos**: un programa que convierte una carpeta de Markdown y un fichero de configuración en una **web estática** (HTML, CSS y JS ya hechos que el servidor solo entrega, sin ejecutar código en cada visita). Esa web se sirve con NGINX o con un hosting estático como **GitHub Pages** (el alojamiento de webs estáticas de GitHub).

| Generador | Configuración | Fuentes | Sale en | Dónde lo hemos usado |
|---|---|---|---|---|
| Zensical (Python) | `zensical.toml` | `docs/` | `site/` | gitanddocs y la web del curso |
| MkDocs (Python) | `mkdocs.yml` | `docs/` | `site/` | Guiada 02, con `mkdocs build --strict` |
| Jekyll (Ruby) | `_config.yml` | Raíz y `_posts/` | `_site/` | El blog de mi práctica. GitHub Pages lo trae integrado |

La UT2 nombra otros generadores al hablar de JAMstack (webs que se generan antes y se sirven ya hechas): Hugo, Astro, Eleventy y Next.js. Y **markdownlint** no genera nada: es un *linter* de Markdown (un programa que revisa un texto o un código sin ejecutarlo y avisa de fallos de formato). En gitanddocs, Zensical se usa con **uv**, el gestor de paquetes y entornos de Python del proyecto. `uv run` ejecuta un comando dentro del entorno del proyecto (`.venv`) con las versiones exactas de `uv.lock`.

| Comando | Qué hace |
|---|---|
| `uv run zensical serve` | Genera la web y la sirve en `http://localhost:8000`. Al guardar un `.md`, la página se recarga sola. Es para escribir. Se para con Ctrl+C |
| `uv run zensical build` | Genera la web una vez en `site/`. Es lo que se despliega |
| `uv run zensical build --clean` | Lo mismo, pero antes borra la caché (lo guardado de la vez anterior para ir más rápido) y lo genera todo desde cero |
| `uv run zensical build --strict` | Si hay un aviso (por ejemplo, un enlace a una página que no existe), aborta y termina con error |

Normas del profe: la documentación va en `docs/`, no en el README, y cada página nueva se añade a `nav` en `zensical.toml`. Las rutas de `nav` son relativas a `docs/`. **TOML** es otro formato de configuración, con `clave = valor` y secciones entre corchetes (`[project]`). Así está en gitanddocs (recortado):

```toml
nav = [
  { "Get started" = "index.md" },
  { "Gitea" = [
  { "Install Gitea with Docker" = "gitea/Install-Gitea-with-docker.md" },
  ]},
]
```

**Formatos de documentación (RA6-c)**: Markdown (README, páginas, entradas del blog), HTML (la web generada), YAML (workflows, `compose.yaml`, `mkdocs.yml`), TOML (`zensical.toml`, `pyproject.toml`), Mermaid (diagramas), texto plano (`comprobaciones.txt` con salidas reales) y PDF (se puede sacar desde Markdown).

#### 5.2.15 CI, entrega continua y despliegue continuo

| Nivel | Qué se automatiza | Qué decide una persona | En una panadería |
|---|---|---|---|
| Integración continua (CI) | Cada push o PR se construye y se prueba solo | Todo lo demás | Cada hornada pasa un control de calidad |
| Entrega continua (CD) | Todo hasta dejar el artefacto listo para producción | **Cuándo** se publica (pulsa un botón) | El pan queda embolsado; el encargado decide cuándo sale la furgoneta |
| Despliegue continuo (CD) | Todo, también la subida a producción | Nada | La furgoneta sale sola con cada hornada que pasa el control |

- Truco: las dos CD solo se diferencian en si hay **aprobación humana antes de producción**.
- **Pipeline**: la cadena de pasos automáticos de cada cambio: Source (descargar el código), Build (instalar o compilar), Test (pruebas), Package (crear el artefacto) y Deploy (publicarlo). Si un paso falla, todo se para ahí y queda en rojo. Lo barato y rápido (el *lint*) va primero: **fallo rápido**.
- **Artefacto**: el paquete que sale del pipeline y que es lo que se instala (una imagen Docker, un ZIP...). Se guarda en un **registro** (Docker Hub, GHCR) con su versión o con el **hash** del commit (su identificador, como `1f456da`). Lo que se probó es justo lo que se instala, y volver atrás es desplegar el artefacto anterior.
- **Entorno**: cada sitio donde corre el programa: local (tu ordenador), integración (donde corre la CI), staging o preproducción (una copia de producción para probar) y producción (lo que usan los clientes). Cuanto más se parezcan, menos sorpresas. El profe tiene una máquina de staging y otra de producción en Oracle Cloud.
- **Ramas y CI**: con feature branches o GitHub Flow, cada PR ejecuta las pruebas y **solo al fusionar en `main`** se construye y publica el artefacto (así no se fabrican artefactos de ramas que nunca llegarán a producción). En trunk-based, cada push a `main` lanza el pipeline y un despliegue frecuente.
- Herramientas: GitHub Actions (`.github/workflows/*.yml`), GitLab CI/CD (`.gitlab-ci.yml`) y Jenkins (`Jenkinsfile`, en un servidor propio).

#### 5.2.16 GitHub Actions: las piezas

**GitHub Actions** es la CI de GitHub. Un **workflow** es un fichero YAML dentro de `.github/workflows/`: si está en otra carpeta, GitHub no lo ejecuta.

| Clave | Qué es |
|---|---|
| `on:` | Los **eventos** que lo disparan: `push` (se filtra con `branches: [main]`), `pull_request`, `workflow_dispatch` (botón **Run workflow** para lanzarlo a mano) y `schedule` (por horario) |
| `jobs:` | Los **trabajos**. Cada job corre en su propia máquina limpia y, por defecto, todos en paralelo |
| `runs-on:` | El **runner**: la máquina virtual de GitHub que ejecuta el job (`ubuntu-latest`, `ubuntu-24.04`) |
| `steps:` | Los **pasos** del job, en orden. Si uno termina con error (código de salida distinto de 0), el job se para y sale en rojo |
| `uses:` | Ejecuta una **acción**: un paso ya hecho y reutilizable (`actions/checkout@v4`; `@v4` es su versión). Se fija siempre la versión, para no depender de cambios inesperados de la acción |
| `run:` | Ejecuta comandos de terminal escritos por ti (`run: \|` para varias líneas) |
| `with:` | Parámetros que recibe una acción |
| `needs:` y `if:` | `needs` hace que un job espere a que otro termine bien (`needs: test`); `if` pone una condición para ejecutar un job o un paso |
| `permissions:` | Lo que puede hacer el **token** automático del workflow (una credencial temporal que GitHub crea en cada ejecución): `contents: read`... Siempre lo mínimo |
| `secrets` | Contraseñas y tokens guardados en **Settings > Secrets and variables > Actions**. Se usan con `${{ secrets.NOMBRE }}` y nunca se escriben en el YAML. `GITHUB_TOKEN` lo crea GitHub solo |

#### 5.2.17 El ci.yml de mi práctica, línea a línea

```yaml
name: CI                          # nombre que sale en la pestaña Actions
on:                               # cuándo se ejecuta
  push:
    branches: [main]              # en cada push a main
  pull_request:                   # y en cada PR, venga de la rama que venga
jobs:
  comprobar:                      # un único job, llamado comprobar
    runs-on: ubuntu-24.04         # runner Ubuntu, con la versión fijada
    steps:
      - name: Descargar el repositorio
        uses: actions/checkout@v7          # copia el repo en el runner
      - name: Instalar uv
        uses: astral-sh/setup-uv@v10.3.0   # acción que instala uv
      - name: Generar la documentación con Zensical
        working-directory: docs-zensical   # carpeta donde corre este paso
        run: |                             # varias líneas de comandos
          uv sync --locked                 # versiones exactas de uv.lock
          uv run zensical build            # crea docs-zensical/site/
      - name: Generar el blog con Jekyll
        run: docker compose run --rm jekyll           # genera el blog y borra el contenedor
      - name: Comprobar la configuración de NGINX
        run: docker compose run --rm nginx nginx -t   # revisa la sintaxis de NGINX
      - name: Arrancar NGINX y probar las dos webs
        run: |
          docker compose up -d                        # arranca NGINX en segundo plano
          sleep 2                                     # le da tiempo a arrancar
          curl -fsS -H "Host: docs.local" http://localhost:8080/ | grep "<title>Get started - Documentation</title>"
          # (aquí van dos curl más: el blog con blog.local y la portada sin nombre)
          curl -sI -H "Host: docs.local" http://localhost:8080/markdown | grep -i "^location: /markdown/"
          docker compose down                         # lo para y lo borra
```

- Los comentarios con `#` son de este apunte; en el fichero real no están. Es **CI pura**: comprueba, pero no publica nada.
- **Docker Compose** arranca los contenedores descritos en `compose.yaml`; **curl** hace peticiones HTTP desde la terminal (`-f`: falla si la respuesta es 400 o más); **grep** busca un texto y falla si no lo encuentra. Cualquier fallo pone el paso en rojo.
- `branches: [main]` solo filtra los push. Por eso también hay ejecuciones de mis PR desde `fase-1` y `fase-2`.

#### 5.2.18 El despliegue de gitanddocs a GitHub Pages

```yaml
name: Documentation
on:
  push:
    branches:
      - master
      - main                    # solo push a main (o master): los PR no lo disparan
permissions:
  contents: read                # leer el código, nada más
  pages: write                  # publicar en GitHub Pages
  id-token: write               # demostrar a Pages que el despliegue sale de este workflow
jobs:
  deploy:
    environment:
      name: github-pages        # el entorno de despliegue que muestra GitHub
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - uses: actions/configure-pages@v6
      - uses: actions/checkout@v7
      - uses: actions/setup-python@v6
        with:
          python-version: 3.x
      - run: pip install zensical
      - run: zensical build --clean           # genera site/ en el runner
      - uses: actions/upload-pages-artifact@v5
        with:
          path: site                          # empaqueta site/ como artefacto
      - uses: actions/deploy-pages@v5         # lo publica
        id: deployment
```

- Cada merge en `main` acaba publicado en https://monium.github.io/gitanddocs/ sin que nadie pulse nada: es **despliegue continuo**. Las 3 aprobaciones deciden si el cambio entra en `main`; a partir de ahí, publicar es automático.
- `site/` se crea en el runner y viaja como **artefacto**: por eso no hace falta (ni se debe) subirlo al repo. Y como no se ejecuta en los PR, antes de abrir uno compruebo en local con `uv run zensical build --clean` que sale "No issues found".

#### 5.2.19 Calidad continua

La CI no solo dice "pasa o no pasa": vigila la calidad en cada cambio. El glosario de la web define la CI como comprobaciones automáticas de tres tipos:

| Comprobación | Qué vigila | Ejemplo del curso |
|---|---|---|
| Lint | Formato y fallos probables, sin ejecutar nada | markdownlint para Markdown |
| Tests (pruebas) | Que el código hace lo que debe | `pytest -q` en la guiada 25; `nginx -t` y `curl` en mi práctica |
| Build estricto | Que la documentación se genera sin enlaces rotos | `mkdocs build --strict` en la guiada 02 |

Matiz clave: sin `--strict`, un enlace roto da un aviso pero el build termina bien (código 0) y la CI sale **verde**. Con `--strict` termina con error y sale **roja**. Con la protección de rama se puede exigir que estas comprobaciones pasen antes del merge.

### 5.3 Manos a la obra

Ningún paso cambia tus repos: solo lees, generas una carpeta que luego borras y escribes en papel.

**Paso 1. Lee el `ci.yml` de mi práctica y explícalo.**

```bash
cd "$HOME/Desktop/DAM 2do Año/DPL/1er-trimestre/1er-examen/nginx-para-todos"
cat .github/workflows/ci.yml
```

Sale el fichero de 5.2, sin mis comentarios y con los tres `curl` de títulos completos. Tapa 5.2 y di en voz alta, bloque a bloque: cuándo se ejecuta (`on`), cuántos jobs hay y dónde corren (`jobs`, `runs-on`) y, para cada step, si usa una acción (`uses`) o comandos (`run`) y qué comprueba. Después responde: ¿qué añadirías para poder lanzarlo a mano? (`workflow_dispatch:` dentro de `on:`).

**Paso 2. Mira las ejecuciones en la pestaña Actions.** Abre https://github.com/diegoalegil/nginx-para-todos/actions (la URL de `git remote -v` sin el `.git` y con `/actions`). Salen 6 ejecuciones de **CI**, todas en verde; la de arriba es "Junto la fase 2 en main" (rama `main`, evento `push`, 52 s). Entra en ella y en el job **comprobar**: salen Set up job, mis seis steps con su `name`, dos "Post" y Complete job (esos los añade GitHub). Despliega "Arrancar NGINX y probar las dos webs" y verás las líneas `<title>` que encontró `grep`. Vuelve a la lista: hay ejecuciones con rama `fase-1` y `fase-2` y evento `pull_request`. Explica por qué, si el workflow dice `branches: [main]`.

<details>
<summary>Respuesta</summary>

`branches: [main]` está debajo de `push`, así que solo filtra los push. `pull_request:` no tiene filtro, y cada PR que abrí (de `fase-1` y de `fase-2` hacia `main`) disparó el workflow. En la lista, la rama que sale es la del PR.

</details>

**Paso 3. Genera la web de gitanddocs y comprueba que Git no la ve.**

```bash
cd "$HOME/Desktop/DAM 2do Año/DPL/gitanddocs"
uv run zensical build --clean
```

Salen tres líneas: `Build started`, `No issues found` y `Build finished in 0.23s` (el tiempo cambia de una vez a otra). Con `ls site` verás una carpeta por página de `docs/` (`markdown/`, `gitea/`...), `assets/` (CSS, JS e imágenes del tema), `search.json` (el buscador), `sitemap.xml` y `404.html`. Ahora `git status` sigue diciendo `nada para hacer commit, el árbol de trabajo está limpio`, y esto te dice por qué:

```bash
git check-ignore -v site/
```

```text
.gitignore:203:/site	site/
```

La regla `/site` de la línea 203 del `.gitignore` la ignora. Di en voz alta las razones de 5.2 por las que no se sube.

**Paso 4. Escribe de memoria un workflow mínimo.** En papel, sin mirar: un workflow que en cada push descargue el repositorio y haga un `echo`. Apunta también en qué ruta va el fichero. Después compara.

<details>
<summary>Respuesta</summary>

Ruta: `.github/workflows/hola.yml` (el nombre del fichero da igual; la carpeta, no).

```yaml
name: Hola
on: push
jobs:
  saludar:
    runs-on: ubuntu-latest
    steps:
      - name: Descargar el repositorio
        uses: actions/checkout@v4
      - name: Saludar
        run: echo "Hola desde GitHub Actions"
```

Repasa: `on: push` sin filtro (cualquier rama); un job con un nombre inventado; `runs-on`; `steps` es una lista (cada paso empieza con `-`); el checkout con `uses` y el echo con `run`; sangría con espacios, nunca con tabuladores. La web usa `actions/checkout@v4`, y mi práctica y gitanddocs `@v7`: el número es la versión de la acción.

</details>

**Paso 5. Escribe de memoria el esqueleto del README.** En papel: títulos, índice y una línea de qué va en cada apartado. Después compara.

<details>
<summary>Respuesta</summary>

```markdown
# Nombre del proyecto

Qué es y para qué sirve, en una o dos líneas.

## Índice

- [Instalación](#instalación)
- [Configuración](#configuración)
- [Comprobación](#comprobación)
- [Problemas encontrados y solución](#problemas-encontrados-y-solución)
- [Repositorio remoto](#repositorio-remoto)
- [Relación curricular](#relación-curricular)

## Instalación
## Configuración
## Comprobación
## Problemas encontrados y solución
## Repositorio remoto
## Relación curricular
```

Qué va en cada uno: instalación, comandos exactos en bloques de código; configuración, ficheros que se tocan y por qué; comprobación, comandos con su salida real; problemas, qué pasó, por qué y cómo lo arreglé; repositorio remoto, la URL; relación curricular, los RA y CE. Repasa: un solo `#`; índice al principio (con tilde en GitHub; la web lo escribe sin tilde); apartados que coinciden con la rúbrica; ninguna credencial real.

</details>

**Limpieza.** En gitanddocs, `rm -rf site` y `git status`: debe acabar en `nada para hacer commit, el árbol de trabajo está limpio`. Solo borras la web generada, que se recrea con otro build; `.venv/` y `.cache/` se quedan (también están ignoradas). En `nginx-para-todos` no has cambiado nada. Guarda los papeles de los pasos 4 y 5 para el viernes.

### 5.4 Comprueba que lo sabes

**P1. (Test)** Al crear un PR ves `base: issue-41 ← compare: main`. Si se aprueba y se fusiona tal cual: **a)** tu arreglo entra en `main`; **b)** `main` entra en `issue-41` y tu arreglo no llega a `main`; **c)** GitHub no deja crear un PR así; **d)** las dos ramas se fusionan en las dos direcciones.

<details>
<summary>Respuesta</summary>

**b)** La base es el destino: los cambios van de `main` hacia `issue-41`. Es lo que pasó en el PR #39. GitHub sí deja crearlo, por eso hay que leer la línea antes de pulsar el botón.

</details>

**P2. (Test)** ¿Qué descripción de PR cierra la issue 19 al fusionar el PR en `main`? **a)** `Relacionado con #19`; **b)** `- Closes #` y, en la línea de abajo, `19`; **c)** `- Closes #19`; **d)** `Closes issue 19`.

<details>
<summary>Respuesta</summary>

**c)** Palabra clave y `#número` juntos en la misma línea. La a) solo enlaza, la b) es el fallo del PR #29 y la d) no lleva `#`, así que GitHub no la reconoce como referencia.

</details>

**P3. (Test)** Quieres mandar un arreglo a un repo público de otra persona en el que no tienes permiso de escritura. ¿Qué haces primero? **a)** Fork en GitHub y después clonar tu fork; **b)** `git clone` del original, commit en `main` y `git push origin main`; **c)** `git remote add upstream URL` y `git push upstream`; **d)** abrir una issue pidiendo permiso de administrador.

<details>
<summary>Respuesta</summary>

**a)** Sin permiso de escritura, el push al original falla (b y c). Trabajas en tu fork y le mandas el cambio con un PR.

</details>

**P4. (Test)** Revisas el PR de un compañero: falta el enlace al repositorio remoto y no quieres que se fusione así. ¿Qué eliges en **Review changes**? **a)** Comment; **b)** Approve, con "LGTM"; **c)** Close pull request; **d)** Request changes.

<details>
<summary>Respuesta</summary>

**d)** "Request changes" pide cambios y, con `main` protegida, bloquea el merge hasta que lo apruebes o se descarte tu revisión. Un "Comment" no bloquea nada, y cerrar el PR lo descartaría en vez de mejorarlo.

</details>

**P5. (Test)** Quieres que tu workflow tenga un botón **Run workflow** para lanzarlo a mano. ¿Qué añades dentro de `on:`? **a)** `schedule:`; **b)** `workflow_dispatch:`; **c)** `manual: true`; **d)** `pull_request:`.

<details>
<summary>Respuesta</summary>

**b)** `workflow_dispatch` es el evento de lanzamiento manual. `schedule` lo lanza por horario y `manual` no existe.

</details>

**P6. (Escribe)** Escribe el `.gitignore` mínimo de un repo con documentación en Zensical (instalada con uv) y un blog en Jekyll, para que no se suban las dos webs generadas ni el entorno de Python.

<details>
<summary>Respuesta</summary>

```text
# entorno de python que crea uv
.venv/
# webs generadas, se recrean con zensical build y jekyll build
site/
_site/
```

Es lo que tiene mi práctica (más `.DS_Store`, que crea macOS). La barra final indica que son carpetas.

</details>

**P7. (Escribe)** En gitanddocs has creado `docs/nginx/instalar.md`. Escribe lo que añades a `nav` en `zensical.toml` para que salga en el menú como "Instalar NGINX" dentro de una sección "NGINX".

<details>
<summary>Respuesta</summary>

```toml
  { "NGINX" = [
  { "Instalar NGINX" = "nginx/instalar.md" },
  ]},
```

Va dentro de la lista `nav = [ ... ]`. La ruta es relativa a `docs/`: no se escribe `docs/nginx/instalar.md`. Lo compruebas con `uv run zensical serve` o con un build que diga "No issues found".

</details>

**P8. (Escribe)** Escribe un step de GitHub Actions que, dentro de la carpeta `docs-zensical`, instale las versiones exactas de `uv.lock` y genere la web de forma que un enlace roto ponga la CI en rojo.

<details>
<summary>Respuesta</summary>

```yaml
      - name: Generar la documentación
        working-directory: docs-zensical
        run: |
          uv sync --locked
          uv run zensical build --strict
```

`working-directory` cambia la carpeta del paso, `run: |` admite varias líneas y `--strict` hace que un aviso termine con error.

</details>

**P9. (Escribe)** Escribe la cabecera de `.github/ISSUE_TEMPLATE/bug_report.md` para que la plantilla salga en el menú como "Reporte de Bug" y ponga sola la label `bug`.

<details>
<summary>Respuesta</summary>

```markdown
---
name: "Reporte de Bug"
about: Reporta un error para que podamos corregirlo
labels: bug
assignees: ''
---
```

Es la cabecera real de gitanddocs. Debajo va el cuerpo de la plantilla en Markdown. La label solo se pone si `bug` existe en el repo.

</details>

**P10. (Escribe)** Te han fusionado el PR de la rama `issue-7` y GitHub ya ha borrado la rama remota. Escribe los comandos para poner al día tu `main` local, borrar la rama local y quitar la referencia vieja `origin/issue-7`.

<details>
<summary>Respuesta</summary>

```bash
git switch main
git pull
git branch -d issue-7
git fetch --prune
```

`-d` solo borra la rama si ya está fusionada, así que es seguro: responde `Eliminada la rama issue-7 (era 191fdbf).` (el hash cambia). `--prune` quita las referencias a ramas que ya no existen en el remoto: enseña una línea con `[eliminado]` y `-> origin/issue-7`.

</details>

**P11. (Interpreta)** En una copia de gitanddocs añades al final de `docs/markdown.md` una línea en blanco y la línea `[Roto](no-existe.md)`, y ejecutas:

```text
$ uv run zensical build --strict
Build started
Warning: page does not exist
     ╭─[ markdown.md:112:8 ]
 112 │ [Roto](no-existe.md)
1 issue found
[...]
RuntimeError: Aborted because --strict flag is set
$ echo $?
1
```

¿Qué ha fallado y dónde? ¿De qué color saldría este paso en una CI? ¿Y sin `--strict`? ¿Cómo lo arreglas?

<details>
<summary>Respuesta</summary>

- Hay un enlace a una página que no existe en `markdown.md`, línea 112, columna 8.
- Por `--strict`, el aviso se convierte en error: el build aborta y termina con código 1 (`echo $?` enseña el código de salida del último comando). En una CI, el paso saldría en **rojo** y los siguientes no se ejecutarían.
- Sin `--strict` sale el mismo aviso y "1 issue found", pero termina con código 0: la CI saldría en **verde** con un enlace roto.
- Se arregla corrigiendo el enlace para que apunte a un `.md` que exista (o creando esa página y añadiéndola a `nav`).

</details>

**P12. (Razona)** En gitanddocs alguien abre un PR que añade un enlace a una página que no existe. Se fusiona y la web publicada queda con el enlace roto. Mirando `docs.yml`, da dos razones por las que la CI no lo paró y propón un cambio.

<details>
<summary>Respuesta</summary>

1. `docs.yml` solo se dispara con push a `main` (o `master`), no con `pull_request`: el PR no pasó por ninguna comprobación.
2. Usa `zensical build --clean` sin `--strict`: incluso después del merge, el aviso no hizo fallar el build y la web se publicó.

Cambio: un workflow aparte (o un job aparte) con `on: pull_request` que solo ejecute `zensical build --strict`, sin publicar nada, y exigirlo en la protección de `main` con **Require status checks to pass**. Mientras no exista, toca comprobarlo en local antes de abrir el PR.

</details>

**P13. (Razona)** ¿El `docs.yml` de gitanddocs es entrega continua o despliegue continuo? Justifícalo y di qué cambiarías para que fuera lo otro.

<details>
<summary>Respuesta</summary>

**Despliegue continuo**: cada push a `main` se construye y se publica en GitHub Pages sin que nadie apruebe la publicación. Las aprobaciones del PR deciden si el cambio entra en `main`, no cuándo se publica. Para que fuera entrega continua haría falta una decisión humana antes de publicar: por ejemplo, lanzar el workflow solo a mano (`workflow_dispatch`) o pedir que alguien apruebe el despliegue al entorno `github-pages`.

</details>

**P14. (Razona)** Sobre mi PR #42 en gitanddocs, donde `main` exige 3 aprobaciones: a) me aprueba alguien con permiso de escritura que no estaba en mi lista de revisores, ¿cuenta?; b) ¿puedo aprobarlo yo para llegar a 3?; c) me piden un cambio y subo un commit nuevo a `issue-41`, ¿tengo que abrir otro PR?

<details>
<summary>Respuesta</summary>

a) **Sí**: cuenta cualquier aprobación de alguien con permiso de escritura, estuviera o no en la lista. b) **No**: el autor no puede aprobar su propio PR. c) **No**: cada push a la rama del PR lo actualiza solo. En gitanddocs las aprobaciones que ya tengo se mantienen, porque el ruleset no anula aprobaciones al subir commits; si lo hiciera, habría que pedirlas otra vez.

</details>

**P15. (Interpreta)** En la ejecución de `docs.yml` lanzada por el merge del PR #38, GitHub enseña en el job `deploy` steps como `Run actions/checkout@v7`, `Run zensical build --clean`, `Run actions/upload-pages-artifact@v5` y `Run actions/deploy-pages@v5`, en ese orden. a) ¿Por qué aquí se llaman "Run ..." y en mi práctica "Descargar el repositorio"? b) Si fallara "Run zensical build --clean", ¿qué pasaría con los dos pasos siguientes y con la web publicada? c) ¿Qué evento lanzó esta ejecución?

<details>
<summary>Respuesta</summary>

a) Los steps de `docs.yml` no tienen `name:`, así que GitHub les pone "Run" seguido de lo que ejecutan. En mi `ci.yml` cada step lleva su `name:`. b) El job se pararía en rojo: no se subiría el artefacto ni se desplegaría, y la web publicada se quedaría como estaba, con la versión anterior. c) Un **push** a `main`: fusionar un PR mete un commit nuevo en `main`, y eso es un push.

</details>

### 5.5 Si te atascas

- Fork, upstream, ciclo del PR, `Closes`, revisión y plantillas: [05, apartado 4](05-ut1-git-documentacion-cicd.md) y https://dpl-f1facc.gitlab.io/ut01/teoria/git/ (apartado 10, flujo colaborativo en GitHub). Flujos de ramas y formas de fusionar un PR: [05, apartado 3](05-ut1-git-documentacion-cicd.md). Protección de ramas, tokens y secretos: [05, apartado 5](05-ut1-git-documentacion-cicd.md).
- README, Markdown, generadores y formatos: [05, apartado 6](05-ut1-git-documentacion-cicd.md) y https://dpl-f1facc.gitlab.io/ut01/teoria/documentacion/
- Qué se entrega y cómo (README, enlace remoto, RA/CE): https://dpl-f1facc.gitlab.io/evaluacion/entregables/ y el flujo colaborativo completo, con MkDocs y `--strict`: https://dpl-f1facc.gitlab.io/ut01/practicas/guiada-02-colaboracion-git/
- Mi práctica: Zensical en [04, apartado 2.3](04-practica-nginx.md), Jekyll en [04, apartado 2.4](04-practica-nginx.md), su flujo de git en [04, apartado 4](04-practica-nginx.md) y el `ci.yml` para defenderlo en [04, apartado 5](04-practica-nginx.md).
- CI/CD y GitHub Actions: [05, apartado 7](05-ut1-git-documentacion-cicd.md), https://dpl-f1facc.gitlab.io/ut01/teoria/ci-cd/ y la guiada 25: https://dpl-f1facc.gitlab.io/ut01/practicas/guiada-25-github-actions-cicd/
- GitHub Pages y el hosting estático: [06, apartado 2.10](06-ut2-arquitecturas-servidores-web.md). Staging y producción en máquinas reales: [08, apartado «Para qué dos máquinas»](08-oracle-cloud-instancias.md).
- Más preguntas: [07, apartado 4.3](07-plan-de-repaso-p1.md), [07, apartado 4.4](07-plan-de-repaso-p1.md), [07, apartado 4.5](07-plan-de-repaso-p1.md) y el simulacro de [07, apartado 5](07-plan-de-repaso-p1.md).

## 6. Miércoles 4/11: arquitecturas web y HTTP

Al acabar el día sabrás dibujar cómo se organiza una web (quién pide, quién responde y por dónde viajan los datos), leer de arriba abajo una conversación HTTP con `curl` y decir dónde vive cada fichero de una aplicación en el servidor. Es la base del RA1 (resultado de aprendizaje: lo que tienes que saber hacer) y en una prueba objetiva da muchas preguntas cortas: códigos, cabeceras, puertos y diferencias entre conceptos parecidos. Cubre los criterios de evaluación (CE: los puntos concretos con los que se mide cada RA) **RA1-a** (arquitecturas), **RA1-b** (protocolos HTTP y HTTPS), **RA1-g** (estructura de una aplicación) y **RA1-h** (requisitos de implantación).

### 6.1 Plan del día

| Bloque | Qué haces | Tiempo |
|---|---|---|
| 0. Registro de fallos | Contesta las filas sin marcar del registro (apartado 11): las del martes y las que sigan pendientes | 10 min |
| 1. Lo imprescindible | Lee el 6.2 con un papel al lado. Al terminar cada tabla, tápala y dila en voz alta | 40 min |
| Descanso | Levántate de la silla | 5 min |
| 2. Manos a la obra | Haz los pasos del 6.3 en la Terminal del Mac y compara tu salida con la del apunte. Solo necesitas Internet | 40 min |
| Descanso | | 5 min |
| 3. Comprueba que lo sabes | Responde P1 a P10 del 6.4 por escrito y sin mirar. Corrige al final, no después de cada una | 30 min |
| Descanso | | 5 min |
| 4. Apuntar fallos | Apunta cada fallo en el registro (apartado 11) y relee su trozo del 6.2 | 15 min |
| **Total** | | **2 h 30 min** |

### 6.2 Lo imprescindible

#### 6.2.1 Qué es una arquitectura web y el modelo cliente-servidor

Una **arquitectura web** es la forma en que se organizan las piezas (programas y máquinas) que hacen funcionar una web. Tiene tres componentes:

| Componente | Qué es | Ejemplos |
|---|---|---|
| Cliente (*user agent*) | El programa que **pide** recursos (páginas, imágenes, datos...) | Navegador, `curl`, `wget`, una app móvil |
| Servidor | El programa que **escucha y responde**, y la máquina donde corre | nginx, Apache |
| Red y protocolo | El camino de los datos y las reglas para hablar | TCP/IP para transportar, HTTP como idioma |

Un **protocolo** es un conjunto de reglas: quién habla, cómo y qué se contesta. Lo que viaja son **recursos**: páginas **HTML** (el texto y su estructura), hojas **CSS** (el estilo), imágenes, **JavaScript** (código que corre en el navegador) o datos en **JSON** (un formato de texto para datos, como `{"total": 42.5}`). La web usa el modelo **cliente-servidor**: **el cliente siempre empieza y el servidor solo contesta**. Piensa en un restaurante: tú (cliente) pides; el camarero (servidor web) te trae lo que ya está hecho y pasa a cocina (servidor de aplicaciones) lo que hay que preparar; la despensa es la base de datos.

#### 6.2.2 Capas de red: dónde va cada protocolo

Enviar datos por la red se reparte en **capas**: cada una hace una tarea, se apoya en la de abajo y da servicio a la de arriba (como una cadena de montaje). La web del curso usa el modelo **OSI** (7 capas) simplificado:

| Nº | Capa | Qué hace | En la web | Se comprueba con |
|---|---|---|---|---|
| 7 | Aplicación | Los protocolos de los programas | HTTP, HTTPS, DNS, FTP | `curl`, `dig` |
| 6 | Presentación | Formato de los datos y cifrado | HTML, CSS, JSON, **TLS** | `curl -v` |
| 5 | Sesión | Mantener el diálogo | Cookies y sesiones | |
| 4 | Transporte | Comunicación entre **puertos** | TCP (80 y 443), UDP | `ss -tlnp` |
| 3 | Red | Direcciones **IP** y rutas | IP | `ping`, `ip route` |
| 2 y 1 | Enlace y física | Direcciones MAC (la dirección física de cada tarjeta de red) y el medio | Ethernet, Wi-Fi, cable | |

- **DNS**: el sistema que traduce nombres (`www.example.org`) a direcciones IP. Es la agenda de contactos de Internet.
- **IP**: la dirección de una máquina en la red (`172.66.157.237`). **Puerto**: número (de 0 a 65535) que indica a qué programa de esa máquina va la conexión. IP = dirección del edificio; puerto = número de puerta.
- **TCP**: transporte fiable, confirma cada paquete y los entrega en orden. **UDP**: sin confirmaciones ni orden, más ligero (lo usan DNS y HTTP/3).
- **TLS** (*Transport Layer Security*): el protocolo que cifra la conexión; convierte HTTP en HTTPS. Aunque se llame "de transporte", el curso lo pone en la capa 6. (El modelo **TCP/IP**, el que se usa de verdad en Internet, agrupa todo en cuatro capas: aplicación, transporte, internet y acceso a red. Si preguntan "según el curso", contesta con OSI.)

Lo que más cae: **HTTP en la 7, TCP en la 4, IP en la 3**. La pila sirve para diagnosticar: "no responde" puede ser el servicio (7), el puerto (4), la ruta (3) o el nombre (DNS).

#### 6.2.3 Capas de una aplicación: dos y tres capas

Además de las capas de red, una aplicación web se divide por **funciones**. La web habla de **cuatro capas** (contando el cliente) y de **tres** (sin contarlo); es el mismo dibujo:

| Capa | Qué hace | En el curso | Restaurante |
|---|---|---|---|
| Cliente | La interfaz que usa la persona | Navegador | El comensal |
| Presentación | Sirve las páginas (HTML, CSS, JS) y recibe lo que manda el cliente | nginx | El camarero |
| Lógica de negocio | Ejecuta el código: calcula, valida, gestiona la sesión, consulta datos | PHP-FPM, Gunicorn | La cocina |
| Datos | Guarda la información que tiene que durar | PostgreSQL, MySQL, ficheros | La despensa |

| | Dos capas | Tres capas |
|---|---|---|
| Piezas | Cliente y servidor web | Servidor web, servidor de aplicaciones y base de datos, separados |
| Ejemplo | nginx sirviendo ficheros (mi práctica de NGINX) | nginx + Gunicorn con Django + PostgreSQL (UT4) |
| Ventajas | Sencilla, barata, fácil de montar | Cada capa se cambia o escala por separado; la base de datos no queda expuesta a Internet |
| Inconvenientes | Mezcla tareas y crece mal | Más piezas que instalar y vigilar, más puntos de fallo, algo más de latencia |

Si la web es **estática** (siempre igual para todos), no hay capa de lógica ni de datos: el contenido va dentro de los propios HTML.

La web cita también las **fases de un proyecto web**: concepto (qué quiere el cliente y si es viable), diseño (tecnologías, módulos y plan), desarrollo (código, pruebas, documentación y Git) y pruebas e implantación (el momento crítico), más el mantenimiento. Se desarrolla **de abajo arriba** (*bottom-up*): primero datos, luego lógica de negocio y al final presentación. Empezar por la interfaz obliga a rehacerla cuando aparecen los datos y las reglas que faltaban.

#### 6.2.4 Servidor web, servidor de aplicaciones y API

| | Servidor web | Servidor de aplicaciones |
|---|---|---|
| Qué hace | Entrega ficheros que ya existen | Ejecuta código y fabrica la respuesta en el momento |
| Contenido | Igual para todos (estático) | Depende de los datos, la sesión o lo que envías (dinámico) |
| Ejemplos | nginx, Apache | Gunicorn (Python), PHP-FPM (PHP), Tomcat (Java), Node.js |

Trampa típica: nginx **no ejecuta** PHP ni Python. Se los pasa al servidor de aplicaciones con dos directivas (órdenes de su configuración): `proxy_pass` a Gunicorn y `fastcgi_pass` a PHP-FPM.

- **Servicio web**: la idea de lo que se hace ("calcular el total de un pedido"). **Agente**: el programa concreto que lo hace; se puede reescribir en otro lenguaje sin que el servicio cambie.
- **API** (interfaz de programación de aplicaciones): el contrato que dice cómo se pide el servicio, con qué datos y qué se recibe. En la web lo normal es una **API REST**: cada recurso tiene su dirección, se usan los métodos HTTP y se responde en JSON.
- Usar un servicio tiene tres pasos: **descubrimiento** (saber dónde está, normalmente su dirección resuelta por DNS), **acuerdo** (mismo protocolo y formato) e **intercambio de mensajes**.

#### 6.2.5 Alternativas de implantación

**Implantar** es instalar y poner en marcha la aplicación donde la va a usar la gente. La web del curso compara on-premise, hosting, cloud y CMS; las filas con (*) no salen en su tabla, pero conviene distinguirlas.

| Alternativa | Qué es | Ventajas | Inconvenientes |
|---|---|---|---|
| En local (*) | Tu ordenador o un contenedor de laboratorio (`dpl-lab`, mi `nginx-para-todos`) | Gratis y rápido para probar | Solo lo ves tú; no es producción |
| On-premise | Servidores propios dentro de la organización | Control total, datos en casa, sin cuotas | Comprar y mantener hardware, luz, seguridad física |
| Hosting | Alquilar espacio en un servidor de otra empresa | No mantienes hardware ni software | Menos control, límites del plan, dependes del proveedor |
| VPS (*) | Servidor privado virtual: una máquina virtual alquilada en la que eres administrador | Control casi total a precio fijo | Tú instalas, actualizas y aseguras todo |
| Cloud (nube) | Recursos de un proveedor (AWS, Azure, Oracle) bajo demanda y de pago por uso | Escala rápido, pagas lo que usas, servicios gestionados | Coste variable, dependencia, factura compleja |
| CMS | Gestor de contenidos (WordPress): aplicación hecha para publicar desde un panel | Publicas rápido sin programar | Menos flexible; actualizaciones y seguridad a tu cargo |
| Contenedores (*) | No es un sitio, es una forma de empaquetar: la aplicación con todo lo que necesita (Docker) | La misma imagen funciona igual en local, en un VPS o en la nube | Hay que aprender Docker; la máquina de debajo sigue siendo tuya o del proveedor |

Cuándo elegir cada una, según el curso: **on-premise** para datos sensibles, intranets o requisitos legales; **hosting** para webs pequeñas o medianas; **cloud** para cargas variables y proyectos que crecen; **CMS** para contenido que cambia a menudo con estructura estable. Dentro de la nube: si te dan la máquina y tú instalas el resto es **IaaS** (como las instancias de Oracle de [08, apartado «Lo que hizo el profe, paso a paso»](08-oracle-cloud-instancias.md)); si solo subes tu código, **PaaS**; si usas la aplicación terminada (Gmail), **SaaS**.

#### 6.2.6 Arquitecturas modernas: CDN, edge y JAMstack

- **CDN** (red de entrega de contenidos): servidores repartidos por el mundo con copias de tu contenido; te atiende el nodo más cercano (*PoP*, punto de presencia) y así baja la **latencia** (lo que tarda un dato en ir y volver, que crece con la distancia). También comprime, pone el HTTPS cerca del usuario y frena ataques. Una **caché** es una copia guardada de algo ya pedido para no pedirlo otra vez. Lo verás en el paso 1 del 6.3: `www.example.org` responde desde Cloudflare con `cf-cache-status: HIT`.
- **Edge computing**: además de guardar copias, **ejecuta código** en esos nodos (redirigir por idioma, pruebas A/B) sin llegar al servidor de origen.
- **JAMstack**: **J**avaScript en el navegador + **A**PIs para lo dinámico + **M**arkup (HTML) fabricado en el **build** (la fase en la que un programa genera todos los ficheros antes de publicar). El CDN entrega ficheros ya hechos. En una web tradicional (WordPress con PHP), cada visita ejecuta código y consulta la base de datos. **Ventajas**: rendimiento (no se ejecuta nada al pedir la página), seguridad (menos superficie de ataque), escalabilidad (el CDN apenas gasta CPU del origen) y coste (planes gratuitos o muy baratos). **Inconvenientes**: no encaja con datos en tiempo real muy sensibles ni con catálogos enormes cuyos precios cambian a cada rato, porque habría que regenerar la web en cada cambio.
- **Hosting estático**: GitHub Pages, Netlify, Vercel y Cloudflare Pages publican desde Git con CDN y HTTPS incluidos. Zensical (gitanddocs) y Jekyll (mi blog) son generadores de sitios estáticos: encajan con esta idea.

#### 6.2.7 Requisitos para implantar

| Requisito | Por qué | Cómo se comprueba o se resuelve |
|---|---|---|
| Máquina | Potencia para las peticiones previstas; lo dinámico gasta más que lo estático | Dimensionar; mejor dedicada |
| Sistema operativo | Estable, seguro y con control de permisos | Linux casi siempre |
| Conexión | Ancho de banda de subida y de bajada | Contrato con el operador |
| IP estática | Si la IP cambia, nadie te encuentra | IP fija o **DDNS** (servicio que actualiza tu nombre cuando cambia la IP, como Duck DNS) |
| DNS | Que el nombre lleve a tu IP | Registro en un DNS; en el laboratorio, `/etc/hosts` o `curl -H "Host: ..."` |
| Puertos | El servicio escucha en uno y tiene que estar abierto o publicado | `-p 8080:80` en Docker; cortafuegos; en AWS, el *Security Group* (cortafuegos virtual) |
| Disco | Aplicación, logs y copias de seguridad | `df -h` (espacio libre), `du -sh /var/www` (lo que ocupa) |
| Permisos | El usuario del servidor web tiene que poder leer | 644 ficheros y 755 carpetas (6.2.19) |

#### 6.2.8 HTTP: qué pasa al escribir una URL

**HTTP** (protocolo de transferencia de hipertexto) es el idioma de la web: el cliente manda una **petición** (*request*) y el servidor devuelve una **respuesta** (*response*). En HTTP/1.x es texto que puedes leer tal cual. Al escribir `https://www.example.org/` en el navegador:

1. **DNS**: el sistema mira `/etc/hosts` y, si no está ahí, pregunta al DNS qué IP tiene `www.example.org`.
2. **TCP**: abre una conexión con esa IP al puerto 443 (al 80 si es `http`).
3. **TLS**, solo con `https`: saludo para acordar el cifrado y comprobar el certificado.
4. **Petición**: `GET /` con sus cabeceras.
5. **Respuesta**: código de estado, cabeceras y el HTML.
6. El navegador lee el HTML y hace **una petición más por cada** CSS, imagen o script que encuentra.

Una **URL** es la dirección completa de un recurso. Ejemplo: `https://docs.local:8080/guia/index.html?pagina=2#indice`

| Parte | En el ejemplo | Para qué |
|---|---|---|
| Esquema | `https` | Protocolo (`http` o `https`) |
| Host | `docs.local` | Nombre o IP del servidor. Viaja en la cabecera `Host` |
| Puerto | `8080` | Si no se escribe: 80 con `http` y 443 con `https` |
| Ruta | `/guia/index.html` | Qué recurso se pide dentro del servidor (lo que nginx llama `$uri`) |
| Consulta (*query*) | `?pagina=2` | Parámetros `clave=valor`, separados por `&` |
| Fragmento | `#indice` | Sitio de la página al que saltar. **No se envía al servidor** |

#### 6.2.9 La petición y la respuesta

Salida real de `curl -v --http1.1 https://www.example.org`, sin las líneas de conexión y recortada. `>` es lo que envía `curl` y `<` lo que recibe:

```text
> GET / HTTP/1.1
> Host: www.example.org
> User-Agent: curl/8.7.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Date: Sun, 01 Nov 2026 16:22:49 GMT
< Content-Type: text/html; charset=utf-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< Server: cloudflare
[...]
<
<!doctype html><html lang=en><head><meta charset=utf-8>[...]<title>Example Domain</title>[...]
```

| | Petición | Respuesta |
|---|---|---|
| 1.ª línea | **Línea de petición**: método + ruta + versión (`GET / HTTP/1.1`) | **Línea de estado**: versión + código + frase (`HTTP/1.1 200 OK`) |
| Después | **Cabeceras**: líneas `Nombre: valor` con información extra | **Cabeceras** |
| Al final | **Línea en blanco** y, si hace falta, **cuerpo** (los datos de un formulario en un POST) | **Línea en blanco** y **cuerpo** (el HTML, la imagen, el JSON) |

- En HTTP/1.1 la cabecera `Host` es **obligatoria** (sin ella, `400 Bad Request`). Si el puerto no es el de por defecto, va incluido: `curl http://blog.local:8080/` envía `Host: blog.local:8080`.
- Aquí no hay `Content-Length` porque el cuerpo llega por trozos (`Transfer-Encoding: chunked`). `Connection: keep-alive` deja abierta la conexión TCP para más peticiones (la conexión persistente de HTTP/1.1).
- Sin `--http1.1`, `curl` usa HTTP/2 con los sitios HTTPS que lo admiten y verás `HTTP/2 200` **sin la frase "OK"** y las cabeceras **en minúsculas**: HTTP/2 no envía frase de estado.

#### 6.2.10 Métodos: seguro e idempotente

El **método** dice qué quieres hacer con el recurso. **Seguro**: no cambia nada en el servidor. **Idempotente**: repetirlo diez veces deja el servidor igual que hacerlo una (como pulsar el botón de un ascensor ya llamado).

| Método | Para qué | Cuerpo en la petición | Seguro | Idempotente |
|---|---|---|---|---|
| GET | Pedir un recurso (el más usado) | No | Sí | Sí |
| HEAD | Como GET, pero la respuesta **sin cuerpo** (`curl -I`) | No | Sí | Sí |
| POST | Enviar datos: formularios, crear recursos | Sí | No | No |
| PUT | Crear o **reemplazar entero** un recurso | Sí | No | Sí |
| PATCH | Modificar **una parte** de un recurso | Sí | No | No |
| DELETE | Borrar un recurso | Normalmente no | No | Sí |
| OPTIONS | Preguntar qué métodos admite el servidor | No | Sí | Sí |

Truco: los seguros (GET, HEAD, OPTIONS) son idempotentes; de los que cambian cosas, solo PUT y DELETE lo son. Ejemplo del curso: la calculadora muestra el formulario con GET y calcula con POST.

#### 6.2.11 Sin estado, cookies, cabeceras y tipos MIME

HTTP es **sin estado** (*stateless*): cada petición va por libre y el servidor no recuerda las anteriores. Para "recordar" (sesión iniciada, carrito) se usan **cookies**: datos pequeños que el servidor pide guardar con `Set-Cookie` y que el navegador le devuelve en cada petición con `Cookie`. Es el ticket del guardarropa: no te recuerdan, pero enseñas el ticket. Ejemplo real de GitHub: `set-cookie: logged_in=no; [...] path=/; HttpOnly; secure; SameSite=Lax` (`secure`: solo viaja por HTTPS; `HttpOnly`: el JavaScript de la página no la lee).

| Cabecera | Va en | Para qué | Ejemplo |
|---|---|---|---|
| `Host` | Petición | Qué sitio se pide; con ella una IP aloja varias webs | `Host: www.example.org` |
| `User-Agent` | Petición | Qué cliente pide | `User-Agent: curl/8.7.1` |
| `Accept` | Petición | Qué formatos acepta el cliente | `Accept: */*` (cualquiera) |
| `Authorization` | Petición | Credenciales (`curl -u`) | `Authorization: Basic YWx1bW5vOkNBTUJJQVJfRVNUTw==` |
| `Cookie` | Petición | Devuelve las cookies guardadas | `Cookie: logged_in=no` |
| `Content-Type` | Las dos | **Tipo MIME** del cuerpo | `Content-Type: text/html; charset=utf-8` |
| `Content-Length` | Las dos | Tamaño del cuerpo en bytes | `Content-Length: 21` |
| `Server` | Respuesta | Software del servidor | `Server: nginx/1.30.6` |
| `Location` | Respuesta | A dónde ir en una redirección 3xx | `Location: https://github.com/` |
| `Cache-Control` | Sobre todo respuesta | Si se puede guardar en caché y cuántos segundos | `cache-control: max-age=14400` (4 h) |
| `Set-Cookie` | Respuesta | Pide al navegador que guarde una cookie | `set-cookie: logged_in=no; [...]` |

El `Basic` de `Authorization` es **base64**, una forma de escribir datos con letras que **no cifra**: `echo YWx1bW5vOkNBTUJJQVJfRVNUTw== | base64 -d` devuelve `alumno:CAMBIAR_ESTO`. Por eso la autenticación básica solo se usa con HTTPS. Si falta la autenticación, el servidor responde `401` con `WWW-Authenticate`.

Un **tipo MIME** dice qué es el contenido (`tipo/subtipo`) y viaja en `Content-Type`: `text/html`, `text/css`, `text/javascript`, `image/png`, `image/svg+xml`, `application/json`, `application/pdf` y `application/octet-stream` ("bytes sin tipo": el navegador lo descarga). nginx lo elige por la **extensión** con su tabla `mime.types`; si no la encuentra, usa `default_type`. Un tipo mal puesto hace que un CSS no se aplique o que un fichero se descargue en vez de mostrarse.

#### 6.2.12 Códigos de estado

La primera cifra da la familia: **1xx** información, **2xx** éxito, **3xx** redirección, **4xx** error del **cliente** ("la culpa es tuya"), **5xx** error del **servidor** ("la culpa es mía").

| Código | Nombre | Qué significa | Cuándo lo ves |
|---|---|---|---|
| 200 | OK | Todo bien | `curl -I` a una web que funciona |
| 201 | Created | Se ha **creado** un recurso | Un POST a una API que crea una tarea |
| 204 | No Content | Éxito, pero la respuesta **no trae cuerpo** | Un DELETE correcto en una API |
| 301 | Moved Permanently | Movido **para siempre**; destino en `Location` | `http` a `https`; carpeta sin barra final (`/markdown` a `/markdown/`) |
| 302 | Found | Movido **temporalmente** | Redirección provisional a la página de login |
| 304 | Not Modified | Tu copia en caché sigue valiendo; va sin cuerpo | El navegador pregunta con `If-None-Match` o `If-Modified-Since` |
| 400 | Bad Request | Petición mal formada | Falta `Host` en HTTP/1.1; cabeceras mal escritas |
| 401 | Unauthorized | **Falta autenticarse** (no sé quién eres) | Zona con usuario y contraseña; va con `WWW-Authenticate` |
| 403 | Forbidden | Sé lo que pides, pero **no te dejo** | Ficheros con `chmod 600`; carpeta sin índice |
| 404 | Not Found | No existe donde el servidor lo busca | URL mal escrita, `root` equivocado |
| 405 | Method Not Allowed | Ese método no se permite ahí | DELETE a una web que solo admite GET y HEAD (paso 4 del 6.3) |
| 500 | Internal Server Error | La aplicación ha fallado | Excepción en Python, error en el PHP |
| 502 | Bad Gateway | nginx no recibe respuesta válida del backend | Gunicorn o PHP-FPM parados; puerto o socket mal |
| 503 | Service Unavailable | El servicio no está disponible ahora | Sobrecarga o mantenimiento |
| 504 | Gateway Timeout | El backend existe pero **tarda demasiado** | Gunicorn bloqueado |

Parejas que se confunden: **401** (falta autenticación) y **403** (falta autorización); **301** (permanente) y **302** (temporal); **502** (el backend no contesta) y **504** (contesta tarde). Con un método inventado, nginx da 405 si está en mayúsculas (`-X BREW`: lo acepta como método desconocido y el contenido estático solo admite GET y HEAD) y 400 si lleva caracteres no válidos, como `-X brew` en minúsculas (no entiende la petición). Por eso la web lo resume como "400/405".

#### 6.2.13 Versiones de HTTP

| Versión | Año | Transporte | Lo que tienes que recordar |
|---|---|---|---|
| HTTP/0.9 | 1991 | TCP | Solo pedir un HTML. Sin cabeceras |
| HTTP/1.0 | 1996 | TCP | Aparecen las cabeceras y otros tipos de recurso. **Una conexión TCP nueva por cada petición** |
| HTTP/1.1 | 1997 | TCP | **Conexiones persistentes** (se reutilizan), **`Host` obligatoria**, negociación de contenido, *pipelining* |
| HTTP/2 | 2015 | TCP | Basado en **SPDY** (un protocolo experimental de Google). **Binario**, **multiplexación**, compresión de cabeceras; traía *server push* (ya retirado por los navegadores) |
| HTTP/3 | 2022 | **QUIC sobre UDP** | Sin **bloqueo de cabeza de línea**; conexión y TLS en un solo saludo; aguanta el cambio de Wi-Fi a datos |

- **Multiplexación**: muchas peticiones y respuestas viajan mezcladas a la vez por una sola conexión.
- **Bloqueo de cabeza de línea**: TCP entrega en orden; si se pierde un paquete, los de detrás esperan aunque hayan llegado. Como un peaje parado por el primer coche. HTTP/2 lo sufre porque todo va por una sola conexión TCP.
- **QUIC**: transporte sobre UDP con flujos independientes (si se pierde un paquete de una imagen, no se para el JavaScript). Se conecta en 1-RTT, o 0-RTT si ya habías estado; **RTT** es una ida y vuelta por la red.

#### 6.2.14 HTTPS y TLS

**HTTPS = HTTP sobre TLS**, por el puerto **443**. SSL era el protocolo anterior a TLS, hoy retirado, aunque se siga diciendo "certificado SSL". HTTP es una postal: cualquiera en el camino la lee. HTTPS es una carta en sobre cerrado, después de comprobar el DNI de quien la recibe.

TLS protege tres cosas: **confidencialidad** (nadie en medio lee los datos), **integridad** (nadie los cambia sin que se note) y **autenticidad del servidor** (el certificado demuestra que hablas con el real). No protege de los fallos de la aplicación ni oculta a qué IP te conectas.

- **Certificado**: documento que une un nombre de dominio con una **clave pública** y que firma una **autoridad de certificación (CA)** en la que confía el sistema. La **clave privada** solo la tiene el servidor. Un certificado **autofirmado** (sin CA) cifra igual, pero el cliente avisa de que no es de confianza.
- **Saludo** (*handshake*), simplificado y después de abrir TCP: el cliente manda *ClientHello* (versiones, cifrados y su parte de la clave); el servidor contesta con *ServerHello* (su parte de la clave) y su certificado; desde ahí todo va cifrado. TLS 1.3 lo hace en 1-RTT (TLS 1.2 necesitaba 2), o en 0-RTT si ya te habías conectado (más rápido, pero esos primeros datos se podrían reenviar en un ataque de repetición).
- TLS 1.3 solo admite cifrados modernos **AEAD** (cifran y comprueban la integridad a la vez) y obliga al **forward secrecy**: si un día roban la clave privada del servidor, las conversaciones pasadas siguen sin poder descifrarse.
- `curl -k`: sigue cifrando, pero **no comprueba el certificado**. Solo para pruebas. Contra un sitio de pruebas con certificado autofirmado, `curl -I https://self-signed.badssl.com/` falla con `curl: (60) SSL certificate problem: self signed certificate`, y `curl -kI https://self-signed.badssl.com/` responde `HTTP/1.1 200 OK` (salidas reales).

#### 6.2.15 Puertos que hay que saberse

| Puerto | Servicio | Nota |
|---|---|---|
| 21 | FTP | Transferencia de ficheros (UT5) |
| 22 | SSH | Conexión remota segura (las instancias de Oracle) |
| 53 | DNS | UDP y TCP |
| 80 | HTTP | |
| 443 | HTTPS | TCP; UDP con HTTP/3 |
| 3306 | MySQL y MariaDB | |
| 5432 | PostgreSQL | La web lo cita como `db:5432` |
| 8000 | Gunicorn en el curso | Costumbre, no estándar (en Linux, escuchar por debajo del 1024 exige ser administrador) |
| 8080 | HTTP alternativo | Calculadora dockerizada y mi práctica (`8080:80`) |
| 9000 | PHP-FPM por TCP | `fastcgi_pass php-fpm:9000` |

#### 6.2.16 curl: las opciones del examen

`curl` es un cliente HTTP de terminal: hace peticiones y te enseña lo que vuelve. Sin opciones hace un GET y muestra el cuerpo. Truco: **I mayúscula, solo cabeceras; i minúscula, cabeceras más cuerpo.**

| Opción | Qué hace |
|---|---|
| `-I` (`--head`) | Envía **HEAD**: solo línea de estado y cabeceras |
| `-i` (`--include`) | GET normal, muestra cabeceras **y** cuerpo |
| `-v` | Todo el diálogo: `*` conexión, `>` lo que envías, `<` lo que recibes |
| `-s` | Silencioso: quita la barra de progreso |
| `-o FICHERO` | Guarda el cuerpo en un fichero (`-o /dev/null` lo tira) |
| `-L` | Sigue las redirecciones 3xx |
| `-H "Host: docs.local"` | Añade o cambia una cabecera |
| `-X DELETE` | Cambia el método |
| `-k` | No comprueba el certificado |
| `-d "a=1&b=2"` | Envía datos de formulario por POST |
| `-u usuario:clave` | Autenticación básica |
| `-w "%{http_code}\n"` | Escribe datos de la respuesta, como el código |

Cuando curl ni siquiera recibe una respuesta HTTP, no hay código de estado: escribe un error con su número entre paréntesis. Hay que distinguir tres:

| Error de curl | Qué ha fallado | Salida real |
|---|---|---|
| `(6)` | El DNS: el nombre no existe o no se resuelve | `curl: (6) Could not resolve host: noexiste.invalid` |
| `(7)` | La conexión TCP: nadie escucha en ese puerto (nginx parado o puerto sin publicar) | `curl: (7) Failed to connect to localhost port 9 after 0 ms: Couldn't connect to server` |
| `(60)` | El certificado de HTTPS no es de confianza (se salta con `-k`) | `curl: (60) SSL certificate problem: self signed certificate` |

Un 404 o un 502, en cambio, sí son respuestas: el servidor contestó.

#### 6.2.17 Estructura de una aplicación web

- **Frontend**: lo que se ejecuta y se ve en el navegador: HTML (estructura), CSS (estilo) y JavaScript (interactividad). En la UT4, el *build* de Vite.
- **Backend**: el código que corre en el servidor (Python con Django o Flask, PHP): la lógica y el acceso a los datos.
- **Datos**: la información que dura (PostgreSQL, MySQL, ficheros).

| | Estático | Dinámico |
|---|---|---|
| Qué es | Ficheros que ya existen y se envían tal cual | Se genera en cada petición ejecutando código |
| Igual para todos | Sí | No |
| Quién lo sirve | nginx, directamente del disco | El servidor de aplicaciones (nginx hace de intermediario) |
| Ejemplos | `index.html`, `estilos.css`, imágenes, lo que generan Zensical y Jekyll | Resultado de la calculadora, carrito, JSON de una API |

Trampa: una web generada con Zensical es **estática** aunque tenga buscador. El índice de búsqueda (`search.json`) se fabrica en el build y la búsqueda la hace el JavaScript en el navegador.

#### 6.2.18 DocumentRoot: de la URL al fichero

El **DocumentRoot** (en nginx, la directiva `root`) es la carpeta desde la que se sirven los ficheros de un sitio. En el paquete de Ubuntu es `/var/www/html`; en la imagen oficial de Docker, `/usr/share/nginx/html`; en mi práctica, `/var/www/docs`, `/var/www/blog` y `/var/www/portada`. Regla: **fichero buscado = `root` + ruta de la URL**. La directiva `index` dice qué fichero servir al pedir una carpeta; por eso `http://servidor/` muestra `index.html`. Si cambias o añades un fichero dentro del DocumentRoot, nginx lo sirve en la siguiente petición sin recargar nada; la recarga (`nginx -s reload`) solo hace falta cuando cambias la **configuración**.

| Petición | Con `root /var/www/html;` busca | Resultado |
|---|---|---|
| `GET /index.html` | `/var/www/html/index.html` | 200 si existe y se puede leer |
| `GET /img/logo.png` | `/var/www/html/img/logo.png` | 200, o 404 si no existe |
| `GET /` | La carpeta y dentro el fichero de `index` (`index.html`) | 200 si hay índice; si no, 403 o 404 según la `location` |

#### 6.2.19 Permisos y quién sirve qué

Los procesos de nginx que atienden peticiones corren como **`www-data`** en Ubuntu (como **`nginx`** en la imagen oficial que usé) y necesitan **leer** los ficheros. Los permisos de Linux son tres cifras (propietario, grupo, otros) que suman lectura 4, escritura 2 y ejecución 1. En una carpeta, la `x` significa "poder entrar". Para publicar: **644** (`rw-r--r--`) en los **ficheros** y **755** (`rwxr-xr-x`) en las **carpetas**. Con **600** (`rw-------`) solo lee el propietario y nginx da **403**; **777** (todo para todos) no se usa **nunca**.

`chmod -R a+rX carpeta` da lectura a todos y la `X` mayúscula da "entrar" solo a las carpetas: un fichero `600` queda en `644` y una carpeta `700` en `755`.

Quién sirve qué: nginx entrega él mismo los estáticos (`/index.html`, `/estilos.css`) leyendo del disco; los `.php` se los pasa a PHP-FPM (`fastcgi_pass`) y, en la UT4, `/api/...` a Gunicorn con Django (`proxy_pass`), que es quien consulta la base de datos. Si el backend está parado, nginx responde **502**.

### 6.3 Manos a la obra

Todo se hace en la Terminal del Mac, solo necesitas Internet y no vas a crear ni borrar ningún fichero. Antes de empezar, `curl --version | head -1` debe escribir la versión de `curl` (la mía: `curl 8.7.1 (...)`). Si tu salida no cuadra en la fecha, en las IP o en números como `age`, es normal: cambian en cada petición.

**Paso 1. Línea de estado y cabeceras con `-I`**

```bash
curl -I https://www.example.org
```

Uso `www.example.org`, el dominio hermano de `example.com` reservado para ejemplos, porque en mi red `example.com` cortaba la conexión (lo analizas en P8). Salida real:

```text
HTTP/2 200
date: Sun, 01 Nov 2026 16:22:45 GMT
content-type: text/html; charset=utf-8
server: cloudflare
last-modified: Thu, 29 Oct 2026 13:15:03 GMT
allow: GET, HEAD
accept-ranges: bytes
age: 3591
cache-control: max-age=14400
cf-cache-status: HIT
cf-ray: a53c3d76f9d4ec92-MAD
alt-svc: h3=":443"; ma=86400
```

Léela así:

- `HTTP/2 200`: versión 2 y código 200. Sin "OK" porque HTTP/2 no manda frase.
- `content-type`: el tipo MIME, una página HTML en UTF-8.
- `server: cloudflare` y `cf-cache-status: HIT`: te ha respondido un **CDN** desde su caché, no el servidor de origen. `age` son los segundos que lleva guardada (3591 s, casi una hora) y `max-age=14400` el máximo (4 horas).
- `allow: GET, HEAD`: los únicos métodos que admite (lo usarás en el paso 4).
- `alt-svc: h3=":443"; ma=86400`: anuncia que también habla HTTP/3 (QUIC sobre UDP) en el 443, y el anuncio vale un día.

**Paso 2. Las fases de la conexión con `-v`**

```bash
curl -v https://www.example.org -o /dev/null
```

Verás mezcladas unas líneas `% Total % Received...`: es la barra de progreso (con `-sv` desaparece). Salida real, sin la barra y recortada:

```text
* Host www.example.org:443 was resolved.
* IPv6: (none)
* IPv4: 172.66.157.237, 104.20.26.136
*   Trying 172.66.157.237:443...
* Connected to www.example.org (172.66.157.237) port 443
* ALPN: curl offers h2,http/1.1
* (304) (OUT), TLS handshake, Client hello (1):
[...]
* (304) (IN), TLS handshake, Server hello (2):
[...]
* (304) (IN), TLS handshake, Certificate (11):
[...]
* SSL connection using TLSv1.3 / AEAD-CHACHA20-POLY1305-SHA256 / [blank] / UNDEF
* ALPN: server accepted h2
* Server certificate:
*  subject: CN=example.org
[...]
*  issuer: C=US; O=SSL Corporation; CN=Cloudflare TLS Issuing ECC CA 3
*  SSL certificate verify ok.
[...]
```

Después vienen la petición (`> GET / HTTP/2`) y la respuesta (`< HTTP/2 200`), como en el 6.2.9, y `{ [577 bytes data]`: el cuerpo llegó, pero `-o /dev/null` lo tiró. Localiza cada fase:

| Fase | Línea que la delata |
|---|---|
| DNS | `Host www.example.org:443 was resolved` y la lista `IPv4:` |
| Conexión TCP | `Trying ...` y `Connected to ... port 443` |
| TLS | `Client hello`, `Server hello`, `Certificate` y `SSL connection using TLSv1.3` (con `AEAD-CHACHA20-POLY1305`, un cifrado AEAD del 6.2.14) |
| Certificado | `subject` (para quién es), `issuer` (la CA que lo firma), `SSL certificate verify ok` |
| Versión de HTTP | `ALPN: server accepted h2`: dentro del saludo TLS acuerdan usar HTTP/2 (ALPN es esa negociación) |

**Paso 3. Redirección 301 y `Location`**

Pide las cabeceras de `http://github.com`, sigue la redirección con `-L` y filtra las líneas importantes:

```bash
curl -sIL http://github.com | grep -iE "^(HTTP|location)"
curl -s -o /dev/null -w "%{http_code} %{num_redirects} %{url_effective}\n" -L http://github.com
```

```text
HTTP/1.1 301 Moved Permanently
Location: https://github.com/
HTTP/2 200
200 1 https://github.com/
```

`curl` hizo dos peticiones: la primera da **301** (GitHub te manda de `http` a `https` para siempre) y `-L` repite la petición en la dirección de `Location`, que ya da 200. Hubo 1 redirección. Sin `-L` verías solo el 301 con su `Location` (la web del curso hace lo mismo: `curl -sI http://dpl-f1facc.gitlab.io/` da 301 y `location: https://dpl-f1facc.gitlab.io/`). La primera respuesta es HTTP/1.1 porque va por `http`, sin TLS; HTTP/2 se acuerda dentro del saludo TLS (ALPN), así que solo aparece en la segunda.

**Paso 4. Un 404 y un 405**

```bash
curl -s -o /dev/null -w "%{http_code}\n" https://dpl-f1facc.gitlab.io/no-existe
curl -s -o /dev/null -w "%{http_code}\n" -X DELETE https://www.example.org/
curl -s -o /dev/null -w "%{http_code}\n" -X OPTIONS https://www.example.org/
curl -sI https://www.example.org | grep -i "^allow"
```

```text
404
405
405
allow: GET, HEAD
```

- **404**: el servidor funciona y contesta; lo que no existe es el recurso. Un 404 no es "el servidor está caído".
- **405**: el servidor solo admite GET y HEAD (lo dice `allow`), así que rechaza DELETE antes de hacer nada: no has borrado nada. OPTIONS también da 405: aunque sirve para preguntar los métodos, cada servidor decide si lo atiende. Prueba estos métodos solo contra dominios de ejemplo como este.

La cabecera `Host` (varias webs en la misma IP y el mismo puerto) la pruebas el jueves con mi práctica, en el paso 3 del 7.3. Hoy no hay nada que limpiar.

### 6.4 Comprueba que lo sabes

**Reconocer (tipo test)**

**P1.** Una API recibe `POST /api/tareas` y crea la tarea sin problemas. ¿Qué código es el más adecuado?

- a) 200 OK
- b) 201 Created
- c) 204 No Content
- d) 302 Found

<details>
<summary>Respuesta</summary>

**b)**. 201 dice exactamente "he creado un recurso" (suele ir con `Location` apuntando al nuevo). 200 es un éxito genérico, 204 es éxito sin cuerpo y 302 es una redirección temporal.

</details>

**P2.** ¿Qué método es idempotente pero **no** seguro?

- a) GET
- b) HEAD
- c) POST
- d) DELETE

<details>
<summary>Respuesta</summary>

**d)**. DELETE cambia el servidor (no es seguro), pero borrar lo ya borrado lo deja igual (es idempotente). GET y HEAD son seguros e idempotentes; POST no es ninguna de las dos cosas.

</details>

**P3.** En `https://blog.local:8080/2026/10/?orden=fecha#comentarios`, ¿qué parte **no** llega al servidor?

- a) `blog.local`
- b) `8080`
- c) `?orden=fecha`
- d) `#comentarios`

<details>
<summary>Respuesta</summary>

**d)**. El fragmento lo usa solo el navegador para saltar a una parte de la página. El host y el puerto viajan en la cabecera `Host` (`Host: blog.local:8080`), y el puerto además decide a dónde se conecta; la consulta va en la línea de petición (`GET /2026/10/?orden=fecha HTTP/1.1`).

</details>

**P4.** ¿Quién firma un certificado para que el navegador confíe en él sin avisar?

- a) El propio servidor web
- b) Una autoridad de certificación (CA)
- c) El servidor DNS
- d) El navegador al conectarse

<details>
<summary>Respuesta</summary>

**b)**. Si lo firma el propio servidor (a) es autofirmado: cifra igual, pero el navegador avisa y `curl` da el error 60 salvo que uses `-k`.

</details>

**Respuesta corta o comando**

**P5.** Escribe la petición completa (línea de petición, cabeceras, línea en blanco y cuerpo) que envía `curl -d "nombre=Ana&curso=2DAM" http://www.alumno.local/registro`.

<details>
<summary>Respuesta</summary>

```text
POST /registro HTTP/1.1
Host: www.alumno.local
User-Agent: curl/8.7.1
Accept: */*
Content-Length: 21
Content-Type: application/x-www-form-urlencoded

nombre=Ana&curso=2DAM
```

Lo que tiene que estar: POST (por `-d`), `Host` sin puerto (es el 80), el tipo de formulario en `Content-Type`, 21 bytes en `Content-Length`, la línea en blanco y el cuerpo.

</details>

**P6.** Completa: SSH ___, DNS ___, HTTPS ___, MySQL ___, PostgreSQL ___, PHP-FPM por TCP en el curso ___.

<details>
<summary>Respuesta</summary>

22, 53, 443, 3306, 5432 y 9000.

</details>

**P7.** Escribe el comando que deja `/var/www/tienda` con lectura para todos y permiso de entrar solo en las carpetas. ¿En qué se convierten un fichero `600` y una carpeta `700`?

<details>
<summary>Respuesta</summary>

```bash
chmod -R a+rX /var/www/tienda
```

El fichero queda en `644` (`rw-r--r--`) y la carpeta en `755` (`rwxr-xr-x`). La `X` mayúscula solo pone la `x` a las carpetas (y a lo que ya era ejecutable).

</details>

**Razonar o interpretar**

**P8.** En mi red, esto pasó con `example.com` (salida real, recortada):

```text
$ curl -v https://example.com -o /dev/null
* Host example.com:443 was resolved.
* IPv6: (none)
* IPv4: 172.66.147.243, 104.20.23.154
*   Trying 172.66.147.243:443...
* Connected to example.com (172.66.147.243) port 443
* ALPN: curl offers h2,http/1.1
* (304) (OUT), TLS handshake, Client hello (1):
[...]
* Recv failure: Connection reset by peer
[...]
curl: (35) Recv failure: Connection reset by peer
```

¿Funcionó el DNS? ¿Y la conexión TCP? ¿En qué fase se cortó? ¿Llegó a enviarse el GET? ¿Hay código de estado?

<details>
<summary>Respuesta</summary>

- DNS: sí, hay IP (`IPv4: ...`).
- TCP: sí, `Connected to ... port 443`.
- Se cortó en **TLS**, justo después de enviar el *ClientHello*: alguien (el servidor o algo de la red por el camino) cerró la conexión de golpe (*reset*).
- El GET **no** se envió: no hay ninguna línea `>`.
- No hay código de estado porque no hay ninguna línea `<`. No es un 4xx ni un 5xx: es un fallo **antes** de HTTP.

Moraleja: con `-v` sabes en qué capa mirar. Con `www.example.org`, en la misma red, todo fue bien.

</details>

**P9.** Una academia te pide: (1) una web informativa que cambia una vez al mes, la mantiene un profesor con Markdown y Git, y no hay presupuesto; (2) una aplicación de notas cuyos datos, por norma interna, no pueden salir del centro. Elige alternativa de implantación y número de capas para cada una, y justifica.

<details>
<summary>Respuesta</summary>

- (1) **Hosting estático** (GitHub Pages) con un generador como Zensical: es JAMstack, gratis, con CDN y HTTPS, y despliega desde Git. **Dos capas**: no hay lógica ni datos, solo ficheros.
- (2) **On-premise** (los datos se quedan en casa) y **tres capas**: nginx (presentación), servidor de aplicaciones (lógica) y base de datos (datos), con la base de datos sin salida a Internet. Requisitos: máquina dedicada con Linux, disco para la base de datos, logs y copias, IP fija (o DDNS) si se entra desde fuera, y HTTPS porque hay datos personales.

</details>

**P10.** Montas nginx en un ordenador de casa (IP `192.168.1.50`). Abres el puerto 80 en el router y le das a un amigo tu IP pública: le funciona. Una semana después, sin tocar nada, a él le sale `Failed to connect`, pero desde tu Wi-Fi `curl -I http://192.168.1.50/` sigue dando 200. ¿Qué requisito falla y cómo se arregla sin pagar? ¿Por qué no le vale a tu amigo `192.168.1.50`?

<details>
<summary>Respuesta</summary>

- El servidor está bien (te da 200). Falla la **IP estática**: tu operador te ha cambiado la IP pública y tu amigo sigue usando la antigua.
- Sin pagar una IP fija: **DDNS** (por ejemplo Duck DNS). Le das un nombre y el servicio lo actualiza solo cuando cambia tu IP.
- `192.168.1.50` es una IP **privada**: solo existe dentro de tu red de casa. Desde fuera se entra por la IP pública del router, que reenvía el 80 a tu ordenador.

</details>

### 6.5 Si te atascas

- Vocabulario, capas, dos y tres capas, servidores, API y fases del proyecto: [06, apartado 0](06-ut2-arquitecturas-servidores-web.md) y [06, apartado 2.3](06-ut2-arquitecturas-servidores-web.md) a [06, apartado 2.8](06-ut2-arquitecturas-servidores-web.md).
- Alternativas, CDN, JAMstack y requisitos: [06, apartado 2.9](06-ut2-arquitecturas-servidores-web.md) a [06, apartado 2.11](06-ut2-arquitecturas-servidores-web.md). La nube y IaaS, PaaS y SaaS: [08, apartado «Vocabulario»](08-oracle-cloud-instancias.md).
- HTTP (petición, respuesta, métodos, cabeceras, MIME, códigos y versiones): [06, apartado 3.3](06-ut2-arquitecturas-servidores-web.md) a [06, apartado 3.9](06-ut2-arquitecturas-servidores-web.md).
- HTTPS, TLS, puertos y `curl`: [06, apartado 3.10](06-ut2-arquitecturas-servidores-web.md) a [06, apartado 3.12](06-ut2-arquitecturas-servidores-web.md).
- Estático y dinámico, DocumentRoot y permisos: [06, apartado 4.2](06-ut2-arquitecturas-servidores-web.md), [06, apartado 4.4](06-ut2-arquitecturas-servidores-web.md) y [06, apartado 4.5](06-ut2-arquitecturas-servidores-web.md).
- Cabecera `Host` en mi práctica: [04, apartado 2.6](04-practica-nginx.md). Puertos publicados con Docker (`-p`): [05, apartado 8](05-ut1-git-documentacion-cicd.md).
- Diagnosticar por capas y fabricar errores (404, 403, 405): [06, apartado 8.1](06-ut2-arquitecturas-servidores-web.md) y [06, apartado 8.5](06-ut2-arquitecturas-servidores-web.md).
- Más preguntas de estos CE: [07, apartado 4.6](07-plan-de-repaso-p1.md) a [07, apartado 4.8](07-plan-de-repaso-p1.md). Mapa de CE: [07, apartado 2](07-plan-de-repaso-p1.md).
- En la web del curso: [Arquitecturas Web](https://dpl-f1facc.gitlab.io/ut02/teoria/arquitecturas-web/), [HTTP y HTTPS](https://dpl-f1facc.gitlab.io/ut02/teoria/http-https/), [Estructura de una aplicación Web](https://dpl-f1facc.gitlab.io/ut02/teoria/estructura-app-web/), [Cloud](https://dpl-f1facc.gitlab.io/ut02/teoria/cloud/), [Red, logs y diagnóstico](https://dpl-f1facc.gitlab.io/ut02/practicas/guiada-17-red-logs/), el [glosario](https://dpl-f1facc.gitlab.io/recursos/glosario/) y los [comandos](https://dpl-f1facc.gitlab.io/recursos/comandos/).

## 7. Jueves 5/11: nginx, servidores de aplicaciones, Docker y nube

Al acabar el día sabrás leer y escribir una configuración de nginx, explicar cómo coopera con Gunicorn y con PHP-FPM, manejar contenedores con Docker Compose, situar la nube (IaaS, PaaS, SaaS, AWS y Terraform) y demostrar con comandos que todo funciona.
Es la parte práctica del RA1: casi todas las preguntas de "qué hace este comando" o "qué sale aquí" salen de este día. Cubre los criterios de evaluación **RA1-c** (servidor web), **RA1-d** (servidores de aplicaciones), **RA1-e** (contenedores y nube), **RA1-f** (pruebas) y **RA1-i** (documentación).

Ojo con el alcance: la web del curso deja los tipos de `location`, `alias`, las redirecciones y los server blocks para "Administración avanzada de nginx" y la UT3. Van aquí porque mi práctica los usa y pueden salir al leer una configuración, pero lo seguro del P1 es lo básico: procesos, rutas, `nginx -t`, recarga, logs, proxy inverso, contenedores y nube.

### 7.1 Plan del día

| Bloque | Qué haces | Tiempo |
|---|---|---|
| 0 | Registro de fallos: contesta las filas sin marcar del registro (apartado 11), las del miércoles y las que sigan pendientes | 10 min |
| 1 | Leer "Lo imprescindible" (7.2) con papel al lado: copia a mano las tablas de `location`, de errores y de IaaS/PaaS/SaaS | 45 min |
| 2 | "Manos a la obra" (7.3) con tu práctica `nginx-para-todos` | 40 min |
| 3 | "Comprueba que lo sabes" (7.4): 15 preguntas sin mirar, y después corriges | 30 min |
| 4 | Apunta cada fallo en el registro (apartado 11) y relee su punto de 7.2 | 10 min |
| | **Total**, con un descanso de 5 min después de los bloques 1, 2 y 3 | **2 h 30 min** |

### 7.2 Lo imprescindible

#### 7.2.1 nginx: qué es, master y workers

**nginx** (se dice "engine-x") es un **servidor web**: un programa que espera peticiones HTTP y responde con ficheros. Hace cuatro trabajos: servir **contenido estático** (ficheros ya hechos: HTML, CSS, imágenes), hacer de **proxy inverso** (pasar la petición a otro programa que está detrás), **caché** (guardar respuestas para no volver a pedirlas) y **balanceo de carga** (repartir peticiones entre varios servidores, con el bloque `upstream`).

Al arrancar crea **un proceso master** y **varios procesos worker** (un **proceso** es un programa en ejecución).

- **Master**: lee y comprueba la configuración, abre los puertos y vigila a los workers. Corre como `root`, porque en Linux solo `root` puede abrir puertos por debajo del 1024, como el 80.
- **Workers**: atienden las peticiones. Corren con el usuario de la directiva `user`, sin privilegios: `www-data` en Ubuntu, `nginx` en la imagen oficial de Docker y en nginx.org. Ese usuario es el que necesita permiso de lectura sobre la web.
- Es **orientado a eventos**: cada worker lleva muchas conexiones a la vez sin quedarse esperando a ninguna. Analogía: el master es el encargado del restaurante; los workers, camareros que llevan muchas mesas a la vez.

`worker_processes auto;` pone un worker por núcleo de CPU y `worker_connections 768;` (va dentro de `events`) son las conexiones de **cada** worker. Máximo aproximado de clientes: `worker_processes × worker_connections` (con 4 núcleos, 4 × 768 = 3072).

#### 7.2.2 nginx frente a Apache

| | Apache | nginx |
|---|---|---|
| Cómo atiende | Un proceso o un hilo por conexión (módulos MPM) | Eventos: pocos workers para muchas conexiones |
| Estático | Bueno | Excelente, con pocos recursos |
| Dinámico | Nativo, con módulos (PHP dentro de Apache) | Necesita un servicio externo (Gunicorn, PHP-FPM) |
| Consumo con mucha carga | Mayor | Menor |
| Configuración | Permite `.htaccess` en cada carpeta | Centralizada en `/etc/nginx/` |

No son enemigos: es habitual poner nginx delante (estáticos, HTTPS, caché) y Apache detrás.

#### 7.2.3 Dónde está cada cosa

| Ruta | Qué hay |
|---|---|
| `/etc/nginx/nginx.conf` | Configuración principal. Incluye las demás con `include` |
| `/etc/nginx/conf.d/*.conf` | Fragmentos. En la imagen oficial y en nginx.org, cada sitio va aquí (mi práctica) |
| `/etc/nginx/sites-available/` | Solo Debian/Ubuntu: un fichero por sitio, escrito pero no activo |
| `/etc/nginx/sites-enabled/` | Solo Debian/Ubuntu: **enlaces simbólicos** (accesos directos) a los sitios activos |
| `/var/log/nginx/access.log` y `error.log` | `access.log`: una línea por cada petición atendida. `error.log`: solo los problemas (permisos, configuración, backend caído) |
| `/usr/share/nginx/html` | DocumentRoot por defecto de nginx.org y de la imagen oficial |
| `/var/www/html` | DocumentRoot del sitio `default` del paquete de Ubuntu (`dpl-lab`) |

El **DocumentRoot** es la carpeta raíz de la web: de ahí salen los ficheros que se piden. Si un sitio no declara `root`, nginx usa uno por defecto que sale del **`--prefix`**, la carpeta base que se fijó al compilar el programa (en nginx.org, `/etc/nginx`); los paquetes de Ubuntu, en cambio, declaran `root /var/www/html;` en su sitio `default`. `nginx -v` enseña solo la versión y `nginx -V` (mayúscula), además, las opciones con las que se compiló, `--prefix` incluido. En el contexto main, `pid /run/nginx.pid;` es el fichero donde nginx apunta el número de proceso (PID) del master: lo leen `nginx -s reload` y `nginx -s stop` para saber a quién avisar. Para activar un sitio en Ubuntu: `ln -s /etc/nginx/sites-available/calculadora /etc/nginx/sites-enabled/`, y después `nginx -t` y recargar. Para desactivarlo se borra el enlace, no el fichero.

#### 7.2.4 La configuración: directivas, bloques y contextos

- **Directiva simple**: nombre, valores y **`;` al final**. Ejemplo: `root /var/www/docs;` (lo que va detrás de `#` es un comentario).
- **Directiva de bloque**: nombre y llaves `{ }`. Si dentro lleva directivas, se llama **contexto**. **Herencia**: lo que pones en un contexto de fuera vale para los de dentro, salvo que lo redefinan.

| Contexto | Dónde va | Para qué |
|---|---|---|
| main | Fuera de todo bloque | Ajustes del proceso: `user`, `worker_processes`, `error_log`, `pid` |
| `events { }` | En main | Conexiones: `worker_connections` |
| `http { }` | En main | Todo lo de HTTP: tipos MIME, logs y los sitios |
| `server { }` | En `http` | Un sitio web (*server block* o *virtual host*) |
| `location { }` | En `server` | Qué hacer con un grupo de URL |

#### 7.2.5 Directivas clave

| Directiva | Qué hace | Ejemplo |
|---|---|---|
| `listen` | Puerto (e IP) del sitio; `default_server` lo hace sitio por defecto de ese puerto | `listen 80 default_server;` |
| `server_name` | Nombres del sitio; se comparan con la cabecera `Host` | `server_name docs.local;` |
| `root` | Carpeta raíz: fichero = `root` + URI | `root /var/www/docs;` |
| `index` | Fichero que se sirve al pedir una carpeta | `index index.html;` |
| `location` | Agrupa URL por patrón | `location / { ... }` |
| `try_files` | Prueba rutas en orden; si ninguna existe, hace lo último | `try_files $uri $uri/ =404;` |
| `error_page` | Página propia para un código de error | `error_page 404 /404.html;` |
| `return` | Responde ya con un código (y una URL si es redirección) | `return 301 https://$host$request_uri;` |
| `include` | Mete el contenido de otro fichero | `include /etc/nginx/conf.d/*.conf;` |
| `access_log` / `error_log` | Ficheros de log (pueden ser propios de cada sitio) | `access_log /var/log/nginx/docs.access.log;` |

`try_files $uri $uri/ =404;` se lee: "¿existe un **fichero** con esa ruta? Si no, ¿existe una **carpeta**? Si no, 404". `$uri` es una **variable** de nginx (un valor que nginx rellena en cada petición): la ruta pedida sin lo que va detrás de `?`. Otras: `$host` (nombre pedido), `$remote_addr` (IP del cliente), `$request_uri` (ruta con la consulta), `$document_root` (el `root` actual).

#### 7.2.6 root frente a alias

Petición `/fotos/playa.jpg`:

| Configuración | Fichero que busca | Regla |
|---|---|---|
| `location /fotos/ { root /srv/web; }` | `/srv/web/fotos/playa.jpg` | `root` **añade** la URI entera |
| `location /fotos/ { alias /srv/imagenes/; }` | `/srv/imagenes/playa.jpg` | `alias` **sustituye** `/fotos/` por la carpeta |

#### 7.2.7 Tipos de location y cuál gana

Una **expresión regular** (*regex*) es un patrón de texto: `\.php$` significa "termina en `.php`".

| Forma | Nombre | Coincide con |
|---|---|---|
| `location = /ruta` | Exacta | Solo esa URI. Si coincide, se para la búsqueda |
| `location ^~ /ruta` | Prefijo preferente | URIs que empiezan así; si es el prefijo más largo, no se miran las regex |
| `location ~ regex` | Regex | Distingue mayúsculas y minúsculas |
| `location ~* regex` | Regex | No las distingue |
| `location /ruta` | Prefijo | URIs que empiezan así |

Orden en que gana: **1)** la exacta `=`; **2)** nginx busca el prefijo más largo y lo recuerda; si lleva `^~`, gana él; **3)** si no, prueba las regex en el orden del fichero y gana **la primera** que coincida; **4)** si ninguna coincide, gana el prefijo recordado. `location /` coincide con todo, pero es el prefijo más corto: es el "todo lo demás".

#### 7.2.8 Cómo elige nginx el server block

Analogía: nginx es un recepcionista que mira el nombre escrito en el sobre (la cabecera **`Host`**, que el navegador manda con el nombre que escribiste).

1. Se queda con los `server` cuyo `listen` coincide con la IP y el puerto por los que entró la conexión.
2. Compara `Host` (sin el puerto) con los `server_name`: nombre exacto, luego comodín `*.algo`, luego `algo.*`, luego la primera regex.
3. Si nadie coincide, responde el **servidor por defecto** del puerto: el que tiene `default_server` o, si nadie lo tiene, el primero que nginx leyó (`include conf.d/*.conf` los lee en orden alfabético).

En mi práctica los tres bloques escuchan en el 80 del contenedor:

| Petición | Responde | Por qué |
|---|---|---|
| `curl -H "Host: docs.local" http://127.0.0.1:8080/` | `docs.conf` | Nombre exacto |
| `curl -H "Host: blog.local" http://127.0.0.1:8080/` | `blog.conf` | Nombre exacto |
| `curl -H "Host: otro.local" http://127.0.0.1:8080/` o `http://localhost:8080/` | `default.conf` (portada) | No coincide nadie: `listen 80 default_server;` |

`server_name _;` no es mágico: `_` es un nombre que nunca coincide. Lo que hace a un sitio "por defecto" es `default_server`. Con dos `default_server` en el mismo puerto, `nginx -t` falla con `a duplicate default server for 0.0.0.0:80`.

#### 7.2.9 Comandos para comprobar y recargar

| Comando | Qué hace |
|---|---|
| `nginx -t` | Comprueba la sintaxis. Dice `syntax is ok` y `test is successful`, o el fichero y la línea del error |
| `nginx -T` | Igual que `-t` y además imprime toda la configuración junta |
| `nginx -s reload` | Avisa al master para releer la configuración **sin cortar** conexiones. Si la nueva tiene errores, sigue con la vieja |
| `nginx -g 'daemon off;'` | Arranca en primer plano: así se lanza en `dpl-lab`, que no tiene systemd |
| `nginx -s stop` / `nginx -s quit` | Paran nginx. La web del curso dice que `stop` lo detiene "de forma ordenada"; la documentación oficial de nginx lo matiza: `quit` es la parada ordenada (espera a que acaben las peticiones en curso) y `stop`, la rápida. En el examen, la versión de la web y, si hay sitio, el matiz |
| `systemctl status nginx` | En un servidor real con **systemd** (el gestor de servicios de Linux): ¿está `active (running)`? |
| `systemctl reload nginx` / `restart nginx` | `reload` relee la configuración sin cortar; `restart` para y vuelve a arrancar, y corta las conexiones en curso |
| `docker compose exec nginx nginx -t` | En mi práctica: `nginx -t` dentro del servicio `nginx` (el primer `nginx` es el servicio; el segundo, el programa) |

Ciclo de trabajo **siempre**: editar, `nginx -t`, `nginx -s reload`, comprobar con `curl -I`.

#### 7.2.10 Leer una línea del access.log

Línea real de mi práctica (formato *combined*, el de por defecto):

```text
192.168.65.1 - - [18/Oct/2026:20:51:23 +0000] "GET / HTTP/1.1" 200 4149 "-" "curl/8.7.1"
```

Por orden: **IP del cliente** (`192.168.65.1`, la red interna de Docker Desktop por la que llegan las peticiones del Mac); `- -` (el primero sale siempre así y el segundo es el **usuario autenticado**, `-` si no hay); **fecha y hora**; **método, ruta y versión** de HTTP; **código de estado** (`200`); **bytes del cuerpo** enviados (`4149`; con `HEAD` sale `0`, porque solo van cabeceras); **Referer**, la página desde la que se llegó (`"-"`: ninguna); y **User-Agent**, el programa cliente (`"curl/8.7.1"`).

#### 7.2.11 Servidores de aplicaciones y proxy inverso

nginx **no ejecuta** Python ni PHP: solo entrega ficheros. Para lo **dinámico** (páginas que se calculan en cada petición) hace falta un **servidor de aplicaciones**: un programa que tiene la aplicación cargada, ejecuta el código y devuelve el resultado.

Un **proxy inverso** es un intermediario del lado del servidor: recibe la petición del cliente y la reenvía a un servicio interno. El cliente solo ve a nginx. Analogía: el camarero (nginx) no cocina; lleva el pedido a la cocina (Gunicorn o PHP-FPM) y te trae el plato. Ventajas: oculta lo de dentro (el backend, el programa que hay detrás, escucha en `127.0.0.1` o en una red privada), protege a la aplicación, sirve él los estáticos y centraliza HTTPS, caché y balanceo.

**Balanceo de carga.** Un **balanceador de carga** reparte las peticiones entre varios backends iguales. En nginx se declara el grupo con `upstream` (en el contexto `http`) y el `proxy_pass` apunta a su nombre:

```nginx
upstream aplicacion {
    least_conn;                          # al que tenga menos conexiones activas
    server 10.0.0.11:8000;
    server 10.0.0.12:8000;
    server 10.0.0.13:8000 backup;        # solo recibe tráfico si caen los otros
}

server {
    listen 80;
    location / {
        proxy_pass http://aplicacion;    # el nombre del upstream, no una IP
    }
}
```

- Reparto por defecto: **round-robin** (por turnos). Otros: `least_conn` (menos conexiones activas), `ip_hash` (la misma IP va siempre al mismo servidor, útil para sesiones) y `weight` (pesos: un servidor con `weight=3` recibe el triple que uno sin `weight`, que por defecto vale 1).
- **Failover**: si un servidor no responde, nginx deja de mandarle tráfico durante un tiempo.

**Caché de proxy.** nginx puede guardar copias de las respuestas del backend y servirlas él si se vuelven a pedir: menos carga para la aplicación y respuestas más rápidas. Se configura con `proxy_cache_path` (la zona de caché en disco, en `http`) y `proxy_cache` (en la `location`); las cabeceras `Cache-Control` y `Expires` del backend dicen qué se puede guardar y cuánto tiempo.

#### 7.2.12 Gunicorn (stack Python)

- **WSGI** (*Web Server Gateway Interface*): el estándar de Python que dice cómo un servidor llama a una aplicación web (Flask, Django).
- **Gunicorn**: servidor WSGI de producción. Un maestro y varios workers, como nginx. Si no le dices dónde escuchar, usa `127.0.0.1:8000`. En cambio, `flask run` es el servidor de **desarrollo**: el propio Flask avisa de que no se use en producción.

```bash
gunicorn -w 2 -b 127.0.0.1:8000 app:app
```

`-w 2` (`--workers`): dos procesos worker. `-b` (`--bind`): dónde escucha; `127.0.0.1` es solo la propia máquina y `0.0.0.0` todas sus interfaces de red (hace falta en Compose, porque nginx está en **otro** contenedor). `app:app`: módulo `app.py` y, dentro, el objeto `app = Flask(__name__)`. En el curso se instala en un **entorno virtual** (`.venv`, una carpeta con su propio Python y sus librerías) y se lanza como `.venv/bin/gunicorn`, porque Ubuntu 24.04 bloquea `pip install` fuera de él (política PEP 668, error `externally-managed-environment`).

```nginx
location / {
    proxy_pass http://127.0.0.1:8000;                               # a dónde reenvía (HTTP)
    proxy_set_header Host $host;                                    # nombre que pidió el cliente
    proxy_set_header X-Real-IP $remote_addr;                        # IP del cliente original
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;    # cadena de IP por las que pasó
}
```

El ejemplo del curso añade `proxy_set_header X-Forwarded-Proto $scheme;` (si el cliente entró por `http` o por `https`). Sin `Host`, la aplicación cree que le pidieron `127.0.0.1:8000`; sin `X-Real-IP` ni `X-Forwarded-For`, cree que el cliente es nginx.

| Comando o dato de Gunicorn | Para qué |
|---|---|
| Cuántos workers | Orientación de producción: **2 × núcleos + 1**. En el laboratorio, 1 o 2 bastan |
| `gunicorn --check-config app:app` | Comprueba que la aplicación se puede cargar, sin arrancar el servidor |
| `--access-logfile -` y `--error-logfile -` | Escriben los logs en la salida estándar (el `-`), que luego se redirige a un fichero o se lee con `docker compose logs` |
| `ps aux \| grep gunicorn` | Debe haber un maestro y tantos workers como pediste |
| `pkill -f gunicorn` | Lo para (sin systemd no hay `systemctl stop`) |

| Error de Gunicorn | Causa | Solución |
|---|---|---|
| `ModuleNotFoundError: No module named 'flask'` | Lo lanzaste con el Python del sistema, no con el del entorno virtual | Usa la ruta `.venv/bin/gunicorn` |
| `Connection in use: ('127.0.0.1', 8000)` | El puerto 8000 ya está ocupado, normalmente por un Gunicorn anterior | `pkill -f gunicorn` y vuelve a lanzarlo |
| `Failed to find attribute 'app' in 'app'.` | Carpeta de trabajo equivocada o nombre de módulo u objeto distinto | Lánzalo desde la carpeta de `app.py` con el nombre real |

#### 7.2.13 PHP-FPM (stack PHP)

- **FastCGI**: protocolo para que el servidor web pase la ejecución a procesos externos **ya arrancados**, en vez de lanzar el intérprete en cada petición. **PHP-FPM** (*FastCGI Process Manager*) mantiene esos procesos PHP listos y ejecuta los scripts.
- **Pool**: grupo de procesos con su configuración. El de Ubuntu se llama `www` (`/etc/php/8.3/fpm/pool.d/www.conf`): usuario `www-data`, dónde escucha (`listen`) y cuántos procesos como máximo (`pm.max_children`). Sin systemd se arranca en primer plano: `php-fpm8.3 -F`.
- Dónde escucha: **socket UNIX** `/run/php/php8.3-fpm.sock` (un fichero especial; solo sirve en la misma máquina y rinde algo mejor) o **TCP** `127.0.0.1:9000` (IP y puerto; sirve entre máquinas o contenedores, como `php-fpm:9000` en Compose).

```nginx
location ~ \.php$ {                                                    # URIs que terminan en .php
    include fastcgi_params;                                            # parámetros FastCGI estándar
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;  # qué fichero ejecutar
    fastcgi_pass unix:/run/php/php8.3-fpm.sock;                        # o 127.0.0.1:9000
}
```

`fastcgi_params` **no** trae `SCRIPT_FILENAME`: por eso se añade a mano. En Ubuntu, `include snippets/fastcgi-php.conf;` ya lo incluye. Sin la `location ~ \.php$`, el navegador **descarga** el `.php` en vez de ejecutarlo.

Comprobar PHP-FPM: `php-fpm8.3 -t` valida su configuración (como `nginx -t`), `ps aux | grep php-fpm` enseña el maestro y los procesos del pool y su log está en `/var/log/php8.3-fpm.log`. Si el `error.log` de nginx dice `connect() to unix:... failed (13: Permission denied)`, el usuario de nginx no puede usar el socket: se arregla en el pool con `listen.owner` y `listen.group` (en Ubuntu, `www-data`) y `listen.mode = 0660`.

| | Gunicorn | PHP-FPM |
|---|---|---|
| Lenguaje | Python (Flask, Django) | PHP |
| Estándar | WSGI | FastCGI |
| Directiva de nginx | `proxy_pass` | `fastcgi_pass` |
| Dirección nativa | `127.0.0.1:8000` | `unix:/run/php/php8.3-fpm.sock` |
| Dirección en Compose | `http://app:8000` | `php-fpm:9000` |
| Arranque sin systemd | `.venv/bin/gunicorn --bind ... app:app` | `php-fpm8.3 -F` |
| Se configura en | Opciones del comando | El pool `www.conf` |

#### 7.2.14 Diagnosticar 502, 504, 404 y 403

| Código | Qué significa | Causa típica | Cómo lo compruebo |
|---|---|---|---|
| 502 Bad Gateway | nginx va bien, pero no consigue respuesta del backend | Gunicorn o PHP-FPM parado; `proxy_pass` o `fastcgi_pass` con otra dirección; socket sin permisos | `ps aux \| grep gunicorn` (o `php-fpm`); `ss -tlnp \| grep 8000` (puertos TCP en escucha y su proceso); `ls -l /run/php/`; `error.log`: `connect() failed (111: Connection refused)` o, con socket, `(2: No such file or directory)` |
| 504 Gateway Timeout | El backend está vivo pero tarda demasiado | Más de lo que espera nginx (`proxy_read_timeout`, 60 s por defecto) | Log del backend; `error.log`: `upstream timed out` |
| 404 Not Found | No existe `root` + URI | Fichero sin copiar, `root` o `alias` mal, responde otro server block, volumen sin montar | `ls -l` de la ruta; `nginx -T`; mirar `Host` y `server_name` |
| 403 Forbidden | Existe pero no se puede leer | Permisos (los workers no pueden leer) o carpeta sin `index` | `ls -l` y `ls -ld`; `error.log`: `(13: Permission denied)` |

Un fallo que no es un código HTTP: si nginx ni siquiera arranca y dice `[emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)`, otro proceso (a menudo otro nginx) ya ocupa el puerto 80. Se mira quién con `ss -tlnp` y se para ese proceso o se usa otro puerto.

#### 7.2.15 Contenedores: máquina virtual, imagen y contenedor

- **Máquina virtual (VM)**: simula un ordenador entero con **su propio sistema operativo**. La gestiona un **hipervisor** (programa que reparte la CPU, la memoria y el disco reales entre las VM).
- **Contenedor**: **comparte el núcleo** (*kernel*, la parte central del sistema operativo) del anfitrión y solo aísla los procesos y ficheros de la aplicación. Por eso arranca en segundos y ocupa megas, cuando una VM tarda minutos y ocupa gigas; a cambio, la VM aísla más. Analogía: una VM es una casa con sus propios cimientos; un contenedor, un piso que comparte los cimientos del edificio.
- **Imagen**: plantilla de solo lectura con formato `nombre:etiqueta` (`nginx:1.30`, `ubuntu:24.04`). **Contenedor**: una imagen en marcha. En DAM: la imagen es la **clase** y el contenedor, el **objeto**.
- En el Mac, Docker Desktop arranca por debajo una pequeña VM Linux, porque los contenedores necesitan un núcleo Linux. Por eso hay que abrirlo antes de usar `docker`.

#### 7.2.16 Volúmenes, puertos y Docker Compose

- **Volumen**: ficheros que el contenedor usa sin estar en la imagen. **Bind mount**: una carpeta tuya aparece dentro (`./nginx/conf.d:/etc/nginx/conf.d`). **Volumen con nombre**: lo guarda Docker (`gemas` en mi práctica). Lo que el contenedor escribe fuera de un volumen se pierde al borrarlo.
- **`:ro`** (*read only*): montaje de solo lectura. nginx solo lee, así que no puede estropear mis ficheros (mínimo privilegio: cada programa con los permisos justos).
- **Puertos `8080:80`**: siempre `anfitrión:contenedor`. Lo que entra por el 8080 del Mac llega al 80 del contenedor, donde escucha nginx.
- **Docker Compose**: describe varios contenedores en un fichero YAML (`compose.yaml` en mi práctica, `compose.yml` en las del curso) y los maneja juntos. Cada contenedor es un **servicio**. Compose crea una red en la que cada servicio se encuentra **por su nombre** (`app`, `php-fpm`). Claves de mi `compose.yaml`: `services:` (lista de servicios), dentro el nombre del servicio (`nginx:`), `image: nginx:1.30` (imagen de la que nace), `ports:` con `- "8080:80"` y `volumes:` con `- ./nginx/conf.d:/etc/nginx/conf.d:ro`. Lo escribirás entero en la P8.
- **`depends_on:`** (en la calculadora dockerizada, `web` depende de `app`) solo fija el **orden de arranque**: Compose arranca `app` antes que `web`, pero no espera a que la aplicación esté lista para responder.

#### 7.2.17 Comandos de Docker y Compose

| Comando | Qué hace |
|---|---|
| `docker run -d --name web -p 8080:80 nginx:1.30` | Crea y arranca un contenedor en segundo plano (`-d`), con nombre y puerto publicado (`-dit` para un Ubuntu que se quede encendido, como `dpl-lab`) |
| `docker ps` (`-a` para todos) | Contenedores en marcha, su estado y sus puertos |
| `docker stop <contenedor>` / `docker start <contenedor>` | Lo para / lo vuelve a arrancar sin perder nada |
| `docker rm -f <contenedor>` | Lo borra aunque esté en marcha |
| `docker build -t app:v1 .` | Construye una imagen a partir del Dockerfile (la receta de la imagen) de la carpeta actual |
| `docker logs <contenedor>` | Lo que escribe el proceso principal del contenedor |
| `docker exec <contenedor> <comando>` | Ejecuta un comando dentro (`-it` abre una terminal; `-d` no espera) |
| `docker compose up -d` | Crea y arranca los servicios en segundo plano (`-d`, *detached*) |
| `docker compose ps` | Estado y puertos de los servicios del proyecto |
| `docker compose logs <servicio>` | Logs del servicio (`--tail=20` las últimas, `-f` en directo) |
| `docker compose exec <servicio> <comando>` | Comando dentro de un servicio que ya está en marcha |
| `docker compose down` | Para y borra contenedores y red. Los volúmenes con nombre se quedan (con `-v`, también se borran) |

#### 7.2.18 El entorno del curso

El curso no usa VM: tu "máquina" es el contenedor **`dpl-lab`** (Ubuntu 24.04), creado con `docker run -dit --name dpl-lab -v ~/dpl:/home/alumno/dpl -p 80:80 -p 8080:8080 -p 8000:8000 ubuntu:24.04`. Dentro instalas con `apt-get`, eres `root` (sin `sudo`) y no hay systemd: los servicios se lanzan en primer plano y `docker exec -d` los deja corriendo. `dpl-cliente` sirve para probar desde "otra máquina". Regla de oro: **nunca se instala software de servidor en el anfitrión** (en mi caso, el Mac). Las calculadoras dockerizadas y mi práctica van en proyectos Compose aparte.

#### 7.2.19 La nube: IaaS, PaaS y SaaS

La **nube** es usar por Internet, bajo demanda, servidores, disco o bases de datos de **otra empresa**, pagando por uso. Lo contrario es **on-premise**: compras y mantienes tus máquinas. Ventajas: elasticidad (de 1 a 100 servidores y vuelta), pago por uso, rapidez, alcance global y fiabilidad. Grandes proveedores: AWS, Microsoft Azure y Google Cloud. Dos formas de pagar el cómputo: **on-demand** (por hora de uso, sin compromiso; la adecuada para aprender y para cargas variables) y **reservada** (te comprometes de 1 a 3 años a cambio de un descuento). Analogía de la vivienda: IaaS es alquilar un piso vacío (lo amueblas tú), PaaS un piso amueblado (solo traes tu ropa) y SaaS un hotel (solo lo usas).

| Modelo | Te dan | Gestionas tú | Ejemplos |
|---|---|---|---|
| IaaS (infraestructura) | Máquinas virtuales, disco y red | Sistema operativo, software y aplicación | AWS EC2, Azure Virtual Machines, Google Compute Engine, las instancias de Oracle Cloud del profesor |
| PaaS (plataforma) | Máquina, sistema y entorno de ejecución listos | Solo tu código y su configuración | AWS Elastic Beanstalk, Heroku, Google App Engine |
| SaaS (software) | La aplicación terminada | Solo usarla | Gmail, Microsoft 365, Salesforce |

#### 7.2.20 Servicios básicos de AWS

| Pieza | Qué es |
|---|---|
| EC2 | Máquinas virtuales (**instancias**). Eliges la **AMI** (plantilla del sistema, por ejemplo Ubuntu) y el **tipo** (CPU y RAM). Familias: **t** de propósito general y económica (`t3.micro`), **m** equilibrada, **c** prioriza CPU y **r** prioriza memoria |
| EBS | El disco (volumen) de la instancia |
| ECS, EKS y Fargate | Servicios gestionados de contenedores: despliegas imágenes sin gestionar la máquina (EKS usa Kubernetes, un orquestador que reparte contenedores entre muchas máquinas; con Fargate no hay servidores que administrar) |
| S3 | Almacenamiento de ficheros (objetos) en *buckets* con nombre único en todo el mundo |
| VPC | Red privada virtual donde viven tus recursos, con subredes públicas y privadas |
| Security Group | Cortafuegos de la instancia: lo que **entra** está cerrado salvo los puertos que abras (22 solo a tu IP, 80 a todos); lo que sale se permite por defecto |
| Key pair | Par de claves SSH: la **pública** va a la instancia y la **privada** (`.pem`) te la quedas tú |
| Región y zona de disponibilidad | Región: lugar geográfico (`eu-west-1`, Irlanda). Zona (AZ): centro de datos independiente dentro de la región. Repartir entre zonas da alta disponibilidad |
| IAM | Quién puede hacer qué. Por defecto todo está denegado; se conceden permisos con políticas |
| Route 53 y CloudWatch | DNS gestionado; métricas, logs y alarmas |

#### 7.2.21 Terraform: infraestructura como código

**Terraform** describe la infraestructura (máquinas, redes, cortafuegos) en ficheros de texto `.tf` escritos en **HCL** (su lenguaje), y la crea en el proveedor. Eso es **infraestructura como código (IaC)**: se versiona en Git como cualquier código. Analogía: los `.tf` son el plano del arquitecto; Terraform es la constructora que hace que el edificio coincida con el plano.

- **Declarativo**: describes el resultado, no los pasos. Ejecutarlo dos veces seguidas no cambia nada la segunda vez. **Provider**: plugin que habla con cada proveedor (`hashicorp/aws`). **Resource**: cada pieza (`aws_instance`, `aws_security_group`).
- **State** (`terraform.tfstate`): donde apunta lo que ya ha creado. No se sube a Git, igual que `.terraform/` y `*.tfvars`. Las credenciales tampoco van en los `.tf`: se guardan con `aws configure`.

| Comando | Qué hace |
|---|---|
| `terraform init` | Prepara la carpeta y descarga los providers |
| `terraform plan` | Enseña qué cambiaría, **sin hacerlo** |
| `terraform apply` | Crea o modifica los recursos (pide confirmación) |
| `terraform destroy` | Borra todo lo que creó, para no pagar |

Otros: `terraform validate` (comprueba la configuración), `terraform fmt` (la ordena), `terraform output` (enseña resultados como la IP pública) y `terraform state list` (lista lo que gestiona). En el ejemplo del curso, `user_data` es un script que la instancia ejecuta en su primer arranque para instalar nginx. La práctica 26 es formativa: no entra en la media de prácticas.

#### 7.2.22 Probar que funciona y documentarlo

| Prueba | Qué demuestra |
|---|---|
| `nginx -t` | La configuración es válida |
| `ps aux \| grep nginx` (o `gunicorn`, `php-fpm`) y `ss -tlnp` | Los procesos están vivos (master y workers) y algo escucha en el puerto esperado |
| `curl -I http://localhost:8080/` y `curl -H "Host: blog.local" http://127.0.0.1:8080/` | Responde, con qué código (`-I` pide solo cabeceras) y desde qué server block |
| `tail -n 5 /var/log/nginx/access.log` y `error.log`; `docker compose ps` y `logs` | Llegó la petición (y si falló, por qué); el contenedor está `Up` con sus puertos |
| `terraform output` y `curl -I http://IP_PUBLICA/` | La instancia de la nube responde |

Documentar (RA1-i) es dejarlo por escrito para que otra persona lo repita: un microproyecto con su Git, un README con Instalación, Configuración, Comprobación, Problemas encontrados y solución y el enlace al remoto, **salidas reales** de los comandos en bloques de código (sin capturas), un diagrama Mermaid, **un commit por paso** con subject y cuerpo, y el ZIP con la carpeta `.git`. Mi README de `nginx-para-todos` es el ejemplo.

### 7.3 Manos a la obra

Vas a repetir el ciclo completo con tu práctica: arrancar, comprobar, romper, arreglar y apagar. Todo se hace en la terminal del Mac, en la carpeta de la práctica.

**Paso 1. Abre Docker Desktop y comprueba la carpeta.**

```bash
open -a Docker
cd "$HOME/Desktop/DAM 2do Año/DPL/1er-trimestre/1er-examen/nginx-para-todos"
git status --short
ls -d docs-zensical/site blog-jekyll/_site
```

Espera a que la ballena de la barra de menús deje de moverse. `git status --short` no debe imprimir nada (repositorio limpio: luego podrás deshacer sin miedo) y `ls -d` debe listar `blog-jekyll/_site` y `docs-zensical/site`, las dos webs ya generadas. Si falta alguna, genérala (`uv run zensical build` dentro de `docs-zensical/`, o `docker compose run --rm jekyll`).

**Paso 2. Arranca, mira el estado y comprueba la configuración.**

```bash
docker compose up -d
docker compose ps
docker compose exec nginx nginx -t
```

`up -d` avisa de que crea la red (`Network nginx-para-todos_default Created`) y arranca el contenedor (`Container nginx-para-todos Started`). Si en su lugar dice `failed to connect to the docker API at unix:///Users/diego/.docker/run/docker.sock; check if the path is correct and if the daemon is running`, Docker Desktop aún no ha terminado de arrancar: espera y repite. Las otras dos órdenes responden así (fíjate en `STATUS`, que dice `Up`, y en `PORTS`, `8080->80`: el 8080 del Mac lleva al 80 del contenedor):

```text
NAME               IMAGE        COMMAND                  SERVICE   CREATED         STATUS         PORTS
nginx-para-todos   nginx:1.30   "/docker-entrypoint.…"   nginx     6 seconds ago   Up 5 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

**Paso 3. Prueba los tres server blocks cambiando solo la cabecera `Host`.**

```bash
curl -s -H "Host: docs.local" http://127.0.0.1:8080/ | grep -o "<title>[^<]*</title>" | head -1
curl -s -H "Host: blog.local" http://127.0.0.1:8080/ | grep -o "<title>[^<]*</title>" | head -1
curl -s -H "Host: otro.local" http://127.0.0.1:8080/ | grep -o "<title>[^<]*</title>" | head -1
```

```text
<title>Get started - Documentation</title>
<title>Mi temporada culé | Blog personal donde cuento cómo estoy viviendo la temporada 2026-2027 del Barça.</title>
<title>NGINX para todos</title>
```

Misma IP y mismo puerto, tres webs: la tercera es el `default_server`, porque `otro.local` no coincide con ningún `server_name`. Con `curl -I http://docs.local:8080/` verás `HTTP/1.1 200 OK` y `Server: nginx/1.30.6` (funciona con el nombre porque `docs.local` y `blog.local` están en mi `/etc/hosts`).

**Paso 4. Lee los logs.**

```bash
docker compose logs nginx
docker compose exec nginx tail -n 3 /var/log/nginx/blog.access.log
```

`docker compose logs nginx` enseña la salida del contenedor; cada línea empieza por el nombre del contenedor. Busca `/docker-entrypoint.sh: Configuration complete; ready for start up` (la imagen terminó de prepararse) y una línea `"GET / HTTP/1.1" 200` de la petición a `otro.local`: la portada no tiene log propio y usa el general, que en la imagen oficial va a la salida del contenedor. Si sale `can not modify /etc/nginx/conf.d/default.conf (read-only file system?)`, es normal: la imagen intenta retocar `default.conf` y no puede porque mi `conf.d` está montada con `:ro`. La petición al blog **no** sale ahí, porque `blog.conf` tiene su propio fichero: el `tail` la enseña como la línea de 7.2.10 (`"GET / HTTP/1.1" 200 4149`), con la fecha de hoy.

**Paso 5. Rompe la configuración quitando un `;`.**

Quita el `;` del final de `try_files` (línea 14 de `docs.conf`), a mano con `code nginx/conf.d/docs.conf` o con `sed` (`-i ''` es la forma de editar en el sitio con el `sed` de macOS). `git diff` enseña la línea vieja con `-` y la nueva con `+`:

```bash
sed -i '' 's/=404;/=404/' nginx/conf.d/docs.conf
git diff
docker compose exec nginx nginx -t
```

```text
[...]
-        try_files $uri $uri/ =404;
+        try_files $uri $uri/ =404
[...]
nginx: [emerg] unexpected "}" in /etc/nginx/conf.d/docs.conf:15
nginx: configuration file /etc/nginx/nginx.conf test failed
```

Puede salir antes la misma línea `[emerg]` con la fecha delante: es el mismo error, que la imagen también escribe en su `error.log` (enlazado a la pantalla). Léelo así: sin `;`, nginx sigue leyendo valores para `try_files` y se topa con la `}` de la línea 15, que no esperaba. **El fallo está en la línea anterior a la que dice el mensaje.** Si faltara el `;` de una directiva seguida de `{` (por ejemplo `error_log` antes de `location / {`), el mensaje sería `directive "error_log" is not terminated by ";"`. Ahora mira dos cosas con tus ojos:

```bash
curl -s -H "Host: docs.local" http://127.0.0.1:8080/ | grep -o "<title>[^<]*</title>" | head -1
docker compose exec nginx nginx -s reload
```

El `curl` sigue dando `<title>Get started - Documentation</title>`: nginx lee la configuración solo al arrancar o al recargar, así que sigue con la buena que tiene en memoria. El `reload` falla con el mismo `[emerg] unexpected "}"` y no aplica nada: la web sigue funcionando con la configuración vieja.

**Paso 6. Déjalo como estaba y recarga.**

```bash
git restore nginx/conf.d/docs.conf
git status --short
docker compose exec nginx nginx -t
docker compose exec nginx nginx -s reload
```

`git status --short` no imprime nada (fichero restaurado), `nginx -t` vuelve a dar `syntax is ok` y `test is successful`, y la recarga responde con una línea como `2026/10/18 17:48:45 [notice] 38#38: signal process started` (la fecha y el número de proceso cambian).

**Paso 7. Apaga y limpia.**

```bash
docker compose down
docker compose ps
curl -I http://localhost:8080/
```

`down` dice que ha quitado (`Removed`) el contenedor `nginx-para-todos` y la red `nginx-para-todos_default`; tus ficheros siguen en el Mac y el volumen `gemas` se queda (sin `-v` no se borra, y así Jekyll no vuelve a descargar las gemas). `docker compose ps` ya no lista ningún contenedor y el `curl` falla con `curl: (7) Failed to connect to localhost port 8080 after 0 ms: Couldn't connect to server`, porque nadie escucha en el 8080. Comprueba con `git status --short` que no queda ningún cambio y cierra Docker Desktop desde la ballena. No uses `docker system prune -a` ni toques `/etc/hosts`: no hace falta y borrarías cosas que usas.

### 7.4 Comprueba que lo sabes

**Reconocer (tipo test, una sola correcta).** Contesta en papel y después abre las respuestas.

**P1.** ¿Dentro de qué contexto se escribe `worker_connections`? a) `http`; b) `server`; c) `events`; d) `location`.

<details>
<summary>Respuesta</summary>

**c)** `events` es el contexto que dice cómo se gestionan las conexiones. `worker_processes` va en main (fuera de todo bloque) y los sitios van en `http`.

</details>

**P2.** Con PHP-FPM del paquete de Ubuntu, ¿en qué fichero se define el pool `www` (usuario, dónde escucha y número de procesos)? a) `/etc/nginx/fastcgi_params`; b) `/etc/php/8.3/fpm/pool.d/www.conf`; c) `/run/php/php8.3-fpm.sock`; d) `/etc/nginx/snippets/fastcgi-php.conf`.

<details>
<summary>Respuesta</summary>

**b)** Los otros son de nginx (a y d) o el propio socket (c), que es el fichero especial por el que se habla con PHP-FPM, no su configuración.

</details>

**P3.** ¿Qué pieza de AWS es la red privada virtual donde viven tus instancias, con subredes públicas y privadas? a) VPC; b) S3; c) IAM; d) Route 53.

<details>
<summary>Respuesta</summary>

**a)** VPC (*Virtual Private Cloud*). S3 guarda ficheros, IAM controla permisos y Route 53 es el DNS.

</details>

**P4.** En mi práctica hago `docker compose down`. ¿Qué pasa con el volumen con nombre `gemas`? a) Se borra siempre junto con el contenedor; b) Se convierte en una carpeta del Mac; c) Se borra solo si el servicio `jekyll` estaba parado; d) Se queda; solo se borra con `docker compose down -v`.

<details>
<summary>Respuesta</summary>

**d)** `down` quita contenedores y red. Los volúmenes con nombre sobreviven para no perder datos; `-v` los borra también.

</details>

**P5.** En `blog.access.log` aparece `"HEAD / HTTP/1.1" 200 0`. ¿Por qué el tamaño es 0? a) Porque `HEAD` pide solo las cabeceras y no se envía cuerpo; b) Porque el blog está vacío; c) Porque la respuesta salió de la caché; d) Porque hubo un error y nginx no envió nada.

<details>
<summary>Respuesta</summary>

**a)** Ese número son los bytes del cuerpo. `curl -I` hace un `HEAD`, que recibe solo cabeceras; el código 200 dice que todo fue bien.

</details>

**Respuesta corta (escribe el comando o la configuración)**

**P6.** Escribe el comando para arrancar Gunicorn con 4 workers, escuchando en todas las interfaces en el puerto 5000, si la aplicación está en `wsgi.py` y el objeto se llama `application`.

<details>
<summary>Respuesta</summary>

```bash
gunicorn -w 4 -b 0.0.0.0:5000 wsgi:application
```

Con opciones largas: `gunicorn --workers 4 --bind 0.0.0.0:5000 wsgi:application`. Delante de los dos puntos va el módulo (el fichero sin `.py`) y detrás el objeto WSGI.

</details>

**P7.** Escribe un server block que responda al nombre `apuntes.local` en el puerto 80 y mande todo, con redirección permanente, a `http://docs.local` conservando la ruta pedida.

<details>
<summary>Respuesta</summary>

```nginx
server {
    listen 80;
    server_name apuntes.local;
    return 301 http://docs.local$request_uri;
}
```

`301` es la redirección permanente y `$request_uri` conserva la ruta y la consulta (`/markdown/?q=x`). En mi práctica, como se entra por el 8080 del Mac, la URL tendría que llevar el puerto: `http://docs.local:8080$request_uri`.

</details>

**P8.** Escribe el servicio `web` de un `compose.yaml` con la imagen `nginx:1.30`, publicado en el puerto 8081 del anfitrión y con la carpeta `./web` montada en solo lectura en `/usr/share/nginx/html`.

<details>
<summary>Respuesta</summary>

```yaml
services:
  web:
    image: nginx:1.30
    ports:
      - "8081:80"
    volumes:
      - ./web:/usr/share/nginx/html:ro
```

El puerto va como `anfitrión:contenedor` y entre comillas (así YAML no lo confunde con otro tipo de dato). `/usr/share/nginx/html` es el DocumentRoot por defecto de la imagen oficial.

</details>

**P9.** En la carpeta de tu práctica, escribe los tres comandos para: comprobar la configuración de nginx, aplicarla sin cortar el servicio y ver las 20 últimas líneas del log del servicio.

<details>
<summary>Respuesta</summary>

```bash
docker compose exec nginx nginx -t
docker compose exec nginx nginx -s reload
docker compose logs --tail=20 nginx
```

El orden importa: primero `-t` y, solo si dice `test is successful`, el `reload`.

</details>

**P10.** Escribe las dos `location` de un server block para que nginx sirva él mismo todo lo que está bajo `/static/` desde la carpeta `/srv/app/static/` (sin que ninguna regex le quite el sitio) y pase lo demás a Gunicorn en `127.0.0.1:8000` conservando el nombre que pidió el cliente.

<details>
<summary>Respuesta</summary>

```nginx
location ^~ /static/ {
    root /srv/app;              # /static/a.css -> /srv/app/static/a.css
}

location / {
    proxy_pass http://127.0.0.1:8000;
    proxy_set_header Host $host;
}
```

`^~` hace que, si `/static/` es el prefijo más largo, no se miren las regex. También vale `alias /srv/app/static/;` en vez de `root /srv/app;`: con `root` se añade la URI entera; con `alias` se sustituye `/static/`.

</details>

**Razonar e interpretar**

**P11.** Tras editar `docs.conf`, `nginx -t` dice esto. ¿En qué línea está el fallo, por qué el mensaje habla de la 13 y qué pasa si recargas sin arreglarlo?

```text
nginx: [emerg] directive "error_log" is not terminated by ";" in /etc/nginx/conf.d/docs.conf:13
nginx: configuration file /etc/nginx/nginx.conf test failed
```

<details>
<summary>Respuesta</summary>

Falta el `;` al final de `error_log` (línea 11). Sin él, nginx sigue leyendo valores para `error_log` en las líneas siguientes hasta que encuentra la `{` de `location / {` (línea 13). Ahí se da cuenta de que una directiva simple no puede terminar en `{` y avisa en esa línea. Si haces `nginx -s reload`, el propio comando vuelve a leer la configuración, da el mismo `[emerg]` y no avisa al master: nginx sigue sirviendo con la configuración anterior.

</details>

**P12.** Tienes la práctica arrancada y `docker compose ps` enseña `0.0.0.0:8080->80/tcp`. Un compañero prueba esto y te dice que "nginx no funciona". ¿Qué ha pasado y cómo lo arreglas?

```text
$ curl -I http://localhost/
curl: (7) Failed to connect to localhost port 80 after 0 ms: Couldn't connect to server
```

<details>
<summary>Respuesta</summary>

nginx funciona. Escucha en el 80 **del contenedor**, pero en el Mac el puerto publicado es el **8080**. Sin puerto, curl va al 80 del Mac, donde no escucha nadie, y por eso falla al conectar (código 7: ni siquiera llega una respuesta HTTP). La prueba correcta es `curl -I http://localhost:8080/`.

</details>

**P13.** En la calculadora dockerizada alguien deja en nginx `proxy_pass http://127.0.0.1:8000;` y arranca Gunicorn en el servicio `app` con `--bind 127.0.0.1:8000`. Los dos contenedores están `Up`, pero la web da 502. Explica los dos fallos y corrígelos.

<details>
<summary>Respuesta</summary>

1. Dentro de un contenedor, `127.0.0.1` es **ese mismo contenedor**. nginx busca Gunicorn en su propio contenedor, donde no hay nada, y responde 502. Debe ser `proxy_pass http://app:8000;`: Compose resuelve el nombre del servicio.
2. Gunicorn escuchando en `127.0.0.1` solo acepta conexiones desde su propio contenedor. Debe ser `--bind 0.0.0.0:8000` para que le llegue nginx desde el otro contenedor. Después: `docker compose down` y `docker compose up -d` para recrear los dos contenedores con los cambios, y probar con `curl -I http://localhost:8080/`.

</details>

**P14.** Con los `.tf` del ejemplo del curso (un Security Group y una instancia EC2), `terraform plan` termina así. ¿Qué significa? ¿Ya existe algo en AWS? ¿Qué harías después y al terminar?

```text
Plan: 2 to add, 0 to change, 0 to destroy.
```

<details>
<summary>Respuesta</summary>

Terraform crearía 2 recursos nuevos (el `aws_security_group` y la `aws_instance`) y no cambiaría ni borraría nada. **Todavía no existe nada**: `plan` solo enseña lo que haría. Para crearlo: `terraform apply` (pide confirmación). Después, `terraform output` para ver la IP y `curl -I` contra ella. Al terminar, `terraform destroy` para no pagar, y `terraform state list` vacío para confirmar que no queda nada.

</details>

**P15.** Creas con Terraform una EC2 que instala nginx con `user_data`. La instancia está en marcha, pero `curl -I http://IP_PUBLICA/` se queda esperando y acaba sin respuesta. El Security Group tiene la regla de salida (`egress`) del ejemplo del curso y una sola regla de entrada: el puerto 22 desde tu IP. ¿Qué pasa y cómo lo arreglas?

<details>
<summary>Respuesta</summary>

El Security Group es el cortafuegos de la instancia y la entrada está cerrada salvo lo que abras. El 80 no está abierto, así que la petición se descarta y curl espera hasta rendirse. Hay que añadir al Security Group una regla de entrada para HTTP:

```hcl
ingress {
  from_port   = 80
  to_port     = 80
  protocol    = "tcp"
  cidr_blocks = ["0.0.0.0/0"]
}
```

Luego `terraform plan` y `terraform apply`. El 22 se queda abierto solo a tu IP (`/32`), nunca a `0.0.0.0/0`. Ojo: un Security Group creado con Terraform no trae la salida abierta si no escribes el bloque `egress`; sin él, ni siquiera el `apt-get` de `user_data` podría descargar nginx.

</details>

### 7.5 Si te atascas

- nginx: [06, apartado 5.2](06-ut2-arquitecturas-servidores-web.md) a [06, apartado 5.13](06-ut2-arquitecturas-servidores-web.md); en mi práctica, la configuración línea a línea en [04, apartado 2.5](04-practica-nginx.md), la elección del server block en [04, apartado 3](04-practica-nginx.md) y la demostración delante del profesor en [04, apartado 8](04-practica-nginx.md).
- Proxy inverso, Gunicorn, PHP-FPM y las calculadoras con Compose: [06, apartado 6.2](06-ut2-arquitecturas-servidores-web.md) a [06, apartado 6.6](06-ut2-arquitecturas-servidores-web.md).
- Contenedores, nube, AWS y Terraform: [06, apartado 7.1](06-ut2-arquitecturas-servidores-web.md) a [06, apartado 7.8](06-ut2-arquitecturas-servidores-web.md), [04, apartado 2.2](04-practica-nginx.md), [05, apartado 8](05-ut1-git-documentacion-cicd.md) y las instancias del profesor en [08, apartado «Vocabulario»](08-oracle-cloud-instancias.md).
- Diagnóstico (502, 404 y otros fallos) y documentar: [06, apartado 8.6](06-ut2-arquitecturas-servidores-web.md) a [06, apartado 8.9](06-ut2-arquitecturas-servidores-web.md). Más preguntas: [07, apartado 4.9](07-plan-de-repaso-p1.md) a [07, apartado 4.13](07-plan-de-repaso-p1.md) y el simulacro de [07, apartado 5](07-plan-de-repaso-p1.md).
- Web del curso, teoría: [Servidor web nginx](https://dpl-f1facc.gitlab.io/ut02/teoria/servidor-web-nginx/), [Gunicorn](https://dpl-f1facc.gitlab.io/ut02/teoria/gunicorn/), [PHP-FPM](https://dpl-f1facc.gitlab.io/ut02/teoria/php-fpm/), [Cloud](https://dpl-f1facc.gitlab.io/ut02/teoria/cloud/) y [Entorno de trabajo](https://dpl-f1facc.gitlab.io/introduccion/entorno/).
- Web del curso, prácticas guiadas: [Prepara tu entorno (Docker)](https://dpl-f1facc.gitlab.io/ut01/practicas/guiada-03-prepara-entorno-docker/), [04, nginx en contenedor](https://dpl-f1facc.gitlab.io/ut02/practicas/guiada-04-nginx/), [Calculadora Python](https://dpl-f1facc.gitlab.io/ut02/practicas/guiada-05-calculadora-python/), [Calculadora PHP](https://dpl-f1facc.gitlab.io/ut02/practicas/guiada-06-php-fpm/), [17, red, logs y diagnóstico](https://dpl-f1facc.gitlab.io/ut02/practicas/guiada-17-red-logs/) y [26, Terraform y AWS](https://dpl-f1facc.gitlab.io/ut02/practicas/guiada-26-terraform-aws/).

## 8. Lo visto en clase que no está en la UT1 y la UT2 (por si acaso)

Al acabar sabrás entrar en un servidor por SSH solo con clave, usar `/etc/hosts`, levantar Gitea con Docker, explicar una instancia de Oracle Cloud, por qué hay staging y producción, y cómo despliega Kamal el task-api con su Dockerfile.
No son criterios de evaluación (CE) propios de la UT1 ni de la UT2 (el SSH como servicio es de la UT5 y el Dockerfile se trabaja a fondo en la UT4), pero se han dado en clase y la web dice que cada examen trata lo impartido en su trimestre.
Además rozan tres CE que sí entran: RA6-f (claves y secretos), RA1-e (nube y contenedores) y RA1-h (máquina, IP y nombres).

### 8.1 Plan del día

Jueves por la tarde y solo si te sobra tiempo. Si vas justo, lee 8.2 y haz las preguntas de 8.4. Entre bloque y bloque, 5 minutos de descanso sin pantallas.

| Bloque | Qué haces | Tiempo |
|---|---|---|
| 1 | Leer «Lo imprescindible» (8.2) con un papel al lado: apunta cada comando, cada fichero y cada número | 45 min |
| 2 | «Manos a la obra» (8.3): mirar tu `~/.ssh` y tu `/etc/hosts`, `ssh -G` y dibujar el flujo de Kamal | 25 min |
| 3 | «Comprueba que lo sabes» (8.4): responde en papel y no abras las respuestas hasta el final | 20 min |
| 4 | Apuntar cada fallo en el registro de fallos (apartado 11) | 10 min |
| Total | Con los descansos | 1 h 55 min |

### 8.2 Lo imprescindible

#### 8.2.1 SSH: entrar en otra máquina por la red

- **SSH** (*Secure Shell*): protocolo (las normas con las que hablan dos programas) para abrir una terminal en otra máquina a través de la red, con todo cifrado. Es el mando a distancia del servidor.
- **Cliente**: el programa que llama, `ssh`, en tu Mac (`ssh usuario@IP`). **Servidor**: el que atiende, `sshd`, un *demonio* (programa que se queda en segundo plano esperando conexiones). Escucha en el **puerto 22** TCP (un puerto es el número de «ventanilla» por la que entra cada servicio).

| Fichero | Dónde vive | Para qué |
|---|---|---|
| `/etc/ssh/sshd_config` | Servidor | Configuración del servidor |
| `~/.ssh/authorized_keys` | Servidor, en el home del usuario | Claves públicas que pueden entrar con ese usuario |
| `~/.ssh/known_hosts` | Tu Mac | Huellas de los servidores que ya conoces |
| `~/.ssh/config` | Tu Mac | Alias y opciones del cliente (lo que lleva `d`, como `sshd_config`, es del servidor) |

#### 8.2.2 Clave pública, clave privada y passphrase

Analogía: la **clave pública** es un candado abierto del que repartes todas las copias que quieras, una en la puerta de cada servidor. La **clave privada** es la única llave que abre esos candados y no sale nunca de tu bolsillo. La **passphrase** es el código de la funda donde guardas la llave: si te roban la funda, sin el código no les sirve.

```bash
ssh-keygen -t ed25519 -C "staging" -f ~/.ssh/staging
```

- `-t ed25519`: tipo de clave (el algoritmo). Es la recomendada: corta y segura. RSA solo para equipos viejos, con `-b 4096`.
- `-C`: comentario para saber de quién o para qué es. `-f`: el nombre del fichero (así no pisas tu `~/.ssh/id_ed25519`). Te pide la passphrase dos veces y crea `staging` (privada) y `staging.pub` (pública).

| Fichero | Qué es | Permisos | ¿Se comparte? |
|---|---|---|---|
| `~/.ssh/` | La carpeta | `700` | No |
| `staging` | Clave privada | `600`. Si está más abierta, `ssh` la ignora (`UNPROTECTED PRIVATE KEY FILE`) | Nunca |
| `staging.pub` | Clave pública: una línea `ssh-ed25519 AAAA... staging` | `644` | Sí |
| `authorized_keys` (servidor) | Lista de públicas autorizadas, una por línea | `600` | No |

- La passphrase **no es** la contraseña del usuario del servidor: se queda en tu Mac y solo descifra la privada. Si al conectar sale `Enter passphrase for key '...'`, te pide la de tu clave. Si sale `ubuntu@IP's password:`, la del usuario del servidor.
- Buena práctica que dio el profe: una clave por máquina. Si roban una, las demás siguen a salvo.

#### 8.2.3 Llevar la pública al servidor: ssh-copy-id y authorized_keys

```bash
ssh-copy-id -i ~/.ssh/staging.pub ubuntu@IP_DE_STAGING
```

Entra una última vez con la contraseña del usuario del servidor y **añade** la pública al final de `~/.ssh/authorized_keys` de ese usuario (crea la carpeta y pone los permisos). Pon siempre `-i`: sin él puede copiar otra clave que no toca. En Oracle Cloud no hace falta: pegas la `.pub` al crear la instancia y ya entras como `ubuntu` con tu clave.

#### 8.2.4 La huella y known_hosts

La **huella** (*fingerprint*) es un resumen corto de la clave propia del servidor, como su DNI (`SHA256:R+jid5pF...`). La primera vez que conectas, `ssh` te la enseña y pregunta `Are you sure you want to continue connecting (yes/no/[fingerprint])?`. Al decir `yes`, tu Mac la guarda en `~/.ssh/known_hosts`. Si otro día no coincide, sale `WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!` y no conecta: podría ser un ataque de intermediario (*man in the middle*, alguien que se hace pasar por el servidor). Si sabes que el cambio es legítimo (has recreado la instancia), borra la huella vieja con `ssh-keygen -R IP_O_NOMBRE` y vuelve a conectar.

#### 8.2.5 Alias en ~/.ssh/config

```text
Host pirita
    HostName 203.0.113.10
    User ubuntu
    IdentityFile ~/.ssh/staging
    IdentitiesOnly yes
```

- Con esto basta `ssh pirita` (la IP `203.0.113.10` es de ejemplo). `Host` es el alias que escribes; `HostName`, la IP o el nombre real. `IdentitiesOnly yes`: solo prueba esa clave. Si prueba muchas, el servidor corta con `Too many authentication failures`.
- Para no escribir la passphrase en cada conexión, `ssh-add ~/.ssh/staging` se la da a `ssh-agent` (un programa que guarda tus claves desbloqueadas en memoria mientras dura la sesión).

#### 8.2.6 Solo con clave: PasswordAuthentication no

En el servidor, con la clave ya probada y **otra sesión abierta** por si te equivocas:

```bash
echo 'PasswordAuthentication no' | sudo tee /etc/ssh/sshd_config.d/00-solo-claves.conf
sudo sshd -t                                    # comprueba la sintaxis: si no dice nada, está bien
sudo systemctl reload ssh                       # relee la configuración sin cortar las sesiones
sudo sshd -T | grep passwordauthentication      # el valor que gana de verdad
```

- `sudo tee` escribe el fichero como root. Con `sudo echo ... > fichero` saldría `Permission denied`, porque la redirección `>` la hace tu shell sin permisos.
- Directivas: `PasswordAuthentication no` (nadie entra con contraseña), `PubkeyAuthentication yes` (con clave; ya viene así) y `PermitRootLogin no` (root no entra por SSH).
- En `sshd_config` **gana el primer valor que se lee**, y `sshd_config.d/*.conf` se lee antes (su `Include` está arriba). Por eso el nombre empieza por `00-`. Ojo: `sshd -t` (minúscula) comprueba; `sshd -T` (mayúscula) enseña la configuración efectiva.
- `reload` y no `restart`: si hay una errata, `restart` para `sshd` y ya no vuelve a arrancar, así que nadie (tú tampoco) puede abrir sesiones nuevas. En Ubuntu el servicio se llama `ssh`; en Rocky, `sshd`.
- Si alguien intenta entrar sin clave: `Permission denied (publickey).` En las imágenes de Ubuntu para la nube `PasswordAuthentication` suele venir ya en `no`: `sshd -T` te lo confirma.

#### 8.2.7 /etc/hosts: tu agenda de nombres

`/etc/hosts` es un fichero de texto que traduce nombres a IP **en tu máquina**, y se mira antes que el **DNS** (el servicio de Internet que traduce nombres a IP). Es la agenda del móvil: si el nombre está ahí, no buscas en la guía. Formato: `IP nombre [otros nombres]`. Se edita con `sudo`. El profe añadió en su ordenador la línea `IP_PUBLICA_DE_LA_MAQUINA   pirita` y desde entonces entra con `ssh ubuntu@pirita`. Diferencia con el alias de `~/.ssh/config`:

| | `/etc/hosts` | `~/.ssh/config` |
|---|---|---|
| Quién lo usa | Cualquier programa: `ssh`, `curl`, `ping`, el navegador | Solo `ssh` y lo que va por SSH (`git`, `scp`) |
| Qué guarda | Solo nombre e IP | IP, usuario, puerto, clave... |
| Alcance | Solo tu ordenador (los demás necesitan un DNS de verdad) | Solo tu usuario en tu ordenador |

#### 8.2.8 Gitea con Docker

**Gitea** es un servicio Git que instalas tú, como un GitHub propio: repos, issues y PR en tu servidor. En clase se levanta con **Docker Compose** (una herramienta que arranca contenedores leyendo un fichero YAML, `docker-compose.yml`). Una **imagen** es la plantilla; un **contenedor**, la imagen en marcha; un **volumen**, una carpeta de la máquina que el contenedor usa para que los datos no se pierdan al borrarlo. Versión con SQLite (base de datos en un solo fichero) de la guía de clase, sin las dos líneas que copian la hora de la máquina:

```yaml
services:
  server:
    image: docker.gitea.com/gitea:28.1.0-rootless
    restart: always
    volumes:
      - ./data:/var/lib/gitea   # repos y base de datos
      - ./config:/etc/gitea     # app.ini, la configuración
    ports:
      - "3000:3000"             # la web
      - "2222:2222"             # el SSH de Gitea, para git push
```

- `"3000:3000"` es `puerto_de_la_máquina:puerto_del_contenedor`: la web queda en `http://IP:3000`. `sudo docker compose up -d` arranca (`-d`: en segundo plano); `stop` para sin borrar; `down` borra los contenedores, pero no `./data` ni `./config`.
- `rootless`: dentro del contenedor Gitea no corre como root (el administrador), que es más seguro. Su SSH escucha en el 2222 y no en el 22: los puertos por debajo del 1024 se reservan tradicionalmente a root, y además el 22 de la máquina ya es de su `sshd`.
- Clonar por SSH con un puerto que no es el 22: `git clone ssh://git@IP:2222/usuario/repo.git`. En la forma corta `git@IP:2222/...`, el `2222` se toma como parte de la ruta y git va al 22.

#### 8.2.9 Oracle Cloud: instancia, imagen y shape

Oracle Cloud (OCI) es la nube de Oracle. Es **IaaS** (infraestructura como servicio): te dan la máquina y tú gestionas el sistema y lo que instalas. Su vocabulario, con el equivalente de AWS de la teoría del curso:

| Oracle | AWS (teoría) | Qué es |
|---|---|---|
| Instancia | Instancia EC2 | Máquina virtual en la nube |
| Imagen | AMI | Sistema operativo con el que arranca (Ubuntu, Rocky...) |
| Shape | Tipo de instancia (`t3.micro`) | CPU y RAM. `VM.Standard.A1.Flex` (Ampere, ARM) o `VM.Standard.E2.1.Micro` (AMD) |
| OCPU | vCPU | Unidad de CPU. En ARM, 1 OCPU es 1 núcleo; en x86, 1 OCPU son 2 vCPU |
| Security List | Security Group | Cortafuegos de la red: el 22 para SSH; el 80 y el 443 si sirves web |
| IP pública | IP pública | Dirección para llegar a la máquina desde Internet |

- **ARM** (`aarch64` o `arm64`: Ampere y tu Mac) y **x86** (`x86_64` o `amd64`: AMD e Intel) son familias de procesador distintas. Un programa o una imagen Docker de una no arranca en la otra (salvo emulando, que es lento). `uname -m` te dice cuál tienes.
- **Ubuntu frente a Rocky**: Ubuntu usa `apt`, `ufw` y AppArmor; Rocky (copia gratuita de Red Hat) usa `dnf`, `firewalld` y SELinux. El profe empezó con Rocky ARM, pero creó la máquina con Ubuntu en una AMD. En Ubuntu de Oracle el usuario es `ubuntu`.
- Lo gratis (*Always Free*) tiene límites: el profe habló de 4 OCPU y 24 GB en ARM, pero desde junio de 2026 son 2 OCPU y 12 GB en total (dos máquinas de 1 OCPU y 6 GB), más 2 AMD pequeñas de 1 GB. Mira siempre la web de Oracle.

#### 8.2.10 Staging y producción: por qué dos máquinas

- **Producción**: donde está la aplicación que usa la gente. **Staging** (*preproducción*): una copia lo más parecida posible donde se prueba cada versión antes. Es el ensayo general antes del estreno.
- Dos máquinas y no una: si el cambio rompe algo (o tumba la máquina), se rompe donde no lo ve nadie, y además pruebas el propio despliegue (puertos, volúmenes, HTTPS). Regla de oro de la UT1: cuanto más se parecen, menos sorpresas. Y se **promociona el mismo artefacto** (el paquete que se despliega, aquí la imagen Docker): la que se probó en staging es la que va a producción, sin volver a construirla.
- En el task-api: staging es `pirita` y producción es `galena`. No lo confundas con el *staging* de Git (lo de `git add`).

#### 8.2.11 Kamal: desplegar contenedores por SSH

**Kamal** despliega una aplicación en contenedores Docker en tus servidores, entrando por SSH. Se instala **solo en tu ordenador** y está hecho en **Ruby** (un lenguaje; sus librerías se llaman *gemas*): `gem install kamal`. Los servidores solo necesitan SSH y Docker, y Docker lo instala Kamal si falta. Analogía: una mudanza. Empaquetas en casa, dejas las cajas en un guardamuebles y el camión va a cada casa nueva, las recoge y lo monta todo. Lo que hace `kamal deploy`:

1. **Construye** la imagen con el Dockerfile, en tu ordenador.
2. La **sube** a un registro (un almacén de imágenes): `ghcr.io`, el de GitHub.
3. **Entra por SSH** en cada servidor del destino.
4. El servidor **descarga** la imagen (*pull*) y arranca un contenedor nuevo.
5. **kamal-proxy**, un proxy inverso (intermediario que recibe las peticiones de Internet y se las pasa a la app) que Kamal pone en el 80 y el 443, le manda el tráfico cuando `GET /up` responde `200`, y para el contenedor viejo. Así no hay corte.

`config/deploy.yml` del task-api (la parte común a los dos entornos, resumida):

```yaml
service: tasks-api
image: modiael/tasks-api
registry:
  server: ghcr.io
  username: modiael
  password:
    - KAMAL_REGISTRY_PASSWORD   # nombre del secreto: el token de GitHub va fuera del repo
ssh:
  user: ubuntu
builder:
  arch: amd64                   # sus servidores son AMD; mi Mac es arm64
proxy:
  app_port: 8000                # puerto en el que escucha la app dentro del contenedor
```

`config/deploy.staging.yml` añade la IP de `pirita` en `servers`, `proxy` con `host: stg.clicbri.es` y `ssl: true` (certificado HTTPS automático), y el volumen `/var/lib/tasks-api:/data` para que la base de datos SQLite no se pierda cuando Kamal cambia de contenedor. El `-d` de los comandos es el **destino**: Kamal mezcla `deploy.yml` con `deploy.staging.yml` (o con `deploy.production.yml`). Comandos, siempre en tu ordenador:

- `kamal setup -d staging`: la primera vez. Instala Docker si falta, arranca kamal-proxy y despliega.
- `kamal deploy -d staging`: cada versión nueva. `kamal app logs -d staging` enseña los logs y `kamal rollback VERSION -d production` vuelve a una versión anterior.

#### 8.2.12 El Dockerfile del task-api

Un **Dockerfile** es la receta para fabricar una imagen. Cada instrucción que cambia ficheros crea una **capa** (un piso de la imagen). El del repo, sin comentarios:

```dockerfile
FROM python:3.14-slim
ENV PYTHONDONTWRITEBYTECODE=1 PYTHONUNBUFFERED=1 PIP_NO_CACHE_DIR=1
WORKDIR /app
COPY requirements.txt .
RUN python -m pip install --no-cache-dir -r requirements.txt
COPY app/ ./app/
RUN useradd --create-home --uid 10001 appuser \
    && mkdir -p /data \
    && chown -R appuser:appuser /app /data
USER 10001
EXPOSE 8000
CMD ["python", "-m", "uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

| Instrucción | Cuándo actúa | Qué hace aquí |
|---|---|---|
| `FROM` | Al construir | Parte de `python:3.14-slim` (Debian mínimo con Python) |
| `ENV` | Al construir y al arrancar | Variables: `PYTHONUNBUFFERED=1` saca los logs al momento |
| `WORKDIR` | Al construir y al arrancar | Es un `cd /app` (y crea la carpeta); la app arranca ahí |
| `COPY` | Al construir | Copia ficheros del proyecto a la imagen |
| `RUN` | Al construir | Ejecuta un comando y guarda el resultado como capa |
| `USER` | Lo que viene después | Usuario con el que corre la app: UID (número de usuario) 10001, sin privilegios |
| `EXPOSE` | Solo informa | Dice que la app usa el 8000. No lo abre: eso lo hace `-p 8000:8000` o kamal-proxy |
| `CMD` | Al arrancar el contenedor | Arranca uvicorn, el servidor de aplicaciones de la API (como Gunicorn en la UT2). Va en forma JSON y solo cuenta el último `CMD` |

- **Caché de capas**: Docker reaprovecha las capas que no cambian, pero si una cambia, rehace esa y todas las siguientes. Por eso instala `requirements.txt` **antes** de copiar `app/`: si solo tocas el código, no reinstala las dependencias.
- **Usuario sin privilegios**: si alguien rompe la app, dentro del contenedor no es root. `.dockerignore` deja fuera `.git`, `.venv`, `.env` y `*.db`: imagen más pequeña, sin secretos ni la base de datos local.
- `--host 0.0.0.0`: escucha en todas las interfaces del contenedor. Con `127.0.0.1` solo se oiría a sí mismo y kamal-proxy no llegaría.

#### 8.2.13 El justfile

`just` ejecuta **recetas** (atajos de comandos) escritas en un fichero `justfile`, como un `make` sencillo. `just` a secas las lista. Las del task-api:

- `just run`: `uv run uvicorn app.main:app --reload` (desarrollo). `just docker-run`: `docker run` con `-p 8000:8000` y un volumen para `/data`.
- `just docker-build`: primero la receta `export-requirements` (saca `requirements.txt` de `uv.lock` con `uv export`) y luego `docker build -t tasks-api:local .`.
- `just setup` y `just deploy`: `kamal setup` y `kamal deploy` con `-d staging`, el destino por defecto. `just deploy production` despliega en producción.

### 8.3 Manos a la obra

Todo es de lectura: no entras en ningún servidor ni cambias nada. Abre la Terminal de tu Mac.

**Paso 1. Mira tu carpeta `~/.ssh`.**

```bash
ls -la ~/.ssh
ssh-keygen -lf ~/.ssh/produccion.pub
```

Mi salida real del 1/11 (solo algunas líneas):

```text
drwx------  14 diego  staff   448 Oct 23 16:57 .
-rw-------@  1 diego  staff  1769 Oct 18 17:52 known_hosts
-rw-------@  1 diego  staff   444 Oct 23 16:57 produccion
-rw-r--r--@  1 diego  staff    92 Oct 23 16:57 produccion.pub
256 SHA256:+u0tifJr4bX0Bxzq545+VN/Bxf3fCMuJ9IHaJdXnF6I produccion (ED25519)
```

- Carpeta en `drwx------` (700), privada en `-rw-------` (600) y pública en `-rw-r--r--` (644), como debe ser. La `@` es cosa de macOS (atributos extendidos) y no afecta a SSH. Tengo también `staging` y su `.pub`: una clave por máquina.
- `ssh-keygen -lf` enseña la huella de una pública: `256` son los bits; después, la huella, el comentario (`-C`) y el tipo. Nunca hagas `cat` de una privada ni la pegues en un chat o en un repo.

**Paso 2. Mira tu `/etc/hosts` y cómo resuelve el Mac.**

```bash
tail -2 /etc/hosts
ping -c1 pirita
```

```text
127.0.0.1 docs.local blog.local
::1 docs.local blog.local
ping: cannot resolve pirita: Unknown host
```

Las dos líneas son las que añadí en la práctica NGINX (`127.0.0.1` es el propio Mac en IPv4; `::1`, en IPv6). `pirita` no está en ningún sitio: para usarlo como el profe habría que añadir `IP_DE_LA_MAQUINA pirita` con `sudo`. Hoy no lo hagas.

**Paso 3. Mira qué haría ssh con un nombre.**

`ssh -G pirita | head -4` enseña la configuración final que usaría `ssh`, **sin conectarse**. Me sale `host pirita`, `user diego`, `hostname pirita` y `port 22`: sin alias, `ssh` usa el nombre tal cual (luego tendría que resolverlo), tu usuario del Mac y el 22. Como en el Ubuntu de Oracle el usuario es `ubuntu`, hace falta `ssh ubuntu@pirita` o un bloque `Host pirita` con `User ubuntu`.

**Paso 4. Dibuja el flujo de Kamal de memoria.**

1. En un papel y sin mirar 8.2, dibuja con cajas y flechas: tu ordenador, la imagen, `ghcr.io`, el servidor de staging, kamal-proxy y el contenedor de la app. Numera las flechas y escribe qué pasa en cada una (construir, `docker push`, SSH, `docker pull`, `/up`).
2. Compara con la solución. Si te ha faltado kamal-proxy o el `/up`, vuelve a leer el 8.2.11.

```mermaid
flowchart LR
    MAC["Mi ordenador: kamal deploy -d staging"] -->|"1. construye con el Dockerfile"| IMG["Imagen tasks-api"]
    IMG -->|"2. docker push"| REG["ghcr.io"]
    MAC -->|"3. entra por SSH como ubuntu"| SRV["Servidor de staging: pirita"]
    REG -->|"4. docker pull"| SRV
    SRV --> PROXY["kamal-proxy en el 80 y el 443"]
    PROXY -->|"5. cuando GET /up da 200"| APP["Contenedor nuevo de la app, puerto 8000"]
    USR["Navegador: https://stg.clicbri.es"] --> PROXY
```

No has cambiado nada. No borres nada de `~/.ssh`: sin `produccion` o `staging` no podrías entrar en tus máquinas.

### 8.4 Comprueba que lo sabes

**P1.** Escribe el comando para crear una clave ED25519 solo para staging, guardada en `~/.ssh/staging` y con el comentario `staging`. ¿Qué dos ficheros crea y cuál pegas en Oracle?

<details>
<summary>Respuesta</summary>

```bash
ssh-keygen -t ed25519 -C "staging" -f ~/.ssh/staging
```

Crea `~/.ssh/staging` (privada, permisos 600, no sale de tu Mac) y `~/.ssh/staging.pub` (pública). En Oracle pegas el contenido de la `.pub`. En un servidor que aún deja entrar con contraseña la llevarías con `ssh-copy-id -i ~/.ssh/staging.pub ubuntu@IP`, que la añade a su `authorized_keys`.

</details>

**P2.** Ya entras con clave en `pirita` (Ubuntu). Escribe cómo dejas la contraseña desactivada en un fichero aparte, cómo compruebas la sintaxis, cómo aplicas el cambio sin cortar tu sesión y cómo ves el valor que gana.

<details>
<summary>Respuesta</summary>

```bash
echo 'PasswordAuthentication no' | sudo tee /etc/ssh/sshd_config.d/00-solo-claves.conf
sudo sshd -t
sudo systemctl reload ssh
sudo sshd -T | grep passwordauthentication
```

La última debe decir `passwordauthentication no`. Prueba desde **otra** terminal antes de cerrar la que tienes abierta.

</details>

**P3.** Haces `ssh ubuntu@pirita` en un Mac y sale `ssh: Could not resolve hostname pirita: nodename nor servname provided, or not known`. ¿Ha llegado a hablar con el servidor? ¿Qué falta y cuáles son dos formas de arreglarlo?

<details>
<summary>Respuesta</summary>

No. Falla antes de salir del Mac: no sabe qué IP es `pirita` («resolver» es traducir el nombre a IP). Arreglos:

1. Añadir `IP_DE_PIRITA pirita` a `/etc/hosts` con `sudo`. Vale para cualquier programa (`ssh`, `curl`, el navegador).
2. Crear un bloque `Host pirita` con `HostName IP_DE_PIRITA` en `~/.ssh/config`. Solo vale para `ssh`, pero de paso guarda el usuario (`User ubuntu`) y la clave (`IdentityFile`).

</details>

**P4.** Explica en tres frases por qué el task-api tiene dos servidores (`pirita` y `galena`) y qué pasa de uno a otro.

<details>
<summary>Respuesta</summary>

`pirita` es staging (preproducción) y `galena` es producción, la que usa la gente. Cada versión se despliega primero en staging (`kamal deploy -d staging`); si algo falla, falla donde no lo ve nadie, y además se prueba el propio despliegue. Si va bien, a producción va **la misma imagen** ya probada (el mismo artefacto), sin volver a construirla.

</details>

**P5.** ¿Dónde tiene que estar instalado Ruby para usar Kamal?

- a) En los dos servidores, staging y producción
- b) Solo en el servidor de producción
- c) En tu ordenador, desde donde lanzas `kamal`
- d) Dentro de la imagen del task-api

<details>
<summary>Respuesta</summary>

**c)** Kamal es una gema de Ruby y se ejecuta en tu ordenador. A los servidores solo llega por SSH, y allí basta con Docker (que instala `kamal setup` si falta). La imagen del task-api es de Python y no lleva Ruby.

</details>

**P6.** ¿Qué hace `EXPOSE 8000` en el Dockerfile del task-api?

- a) Publica el puerto 8000 del servidor en Internet
- b) Documenta que la app escucha en el 8000; para abrirlo hace falta `-p` o un proxy
- c) Arranca uvicorn en el puerto 8000
- d) Abre el 8000 en el cortafuegos de Oracle

<details>
<summary>Respuesta</summary>

**b)** `EXPOSE` solo informa. Quien arranca uvicorn en el 8000 es el `CMD` con `--port 8000`, y quien lo hace accesible es `docker run -p 8000:8000` o, con Kamal, kamal-proxy (`app_port: 8000`).

</details>

### 8.5 Si te atascas

- SSH completo con salidas reales (claves, `ssh-copy-id`, `sshd_config`, errores de permisos, huella cambiada): [mi práctica SSH](../practica-ssh/README.md), pasos 5 a 9 y errores A a E.
- Claves SSH, tokens y secretos fuera del repo: [05, apartado 5](05-ut1-git-documentacion-cicd.md) y la sección 11 de https://dpl-f1facc.gitlab.io/ut01/teoria/git/
- Oracle, `pirita`, la passphrase y Kamal con Ruby: [08, apartado «Conectarse por SSH»](08-oracle-cloud-instancias.md) y [08, apartado «Kamal: desplegar con Docker sin instalar todo a mano»](08-oracle-cloud-instancias.md).
- `/etc/hosts` y DNS: [04, apartado 2.6](04-practica-nginx.md) y [06, apartado 2.11](06-ut2-arquitecturas-servidores-web.md). `0.0.0.0` frente a `127.0.0.1`: [06, apartado 0](06-ut2-arquitecturas-servidores-web.md).
- Imagen, contenedor, capas y Compose: [04, apartado 2.2](04-practica-nginx.md), [06, apartado 7.2](06-ut2-arquitecturas-servidores-web.md) y [06, apartado 7.4](06-ut2-arquitecturas-servidores-web.md).
- Nube (IaaS, EC2, AMI, Security Group), entornos y artefactos: [06, apartado 7.7](06-ut2-arquitecturas-servidores-web.md), [05, apartado 7](05-ut1-git-documentacion-cicd.md), https://dpl-f1facc.gitlab.io/ut02/teoria/cloud/ y las secciones 3 y 4 de https://dpl-f1facc.gitlab.io/ut01/teoria/ci-cd/
- Gitea: https://github.com/monium/gitanddocs/blob/main/docs/gitea/Install-Gitea-with-docker.md. El task-api: https://github.com/monium/task-api. Kamal: https://kamal-deploy.org/docs/installation/

## 9. Simulacro 2 (jueves por la tarde, 60 minutos)

Es el ensayo general. Las preguntas no repiten las del simulacro 1 ([07, apartado 5](07-plan-de-repaso-p1.md)) ni las de los días anteriores: tocan los mismos temas, pero desde otro ángulo.

**Ojo: es un formato de ensayo, no el oficial.** La web del curso solo dice que el examen es una prueba objetiva y que el formato (tipos de ejercicio, número de preguntas y puntuación) lo publica el profesor en el aula virtual. Si lo publica antes del jueves, adapta este simulacro a ese formato.

**Cómo hacerlo**

- Papel, boli y reloj. Sin apuntes, sin ordenador y sin móvil.
- Si una pregunta te atasca más de 2 minutos, márcala y sigue. Vuelve a ella al final.
- En este ensayo los fallos del test no restan: contesta todas y pon un "?" al lado de las que contestes a ciegas.
- Los términos nuevos se explican en las soluciones (apartado 9.4), para no dar pistas en las preguntas.

| Parte | Qué es | Puntos | Tiempo |
|---|---|---|---|
| A | 15 preguntas tipo test | 3 | 15 min |
| B | 6 preguntas de respuesta corta | 3 | 20 min |
| C | 3 casos prácticos | 4 | 25 min |

**Al terminar**

1. Corrige con el apartado 9.4. Las partes B y C traen el reparto de puntos: lo que está a medias puntúa a medias.
2. Pasa al registro de fallos (apartado 11) cada fallo y cada acierto marcado con "?": acertar a ciegas no es saberlo.
3. Suma la nota sobre 10:

| Nota | Qué significa | Viernes por la mañana |
|---|---|---|
| 8 a 10 | Vas preparado | Registro de fallos (10 min) y apartado 10 (30 min). Nada más |
| 5 a 7,9 | Aprobado, con huecos concretos | Registro de fallos (10 min), las dos filas de "Si fallaste... repasa" (final del 9.4) donde más puntos perdiste (15 min) y el apartado 10 (30 min) |
| Menos de 5 | Un ensayo la tarde antes no es el examen: solo te dice qué asegurar | Registro de fallos (10 min), las filas de la parte C en "Si fallaste... repasa" (20 min, es donde más puntos hay) y el apartado 10 a buen ritmo (20 min) |

Saques lo que saques: el jueves por la noche no estudies más (dormir fija lo repasado), el viernes nada nuevo (no abras 05 ni 06) y en un caso práctico escribe siempre algo. Un comando o una directiva bien escritos valen más que dejarlo en blanco.

### 9.1 Parte A: test (3 puntos)

Cada pregunta vale 0,2 y solo tiene una respuesta correcta. De la A1 a la A5 son de RA6 (Git, documentación y CI/CD); de la A6 a la A15, de RA1.

**A1.** Ejecutas `git checkout 643dfa8` para ver una versión antigua, haces un commit ahí y vuelves con `git switch main` sin crear ninguna rama. ¿Qué le pasa a ese commit?

- a) No pertenece a ninguna rama y lo puedes perder.
- b) Se fusiona solo en `main`.
- c) Se sube a `origin` en el siguiente `git push`.
- d) Git lo convierte en una etiqueta.

**A2.** En un proyecto con Git Flow aparece un fallo urgente en producción. La rama `hotfix/1.1.1`:

- a) nace de `develop` y vuelve solo a `develop`.
- b) nace de `main` y vuelve a `main` y a `develop`.
- c) nace de una rama `feature/*` y vuelve a `release/*`.
- d) nace de `release/*` y vuelve solo a `main`.

**A3.** Un job de un workflow de GitHub Actions lleva esta línea. ¿Cuándo se ejecuta?

```yaml
if: github.ref == 'refs/heads/main' && github.event_name == 'push'
```

- a) En cualquier push a cualquier rama.
- b) En cada pull request que apunte a `main`.
- c) Nunca, porque le falta `needs`.
- d) Solo cuando llega un push a `main` (por ejemplo, al fusionar un pull request).

**A4.** Un pipeline tiene las fases Source, Build, Test, Package y Deploy. Falla Test. ¿Qué pasa?

- a) Package y Deploy no se ejecutan y el cambio se marca en rojo.
- b) Package y Deploy se ejecutan igual, con un aviso.
- c) Se despliega en staging, pero no en producción.
- d) La herramienta repite Test hasta que pasa.

**A5.** Según la convención del módulo, ¿cómo se organizan los encabezados del README de una práctica?

- a) Un `#` por cada criterio de la rúbrica, sin índice.
- b) Un solo `#` con el nombre del proyecto, un índice al principio y cada criterio de la rúbrica como `##`.
- c) `##` para el título y `#` para cada apartado.
- d) Sin encabezados: el README es un texto corrido.

**A6.** En el modelo OSI simplificado del curso, ¿en qué capa están el formato de los datos (HTML, CSS, JSON) y el cifrado TLS?

- a) 4, transporte.
- b) 5, sesión.
- c) 6, presentación.
- d) 3, red.

**A7.** En mi Mac, que tiene `docs.local` en `/etc/hosts` pero no `fotos.local`, salen estas dos líneas. ¿Qué significan?

```text
$ curl -I http://docs.local:8080/
curl: (7) Failed to connect to docs.local port 8080 after 5 ms: Couldn't connect to server
$ curl -I http://fotos.local:8080/
curl: (6) Could not resolve host: fotos.local
```

- a) En la primera, el nombre se traduce a una IP, pero nadie escucha en el 8080; en la segunda, el nombre no se puede traducir a ninguna IP.
- b) Las dos son respuestas 404 de NGINX.
- c) La primera es un problema de nombres y la segunda, de puerto.
- d) Las dos indican que el certificado HTTPS ha caducado.

**A8.** La hoja `estilos.css` llega al navegador, pero no se aplica, y `curl -I` muestra `Content-Type: text/plain`. ¿De dónde saca NGINX normalmente el `Content-Type` de un fichero estático?

- a) Lee el fichero entero y adivina qué es.
- b) De la extensión del fichero, con la tabla `mime.types`.
- c) De la cabecera `Accept` que manda el navegador.
- d) De los permisos del fichero.

**A9.** NGINX y PHP-FPM funcionan, pero `calcular.php` tiene un error de sintaxis. Al pedirlo, ¿qué código es el más probable?

- a) 404
- b) 502
- c) 500
- d) 301

**A10.** Una tienda online tiene miles de productos con precios y stock que cambian cada pocos minutos. Según el curso, ¿qué opción encaja peor?

- a) Un servidor de aplicaciones que genere cada página al pedirla.
- b) Un CDN delante del servidor de origen para servir las imágenes.
- c) Una API que devuelva el stock en JSON.
- d) Un sitio JAMstack que genere todo el HTML en el build y lo sirva tal cual desde un CDN.

**A11.** En `dpl-lab` cambias la configuración. `nginx -t` dice `syntax is ok`, pero `nginx -s reload` da error y no se aplica nada. `ps aux | grep nginx` no muestra ningún proceso `master`. ¿Qué haces?

- a) Arrancarlo en primer plano: `docker exec -d dpl-lab nginx -g 'daemon off;'`.
- b) `systemctl restart nginx` dentro del contenedor.
- c) Borrar `sites-enabled/` y volver a crearlo.
- d) `chmod 777 /etc/nginx`.

**A12.** Instalaste Flask y Gunicorn con `.venv/bin/pip install -r requirements.txt`. Al arrancar con `gunicorn app:app` sale `ModuleNotFoundError: No module named 'flask'`. ¿Cuál es la causa más probable?

- a) NGINX no está arrancado.
- b) Has lanzado un `gunicorn` que no es el del entorno virtual: hay que usar `.venv/bin/gunicorn`.
- c) El puerto 8000 está ocupado.
- d) Hay que escribir `app.py:app`.

**A13.** Un servidor de producción tiene 4 núcleos. Según la orientación del curso, ¿cuántos workers de Gunicorn pones?

- a) 1
- b) 4
- c) 9
- d) 16

**A14.** Pides `http://localhost/index.php` y el navegador descarga el fichero, con el código PHP dentro, en vez de mostrar la página. ¿Qué falla?

- a) Falta un `index.html` en el DocumentRoot.
- b) El fichero tiene permisos 644.
- c) El puerto 443 está cerrado.
- d) No hay una `location ~ \.php$` con `fastcgi_pass` hacia PHP-FPM, o está mal puesta.

**A15.** En la nube te comprometes a usar una instancia durante 1 a 3 años a cambio de un descuento. ¿Cómo se llama esa forma de contratar?

- a) Reservada.
- b) Bajo demanda (on-demand).
- c) PaaS.
- d) SaaS.

### 9.2 Parte B: respuesta corta (3 puntos)

Cada pregunta vale 0,5. Contesta en pocas líneas.

**B1. (Comando exacto)** Acabas de hacer un commit, todavía sin `git push`, y te das cuenta de que se te olvidó incluir `nginx/conf.d/fotos.conf`. Escribe los dos comandos para meterlo en ese mismo commit sin cambiar el mensaje. Después, en una línea: ¿por qué no lo harías si ya hubieras hecho push?

**B2. (Código de estado y por qué)** En `dpl-lab` funcionaban NGINX y PHP-FPM. Actualizas PHP de la 8.2 a la 8.3 y desde entonces todos los `.php` fallan. En el server block sigue esta línea:

```nginx
fastcgi_pass unix:/run/php/php8.2-fpm.sock;
```

¿Qué código recibe el cliente y por qué? ¿Con qué comando lo confirmas? ¿Cómo lo arreglas?

**B3. (Diferencia en dos líneas)** WSGI y FastCGI. Di entre qué dos piezas del curso habla cada uno.

**B4. (Completa la configuración)** NGINX reparte la calculadora entre tres servidores Gunicorn. Completa los huecos (1), (2) y (3) y contesta la (4).

```nginx
upstream calculadora {
    ____________;                     # (1) al que tenga menos conexiones activas
    server 10.0.0.11:8000;
    server 10.0.0.12:8000;
    server 10.0.0.13:8000 ______;     # (2) solo si caen los otros dos
}

server {
    listen 80;
    server_name calculadora.local;

    location / {
        proxy_pass http://____________;   # (3)
    }
}
```

(4) Si borras la línea (1), ¿cómo reparte NGINX las peticiones?

**B5. (Explica)** a) Di dos mejoras de TLS 1.3 frente a TLS 1.2. b) ¿Qué problema de HTTP/2 resuelve HTTP/3 y cómo lo consigue?

**B6. (Completa el bloque)** Quieres que un workflow se lance en cada push a `main`, en cada pull request y también a mano desde la pestaña Actions de GitHub. Completa:

```yaml
on:
  ________:
    branches: [______]
  ________________:
  ________________:
```

### 9.3 Parte C: casos prácticos (4 puntos)

#### 9.3.1 C1. Dos sitios por nombre: uno estático y otro con Gunicorn (1,5 puntos)

Tienes un servidor Ubuntu con el paquete de NGINX (sin contenedores). Tiene que servir:

- La web estática de la empresa, que está en `/var/www/empresa`, con el nombre `empresa.local`. Si un recurso no existe, 404.
- La calculadora Flask con el nombre `calc.local`. El código está en `/srv/calculadora/app.py` y su entorno virtual en `/srv/calculadora/.venv`. Gunicorn escucha en `127.0.0.1:8000`. NGINX le tiene que pasar el nombre que pidió el cliente, la IP del cliente y si la petición llegó por http o por https.
- Cualquier otro nombre, o una petición directa a la IP, tiene que ir a la web de la empresa.

Completa los huecos (1) a (8):

```nginx
server {
    listen 80 ______________;                          # (1)
    server_name empresa.local;

    root ______________;                               # (2)
    index index.html;

    location / {
        try_files ______________;                      # (3)
    }
}

server {
    listen 80;
    server_name ______________;                        # (4)

    location / {
        ______________ http://127.0.0.1:8000;          # (5)
        proxy_set_header Host ______________;          # (6)
        proxy_set_header X-Real-IP ______________;     # (7)
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto ______________;   # (8)
    }
}
```

Y contesta:

- a) Escribe cómo arrancas Gunicorn desde `/srv/calculadora`, con el Gunicorn del entorno virtual, 2 workers y escuchando solo en la propia máquina. ¿Por qué `127.0.0.1` y no `0.0.0.0`?
- b) Escribe dos `curl` que comprueben, sin tocar `/etc/hosts`, que cada nombre llega a su sitio.
- c) Guardas el fichero en `sites-available/`, lo activas con un enlace en `sites-enabled/` y `nginx -t` falla con `[emerg] a duplicate default server for 0.0.0.0:80`. ¿Por qué, si tú solo has escrito un `default_server`? ¿Cómo lo arreglas?

#### 9.3.2 C2. Git: una issue de principio a fin y un historial para leer (1,5 puntos)

**Parte 1: escribe los comandos en orden (0,75 puntos).** Estás en `main`, al día con `origin`. En GitHub está abierta la issue #9, "Añadir la página de preguntas frecuentes". Ya tienes escritos, sin confirmar, `faq.html` (nuevo) y el enlace en `index.html`. Escribe los comandos para:

1. Crear la rama `issue-9` y cambiarte a ella.
2. Confirmar `faq.html` con la convención de commits del módulo (subject y cuerpo).
3. Confirmar `index.html` en un segundo commit cuyo cuerpo cierre la issue #9 cuando llegue a `main`.
4. Volver a `main` y fusionar `issue-9` creando siempre un commit de fusión.
5. Crear la etiqueta anotada `v1.1.0` con un mensaje.
6. Subir `main` y la etiqueta a GitHub con un solo comando.
7. Borrar la rama local `issue-9`.

**Parte 2: interpreta el historial (0,75 puntos).** Esta es la salida real de un repositorio de prueba:

```text
$ git log --oneline --graph --all --decorate
* f2566cf (HEAD -> issue-7) Enlaza el contacto desde la portada
* 29be8f6 Crea la página de contacto
| * 555d4d4 (main) Actualiza el año del pie
|/
* aff2476 Corrige el enlace de inicio
*   15fc001 (tag: v1.0.0, origin/main) Fusiona issue-3: portada con estilos
|\
| * 588eac8 Añade la hoja de estilos
| * 2746766 Crea la portada
|/
* 1a7a23a Añade el README y el .gitignore
```

1. ¿En qué rama estás? ¿Cómo lo sabes?
2. ¿Qué rama se fusionó con `--no-ff`? ¿Qué commit lo demuestra?
3. Mirando solo este dibujo, ¿puedes saber si `aff2476` se hizo en una rama o directamente en `main`? ¿Por qué?
4. ¿Cuántos commits de `main` no están todavía en GitHub? ¿Cuáles?
5. Si ahora haces `git switch main` y `git merge issue-7`, sin `--no-ff`, ¿será un fast-forward? ¿Por qué?

#### 9.3.3 C3. Un workflow con tres errores (1 punto)

Este workflow tiene que pasar las pruebas en cada push a `main` y en cada pull request y, solo cuando llega un push a `main` y las pruebas han pasado, construir una imagen Docker y publicarla en el registro de contenedores de GitHub (GHCR). Tiene **tres errores**. Encuéntralos, di qué pasaría por cada uno y corrígelos. Después, en una línea: ¿este workflow es CI, entrega continua o despliegue continuo?

```yaml
name: CI/CD

on:
  push:
    branches: [main]
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Preparar Python
        uses: actions/setup-python@v5
        with:
          python-version: "3.12"
      - name: Instalar dependencias
        run: pip install -r requirements.txt
      - name: Ejecutar las pruebas
        run: pytest -q

  build-and-push:
    if: github.ref == 'refs/heads/main' && github.event_name == 'push'
    runs-on: ubuntu-latest
    permissions:
      contents: read
      packages: write
    steps:
      - name: Descargar el repositorio
        uses: actions/checkout@v4
      - name: Iniciar sesión en GHCR
        uses: docker/login-action@v3
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: Token-De-Diego-2026
      - name: Construir y publicar la imagen
        uses: docker/build-push-action@v6
        with:
          context: .
          push: true
          tags: ghcr.io/${{ github.repository }}:${{ github.sha }}
```

### 9.4 Soluciones

Corrige con calma y pasa cada fallo al registro (apartado 11), con lo que confundiste.

#### 9.4.1 Soluciones de la parte A

<details>
<summary>Respuesta</summary>

| Pregunta | Respuesta | Por qué |
|---|---|---|
| A1 | a | Con `git checkout <hash>` quedas en *detached HEAD* (HEAD desacoplada). HEAD es el puntero que marca dónde estás; aquí apunta a un commit suelto, no a una rama. Lo que confirmes ahí no lo señala ninguna rama y, al irte, lo puedes perder. Para conservarlo, crea una rama antes de irte: `git switch -c nombre`. |
| A2 | b | Git Flow es una estrategia de ramas con `main` (solo versiones publicadas), `develop` (donde se integra lo terminado) y ramas `feature/*`, `release/*` y `hotfix/*`. Un *hotfix* (arreglo urgente) sale de lo que está en producción, `main`, y vuelve a `main` y a `develop` para que el arreglo no se pierda en la siguiente versión. |
| A3 | d | `github.ref` es la rama que disparó el workflow y `github.event_name`, el evento. `&&` significa "y": se tienen que cumplir las dos cosas, push y en `main`. Un pull request no la cumple (su evento es `pull_request`). Al fusionar un pull request en `main` se produce un push a `main`, así que en ese momento sí se ejecuta. `needs` no es obligatorio. |
| A4 | a | Un *pipeline* es la cadena de fases automáticas que recorre cada cambio. Según la web, falla de forma controlada: si una fase falla, las siguientes no se ejecutan y el cambio se marca en rojo. Así nunca se empaqueta ni se despliega algo que no pasa las pruebas. |
| A5 | b | La web pide un único `#` (el título del proyecto), un índice al principio con enlaces que funcionen en GitHub y cada criterio de la rúbrica como `##`. Así el profesor encuentra cada criterio sin buscarlo. |
| A6 | c | El modelo OSI reparte la comunicación en red en 7 capas, cada una con su tarea. La 6, presentación, es el formato de los datos y el cifrado TLS. La 4 (transporte) es TCP con los puertos 80 y 443; la 5 (sesión), el diálogo, con cookies y sesiones; la 3 (red), las direcciones IP. |
| A7 | a | `(7) Failed to connect`: `docs.local` sí se traduce a `127.0.0.1` (está en `/etc/hosts`), pero en el 8080 no escucha nadie (Docker estaba parado). Es un fallo de transporte: servicio caído o puerto sin publicar. `(6) Could not resolve host`: el nombre no se puede traducir a una IP porque no está en `/etc/hosts` ni lo conoce el DNS. En ninguno de los dos casos llega a responder NGINX, así que no hay código HTTP. Las dos salidas son reales. |
| A8 | b | El tipo MIME es la etiqueta `tipo/subtipo` que le dice al navegador qué es el contenido (`text/css`, `image/png`...). NGINX lo pone según la extensión del fichero, con la tabla `mime.types` que se incluye en `nginx.conf`. Un `.css` servido como `text/plain` indica que esa tabla no se está aplicando (por ejemplo, falta `include mime.types;`), y el navegador se niega a usarlo como hoja de estilos. |
| A9 | c | 500 Internal Server Error: el fallo está en el propio programa. NGINX sí ha llegado a PHP-FPM (si no, sería 502), pero el script no se puede ejecutar. El detalle se lee en `error.log` o en el log de PHP-FPM, no en el navegador. |
| A10 | d | JAMstack genera el HTML en el *build* (cuando se construye la web) y lo sirve desde un CDN (red de servidores repartidos por el mundo con copias del contenido). Es muy rápido, pero la web del curso dice que no es ideal para catálogos enormes con precios que cambian constantemente: habría que reconstruir la web cada pocos minutos. |
| A11 | a | `nginx -s reload` manda una señal al proceso *master* (el principal, que reparte el trabajo entre los *workers*). Sin master no hay a quién avisar: NGINX está parado. En el contenedor no hay systemd (el programa que arranca los servicios en un Linux normal), así que `systemctl` no sirve. Se arranca en primer plano con `nginx -g 'daemon off;'`, lanzado con `docker exec -d` (desatendido). |
| A12 | b | El entorno virtual (venv) es una carpeta con su propio Python y sus propios paquetes, separada del sistema. Si escribes solo `gunicorn`, la terminal usa otro (el del sistema, que no ve Flask). Con la ruta `.venv/bin/gunicorn` usas el del venv. |
| A13 | c | La orientación de producción del curso es 2 × núcleos + 1 = 2 × 4 + 1 = 9. Un *worker* es un proceso que atiende peticiones; con varios se atienden varias a la vez. En el laboratorio bastan 1 o 2. |
| A14 | d | NGINX no ejecuta PHP. Sin una `location ~ \.php$` con `fastcgi_pass`, trata el `.php` como un fichero más y lo entrega tal cual; como `.php` no está en `mime.types`, el navegador lo descarga. Además es peligroso: deja ver el código fuente. |
| A15 | a | Reservada: compromiso de 1 a 3 años con descuento. Bajo demanda (*on-demand*): pagas por hora, sin compromiso; es la buena para aprender y para cargas que cambian. PaaS y SaaS son modelos de servicio (qué parte gestiona el proveedor), no formas de pago. |

</details>

#### 9.4.2 Soluciones de la parte B

<details>
<summary>Respuesta</summary>

**B1.**

```bash
git add nginx/conf.d/fotos.conf
git commit --amend --no-edit
```

`--amend` rehace el último commit con lo que hay en el staging (la zona de preparación) y `--no-edit` conserva el mensaje. Si ya hubieras hecho push: `--amend` no modifica el commit, crea otro con un hash nuevo (el hash es el identificador de cada commit). Tu historia deja de coincidir con la del remoto, el `git push` normal se rechaza y tendrías que forzarlo, rompiendo el trabajo de quien ya lo hubiera descargado. Si ya lo subiste, haz un commit nuevo con el fichero.

Qué se valora: 0,15 por cada comando y 0,2 por el motivo (hash nuevo, reescribe una historia ya publicada).

**B2.**

- **502 Bad Gateway.** Un socket UNIX es un fichero especial por el que hablan dos programas de la misma máquina. Al actualizar, PHP-FPM 8.3 crea el suyo con otro nombre (`php8.3-fpm.sock`). NGINX intenta conectar con `php8.2-fpm.sock`, que ya no existe, y no recibe respuesta del servidor de aplicaciones. En `error.log` verás una línea parecida a `connect() to unix:/run/php/php8.2-fpm.sock failed (2: No such file or directory)`.
- **Comprobar:** `docker exec dpl-lab ls /run/php/` muestra el socket real, `php8.3-fpm.sock`. Con `docker exec dpl-lab ps aux | grep php-fpm` confirmas que PHP-FPM está en marcha.
- **Arreglar:** cambiar la línea a `fastcgi_pass unix:/run/php/php8.3-fpm.sock;`, después `docker exec dpl-lab nginx -t` y `docker exec dpl-lab nginx -s reload`, y probar con `curl -I` sobre un `.php` (debe dar `200 OK`).

Qué se valora: 0,15 el código, 0,15 el porqué, 0,1 el comando y 0,1 el arreglo.

**B3.** Un protocolo es el conjunto de reglas con el que se entienden dos programas.

- **WSGI**: el estándar de Python que dice cómo se hablan el servidor de aplicaciones y la aplicación. En el curso, entre **Gunicorn y Flask** (el objeto `app` de `app:app`). NGINX no habla WSGI: le pasa la petición a Gunicorn por HTTP con `proxy_pass`.
- **FastCGI**: el protocolo entre el **servidor web y el gestor de procesos del lenguaje**. En el curso, entre **NGINX y PHP-FPM**, con `fastcgi_pass`, por socket UNIX o por TCP (puerto 9000).

Qué se valora: 0,25 cada uno, con sus dos piezas bien puestas.

**B4.** (1) `least_conn`. (2) `backup`. (3) `calculadora`, porque `proxy_pass` apunta al nombre del bloque `upstream` (el grupo de servidores entre los que NGINX reparte). (4) *Round-robin*: por turnos, una petición a cada servidor; es el reparto por defecto. Repartir así es hacer de **balanceador de carga**: varias copias de la aplicación y NGINX delante repartiendo. Qué se valora: 0,125 cada respuesta.

**B5.** a) Dos de estas tres (el saludo, o *handshake*, es el intercambio inicial en el que cliente y servidor acuerdan cómo cifrar):

- **Saludo más rápido**: 1-RTT en vez de 2 (RTT es un viaje de ida y vuelta por la red), o 0-RTT si ya te habías conectado antes.
- **Solo cifrados AEAD**: cifran y comprueban la integridad a la vez (nadie lo lee y nadie lo cambia sin que se note). Quita los cifrados viejos y débiles.
- **Forward secrecy obligatorio**: cada sesión usa claves de un solo uso, así que si mañana roban la clave privada del servidor no pueden descifrar las sesiones grabadas antes.

b) El **bloqueo de cabeza de línea**. HTTP/2 mete todas las peticiones en una sola conexión TCP, y TCP entrega en orden: si se pierde un paquete, todo lo de detrás espera aunque ya haya llegado (como un peaje parado por el primer coche). HTTP/3 cambia TCP por **QUIC sobre UDP**, con flujos independientes: si se pierde un paquete de una imagen, el JavaScript sigue llegando.

Qué se valora: a) 0,125 cada mejora; b) 0,1 el problema y 0,15 cómo lo resuelve.

**B6.** Los huecos, en orden: `push`, `main`, `pull_request` y `workflow_dispatch` (las dos últimas claves se quedan vacías, solo con sus dos puntos). `workflow_dispatch` es el evento que añade en la pestaña Actions el botón para lanzar el workflow a mano. `pull_request:` vacío significa "en cualquier pull request". Qué se valora: 0,125 cada hueco.

</details>

#### 9.4.3 Soluciones de la parte C

<details>
<summary>Respuesta</summary>

**C1.** Los huecos:

1. `default_server` (queda `listen 80 default_server;`): atiende cualquier nombre que no coincida con otro `server_name` y las peticiones por IP.
2. `/var/www/empresa`: la carpeta de la web (su DocumentRoot).
3. `$uri $uri/ =404`: prueba el fichero, luego la carpeta y, si no hay nada, 404.
4. `calc.local`
5. `proxy_pass`: NGINX hace de proxy inverso, es decir, recibe la petición en nombre de Gunicorn y se la reenvía.
6. `$host`: el nombre que pidió el cliente. Sin él, la aplicación creería que le han pedido `127.0.0.1:8000`.
7. `$remote_addr`: la IP del cliente.
8. `$scheme`: `http` o `https`.

**a)**

```bash
cd /srv/calculadora
.venv/bin/gunicorn --bind 127.0.0.1:8000 --workers 2 app:app
```

`app:app` es el módulo `app` (el fichero `app.py`) y el objeto `app` que hay dentro. Con `127.0.0.1` Gunicorn solo escucha en la propia máquina: le llega NGINX, pero nadie desde fuera. El exterior solo ve el puerto 80 de NGINX. Con `0.0.0.0` escucharía en todas las interfaces y la calculadora quedaría expuesta sin pasar por NGINX.

**b)**

```bash
curl -I -H "Host: empresa.local" http://localhost/
curl -I -H "Host: calc.local" http://localhost/
```

Las dos deben responder `HTTP/1.1 200 OK`. Con `-H` pones a mano la cabecera `Host`, que es la que NGINX compara con cada `server_name`. Extra: `curl -I http://127.0.0.1/` debe ir a la empresa, por el `default_server`.

**c)** El paquete de Ubuntu trae activo su sitio por defecto, `sites-enabled/default`, y ese fichero ya tiene `listen 80 default_server`. Solo puede haber un servidor por defecto por cada dirección y puerto, así que con el tuyo hay dos. Arreglo: quitar el enlace del sitio de Ubuntu con `rm /etc/nginx/sites-enabled/default` (el fichero sigue en `sites-available/`), y después `nginx -t` y `nginx -s reload`.

Qué se valora: huecos, 0,1 cada uno (0,8); a) comando completo 0,15 y por qué `127.0.0.1` 0,1 (0,25); b) un `curl` con `-H "Host: ..."` por sitio (0,2); c) el porqué 0,1 y el arreglo 0,15 (0,25).

**C2, parte 1.**

```bash
git switch -c issue-9
git add faq.html
git commit -m "Añade la página de preguntas frecuentes" -m "Creo faq.html con las dudas más repetidas de los clientes. La compruebo con curl -I http://localhost/faq.html, que responde 200 OK."
git add index.html
git commit -m "Enlaza las preguntas frecuentes desde la portada" -m "Añado el enlace a faq.html en el menú de index.html. Closes #9"
git switch main
git merge --no-ff issue-9 -m "Fusiona issue-9: preguntas frecuentes"
git tag -a v1.1.0 -m "Versión 1.1.0: preguntas frecuentes"
git push --follow-tags origin main
git branch -d issue-9
```

- Dos `-m`: el primero es el *subject* (línea corta en imperativo) y el segundo, el cuerpo (qué, cómo y por qué).
- `Closes #9` cierra la issue cuando ese commit llega a `main` en GitHub, es decir, con el push del paso 6, no antes.
- `--no-ff` crea el commit de fusión aunque se pudiera hacer un *fast-forward* (avanzar el puntero de `main` sin commit de fusión). Así el historial muestra que existió la rama.
- `-a` hace la etiqueta anotada (guarda autor, fecha y mensaje). `--follow-tags` sube los commits y, con ellos, las etiquetas anotadas. En un solo comando también vale `git push origin main v1.1.0`.
- `-d` (minúscula) borra la rama porque ya está fusionada; si no lo estuviera, Git se negaría.
- Probado en un repositorio de prueba: el push termina con `main -> main` y `* [new tag] v1.1.0 -> v1.1.0`.

**C2, parte 2.**

1. En **`issue-7`**: lo dice `HEAD -> issue-7`. HEAD marca dónde estás.
2. **`issue-3`**. Lo demuestra el commit de fusión `15fc001`, "Fusiona issue-3: portada con estilos", que tiene dos padres: en el dibujo la rama se abre con `|\` y vuelve con `|/`. Y fue con `--no-ff` porque `main` no había avanzado mientras tanto (su línea baja directa a `1a7a23a`, de donde salió la rama): sin `--no-ff` habría sido un fast-forward, sin commit de fusión.
3. **No.** `aff2476` está en línea recta: puede haberse hecho en `main` o venir de una rama fusionada en fast-forward (en este repositorio venía de `issue-5`). Un fast-forward no crea commit de fusión, así que la rama no deja ningún rastro. Lo mismo pasa con `555d4d4`, que venía de `issue-6`. Por eso el módulo pide `--no-ff`.
4. **Dos**: `aff2476` y `555d4d4`. `origin/main` (lo último que tu repositorio sabe del remoto) está en `15fc001`, y `main` va dos commits por delante. `git branch -avv` lo confirma: `main 555d4d4 [origin/main: adelante 2] Actualiza el año del pie`. Se suben con `git push origin main`.
5. **No.** Desde que `issue-7` salió de `aff2476`, `main` ha avanzado con `555d4d4`: las dos ramas se han separado. Git no puede limitarse a mover el puntero y crea un commit de fusión con dos padres, aunque no pongas `--no-ff`. Probado: sale `Merge made by the 'ort' strategy.` (`ort` es el método de fusión que Git usa por defecto) y el commit nuevo tiene como padres `555d4d4` y `f2566cf`. No hay conflicto porque los dos cambios de `index.html` están en líneas distintas (Git dice `Auto-fusionando index.html`).

Qué se valora: parte 1, 0,75 (paso 1, `git switch -c issue-9` o `git branch` más `git switch`: 0,1; pasos 2 y 3, dos commits con dos `-m` y `Closes #9` en el segundo: 0,2; paso 4, `git switch main` y `git merge --no-ff issue-9`: 0,15; pasos 5, 6 y 7: 0,1 cada uno). Parte 2, 0,15 cada respuesta (0,75).

**C3. Error 1: el job `test` no descarga el repositorio.** Falta `actions/checkout`. El *runner* (la máquina virtual de GitHub que ejecuta el job) empieza vacío: sin el checkout no existe `requirements.txt`, `pip install` falla y el job sale en rojo. Es la fase Source del pipeline. Arreglo, como primer paso de `test`:

```yaml
      - name: Descargar el repositorio
        uses: actions/checkout@v4
```

**Error 2: `build-and-push` no espera a `test`.** Por defecto los jobs de un workflow corren a la vez. Sin `needs`, en un push a `main` se publicaría la imagen aunque las pruebas fallaran. Arreglo: añadir `needs: test` en `build-and-push`, a la altura de `if` y `runs-on`.

**Error 3: la contraseña está escrita en el YAML.** El workflow está versionado: cualquiera con acceso al repositorio la ve y se queda para siempre en el historial. Arreglo: `password: ${{ secrets.GITHUB_TOKEN }}`, un secreto que GitHub da a cada ejecución, que no queda en el código y que se oculta en los logs. Si era un token real, además hay que revocarlo.

Con los tres arreglos queda igual que el ejemplo de la web ([CI/CD, apartado 7](https://dpl-f1facc.gitlab.io/ut01/teoria/ci-cd/)), que además añade `workflow_dispatch`.

**Lo que no es error** (si lo marcaste, no suma, pero tampoco resta): `ubuntu-latest`; `pull_request:` vacío; `permissions` con `packages: write`, el permiso mínimo para publicar en GHCR; y la etiqueta `${{ github.sha }}`, el hash del commit, que da trazabilidad (sabes de qué commit sale cada imagen).

**¿CI, entrega o despliegue continuo?** CI más **entrega continua**: prueba cada cambio y, en `main`, deja el artefacto (la imagen Docker, el paquete que se despliega) listo en el registro. No lo despliega en producción: eso lo sigue decidiendo una persona. Para ser despliegue continuo faltaría un paso que lo desplegara solo en producción.

Qué se valora: cada error, 0,3 (0,15 localizarlo y decir qué pasaría, 0,15 corregirlo), en total 0,9; CI más entrega continua con el motivo, 0,1.

</details>

#### 9.4.4 Si fallaste... repasa

Busca tus fallos en la primera columna. "Repasa" es el apartado de este plan; "Para ampliar", solo si te sobra tiempo el jueves antes de cenar (el viernes, no).

| Si fallaste... | Tema | Repasa | Para ampliar |
|---|---|---|---|
| A1, A2, B1 | HEAD, `--amend` y Git Flow | Apartado 4 | [05, apartado 2.7](05-ut1-git-documentacion-cicd.md), [05, apartado 2.8](05-ut1-git-documentacion-cicd.md) y [05, apartado 3](05-ut1-git-documentacion-cicd.md) |
| C2 | Ramas, fusiones, etiquetas y lectura del historial | Apartado 4 | [05, apartado 2.9](05-ut1-git-documentacion-cicd.md) y [05, apartado 2.13](05-ut1-git-documentacion-cicd.md) |
| A3, A4, A5, B6, C3 | README, pipeline, GitHub Actions y secretos | Apartado 5 | [05, apartado 6](05-ut1-git-documentacion-cicd.md), [05, apartado 7](05-ut1-git-documentacion-cicd.md) y [04, apartado 5](04-practica-nginx.md) |
| A6, A7, A10 | Capas OSI, diagnóstico con `curl`, CDN y JAMstack | Apartado 6 | [06, apartado 2.3](06-ut2-arquitecturas-servidores-web.md), [06, apartado 8.1](06-ut2-arquitecturas-servidores-web.md) y [06, apartado 2.10](06-ut2-arquitecturas-servidores-web.md) |
| A8, B5 | Tipos MIME, versiones de HTTP y TLS | Apartado 6 | [06, apartado 3.7](06-ut2-arquitecturas-servidores-web.md), [06, apartado 3.9](06-ut2-arquitecturas-servidores-web.md) y [06, apartado 3.10](06-ut2-arquitecturas-servidores-web.md) |
| A11, B4 | Arranque de NGINX, proxy inverso y balanceo | Apartado 7 | [06, apartado 5.5](06-ut2-arquitecturas-servidores-web.md), [06, apartado 5.12](06-ut2-arquitecturas-servidores-web.md) y [06, apartado 5.14](06-ut2-arquitecturas-servidores-web.md) |
| C1 | Server blocks por nombre y proxy a Gunicorn | Apartado 7 | [06, apartado 5.11](06-ut2-arquitecturas-servidores-web.md), [06, apartado 6.3](06-ut2-arquitecturas-servidores-web.md) y [04, apartado 3](04-practica-nginx.md) |
| A12, A13, B3 | Gunicorn, venv, workers y WSGI | Apartado 7 | [06, apartado 6.3](06-ut2-arquitecturas-servidores-web.md) |
| A9, A14, B2 | PHP-FPM, FastCGI y los códigos 500 y 502 | Apartado 7 | [06, apartado 6.4](06-ut2-arquitecturas-servidores-web.md) y [06, apartado 8.6](06-ut2-arquitecturas-servidores-web.md) |
| A15 | Nube: formas de pago | Apartado 7 | [06, apartado 7.5](06-ut2-arquitecturas-servidores-web.md) |

Fuentes del simulacro: [Git](https://dpl-f1facc.gitlab.io/ut01/teoria/git/), [Documentación](https://dpl-f1facc.gitlab.io/ut01/teoria/documentacion/), [CI/CD](https://dpl-f1facc.gitlab.io/ut01/teoria/ci-cd/), [Arquitecturas Web](https://dpl-f1facc.gitlab.io/ut02/teoria/arquitecturas-web/), [HTTP y HTTPS](https://dpl-f1facc.gitlab.io/ut02/teoria/http-https/), [Servidor Web nginx](https://dpl-f1facc.gitlab.io/ut02/teoria/servidor-web-nginx/), [Gunicorn](https://dpl-f1facc.gitlab.io/ut02/teoria/gunicorn/), [PHP-FPM](https://dpl-f1facc.gitlab.io/ut02/teoria/php-fpm/) y [Cloud](https://dpl-f1facc.gitlab.io/ut02/teoria/cloud/).

## 10. Repaso de última hora (viernes por la mañana)

Chuleta para leer en 30 minutos la mañana del examen. Aquí no hay nada nuevo: todo sale de los apartados 4 a 7. Hoy no se aprende, se repasa.

Cómo usarla:

- Antes, los 10 minutos del registro de fallos (apartado 11), solo las filas sin marcar.
- Lee cada tabla tapando la columna de la derecha. Di la respuesta y luego destapa.
- Calcula unos 2 minutos por tabla y 5 para las trampas y los consejos del final.
- Si algo no te suena, léelo una vez y sigue. No abras 05 ni 06: hoy ya no toca.

### 10.1 Puertos

Un puerto es el número que dice a qué programa de una máquina va el tráfico. Si la IP es la dirección del edificio, el puerto es el número de puerta.

| Puerto | Para qué | Dónde lo ves |
|---|---|---|
| 22 | SSH: acceso remoto cifrado. También lo usa Git al clonar con `git@github.com:...` | Claves SSH de GitHub; Security Group (el cortafuegos de una máquina de AWS) |
| 80 | HTTP: la web sin cifrar | `listen 80;` en NGINX |
| 443 | HTTPS: la web cifrada con TLS (el protocolo que cifra la conexión) | Se configura en la UT3 |
| 8000 | Gunicorn (costumbre del curso, puerto interno) | `--bind 127.0.0.1:8000`, `proxy_pass http://127.0.0.1:8000;` |
| 9000 | PHP-FPM por TCP (costumbre) | `fastcgi_pass php-fpm:9000;` entre contenedores |
| 8080 | HTTP alternativo en el anfitrión | Mi práctica: `"8080:80"` |

En `-p 8080:80` o en `"8080:80"` el primero es el **anfitrión** (mi Mac) y el segundo el **contenedor**.

### 10.2 Códigos de estado

La primera cifra dice la familia: **2xx** bien, **3xx** está en otro sitio, **4xx** la culpa es del cliente, **5xx** la culpa es del servidor.

| Código | Nombre | Qué significa | Cuándo lo ves |
|---|---|---|---|
| 200 | OK | Todo correcto | `curl -I` a un sitio que funciona |
| 301 | Moved Permanently | Movido para siempre; la nueva URL va en `Location` | `http` a `https`; en mi práctica, `/markdown` a `/markdown/` |
| 400 | Bad Request | Petición mal formada | Cabeceras mal escritas |
| 401 | Unauthorized | Falta autenticarse: no sé quién eres | Zona con usuario y contraseña (UT3) |
| 403 | Forbidden | Sé lo que pides, pero no te dejo | Permisos de ficheros o carpetas mal |
| 404 | Not Found | No existe donde el servidor lo busca | URL mal escrita, fichero no publicado, `root` mal |
| 405 | Method Not Allowed | Ese método no se permite ahí | Un POST a un fichero estático, o un método inventado en mayúsculas (`curl -X BREW`; en minúsculas da 400) |
| 500 | Internal Server Error | La aplicación ha fallado | Error en el código PHP o Python |
| 502 | Bad Gateway | NGINX no consigue respuesta del servidor de aplicaciones | Gunicorn o PHP-FPM parados; puerto o socket mal |
| 504 | Gateway Timeout | El servidor de aplicaciones está, pero tarda demasiado | Gunicorn saturado o petición muy lenta |

### 10.3 Comandos de Git imprescindibles

| Comando | Qué hace |
|---|---|
| `git init` | Crea el repositorio (la carpeta oculta `.git`) en la carpeta actual |
| `git config --local user.name "Nombre Apellidos"` | Pone tu identidad solo en este repositorio (con `--global`, en todos) |
| `git status` | Dice en qué zona está cada fichero: sin preparar, preparado o sin seguimiento |
| `git add fichero` | Pasa los cambios del fichero al staging |
| `git commit -m "subject" -m "cuerpo"` | Guarda un commit con la convención del módulo |
| `git commit --amend` | Rehace el último commit; solo si todavía no lo has subido |
| `git log --oneline --graph --all` | Historial resumido con el dibujo de todas las ramas |
| `git log --format='%an <%ae>' \| sort -u` | Lista los autores de los commits (para comprobar la autoría) |
| `git diff` | Cambios que aún no has preparado |
| `git show <hash>` | Qué hizo un commit concreto (el hash es su identificador, como `d007fc3`) |
| `git restore fichero` | Tira los cambios sin preparar del fichero (no se recuperan) |
| `git restore --staged fichero` | Saca el fichero del staging sin tocar sus cambios |
| `git rm --cached fichero` | Deja de versionar el fichero sin borrarlo del disco |
| `git switch -c rama` | Crea una rama y se cambia a ella |
| `git merge --no-ff rama` | Fusiona la rama creando siempre un commit de fusión |
| `git merge --abort` | Cancela una fusión con conflicto (las dos ramas cambiaron las mismas líneas) y lo deja todo como estaba |
| `git branch -d rama` | Borra una rama ya fusionada |
| `git clone URL` | Copia un repositorio remoto con todo su historial y crea el remoto `origin` |
| `git remote add upstream URL` | Añade el remoto del repositorio original (en un fork) |
| `git fetch upstream` | Descarga los cambios del remoto sin fusionarlos |
| `git pull` | Descarga y fusiona en tu rama (`fetch` + `merge`) |
| `git push -u origin rama` | Sube una rama nueva y la vincula a la remota (solo la primera vez) |
| `git tag -a 0.1.0 -m "mensaje"` | Crea una etiqueta anotada que marca una versión |
| `git push --follow-tags` | Sube los commits y las etiquetas anotadas |
| `git stash -u` / `git stash pop` | Guarda el trabajo a medias (también lo nuevo) / lo recupera |
| `git revert <hash>` | Crea un commit nuevo que deshace otro, sin reescribir la historia |

### 10.4 Claves de un workflow de GitHub Actions

El fichero va en `.github/workflows/` con extensión `.yml`. Las sangrías son espacios, nunca tabuladores.

| Clave | Qué es | Ejemplo |
|---|---|---|
| `name` | Nombre del workflow, de un trabajo o de un paso | `name: CI` |
| `on` | Eventos que lo disparan | `push`, `pull_request` |
| `branches` | Limita el evento a unas ramas | `push:` con `branches: [main]` |
| `workflow_dispatch` | Permite lanzarlo a mano | `on:` con `workflow_dispatch:` |
| `jobs` | Los trabajos del workflow | `jobs:` con `test:` debajo |
| `runs-on` | Máquina virtual (runner) en la que corre el trabajo | `runs-on: ubuntu-latest` |
| `steps` | Los pasos del trabajo, en orden | Lista de `- name: ...` |
| `uses` | Usa una acción ya hecha | `uses: actions/checkout@v4` |
| `with` | Parámetros de esa acción | `python-version: "3.12"` |
| `run` | Ejecuta comandos en el runner | `run: pytest -q` |
| `working-directory` | Carpeta donde se ejecuta el `run` | En mi práctica, `docs-zensical` |
| `needs` | Este trabajo espera a que otro termine bien | `needs: test` |
| `if` | Condición para ejecutar el trabajo o el paso | `if: github.ref == 'refs/heads/main'` |
| `permissions` | Permisos mínimos del token automático | `contents: read` |
| `secrets` | No es una clave del YAML: es la forma de leer, dentro de `${{ }}`, las credenciales guardadas en GitHub. Nunca se escriben en el fichero | `${{ secrets.GITHUB_TOKEN }}` (este lo crea GitHub solo) |

- **Fases de un pipeline**: source (descargar el código), build (compilar o instalar dependencias), test (pruebas), package (crear el artefacto) y deploy (publicarlo). Si una fase falla, las siguientes no se ejecutan.
- **Artefacto**: el resultado empaquetado que se despliega (una imagen Docker, un ZIP).
- **Entornos**: local, integración, staging (preproducción) y producción.
- **Herramientas**: Jenkins (`Jenkinsfile`), GitHub Actions (`.github/workflows/*.yml`) y GitLab CI (`.gitlab-ci.yml`).

### 10.5 Directivas de NGINX

Toda directiva acaba en `;` y todo bloque va entre `{ }`.

| Directiva | Qué hace | Ejemplo |
|---|---|---|
| `server` | Bloque que describe un sitio (server block) | `server { ... }` |
| `listen` | Puerto en el que escucha el sitio; `default_server` lo hace sitio por defecto (el que responde cuando el `Host` no coincide con ningún `server_name`) | `listen 80 default_server;` |
| `server_name` | Nombres a los que responde; se comparan con la cabecera `Host` | `server_name docs.local;` |
| `root` | Carpeta raíz del sitio (DocumentRoot): ruta del fichero = `root` + URI (la ruta que va detrás del nombre, como `/blog/index.html`) | `root /var/www/docs;` |
| `index` | Fichero que se sirve al pedir una carpeta | `index index.html;` |
| `location` | Agrupa las URL que coinciden con un patrón | `location / { ... }`, `location ~ \.php$ { ... }` |
| `try_files` | Prueba ficheros en orden; si ninguno existe, usa el último parámetro (aquí, responder 404) | `try_files $uri $uri/ =404;` |
| `error_page` | Página propia para un código de error | `error_page 404 /404.html;` |
| `access_log` / `error_log` | Ficheros de log del sitio | `access_log /var/log/nginx/docs.access.log;` |
| `proxy_pass` | Reenvía la petición por HTTP (a Gunicorn) | `proxy_pass http://127.0.0.1:8000;` |
| `proxy_set_header` | Cabecera que se añade al reenviar | `proxy_set_header Host $host;` |
| `fastcgi_pass` | Reenvía la petición por FastCGI (a PHP-FPM) | `fastcgi_pass unix:/run/php/php8.3-fpm.sock;` |
| `include` | Mete el contenido de otro fichero | `include snippets/fastcgi-php.conf;` |
| `user` | Usuario de los procesos worker (los que atienden las peticiones) | `user www-data;` |
| `worker_processes` | Número de procesos worker | `worker_processes auto;` |
| `worker_connections` | Conexiones a la vez por worker (dentro de `events`) | `worker_connections 768;` |
| `upstream` | Grupo de servidores para repartir carga | `upstream aplicacion { server 10.0.0.11:8000; ... }` |

| Comando o ruta | Qué es |
|---|---|
| `nginx -t` | Comprueba la sintaxis de toda la configuración |
| `nginx -T` | Igual, y además imprime la configuración completa |
| `nginx -s reload` | Recarga la configuración sin cortar el servicio (necesita nginx en marcha) |
| `nginx -g 'daemon off;'` | Arranca en primer plano: así se lanza en un contenedor, que no tiene systemd (el gestor de servicios de Linux) |
| `nginx -s stop` / `nginx -s quit` | Paran nginx. La web del curso dice que `stop` lo detiene "de forma ordenada". La documentación oficial de nginx lo matiza: `quit` es la parada ordenada (espera a que acaben las peticiones en curso) y `stop`, la rápida. En el examen, da la versión de la web y, si hay sitio, el matiz |
| `/etc/nginx/nginx.conf` | Configuración principal |
| `sites-available/` y `sites-enabled/` | Paquete de Ubuntu: el sitio vive en el primero y se activa con un enlace simbólico (un acceso directo, `ln -s`) en el segundo |
| `conf.d/*.conf` | Imagen oficial de NGINX y nginx.org (mi práctica) |
| `/var/www/html` | DocumentRoot por defecto en Ubuntu (en la imagen oficial, `/usr/share/nginx/html`) |
| `/var/log/nginx/` | `access.log` (cada petición) y `error.log` (los problemas) |
| `curl -I URL` | Solo cabeceras (método HEAD): la primera comprobación |
| `curl -v URL` | Petición y respuesta completas (`>` lo que envías, `<` lo que recibes) |
| `curl -H "Host: docs.local" URL` | Pide un sitio por su nombre sin tocar el DNS |

Ciclo de siempre: editar, `nginx -t`, `nginx -s reload`, `curl -I`. Con Docker, como en mi práctica: `docker compose exec nginx nginx -t` y `docker compose exec nginx nginx -s reload`.

### 10.6 Gunicorn frente a PHP-FPM

| | Gunicorn | PHP-FPM |
|---|---|---|
| Lenguaje | Python (Flask, Django) | PHP |
| Qué es | Servidor WSGI | Gestor de procesos FastCGI |
| Protocolo con NGINX | HTTP (NGINX hace de proxy inverso: recibe la petición y la reenvía) | FastCGI (protocolo para que el servidor web pase la petición a un programa externo) |
| Protocolo con la aplicación | WSGI: cómo Gunicorn llama al código Python | Ejecuta los scripts `.php` con su pool (grupo de procesos ya arrancados) |
| Puerto típico | 8000 (`127.0.0.1:8000`; `0.0.0.0:8000` dentro de un contenedor) | 9000 por TCP, o socket UNIX (fichero especial para hablar dentro de la misma máquina) `/run/php/php8.3-fpm.sock` |
| Directiva de NGINX | `proxy_pass http://127.0.0.1:8000;` más `proxy_set_header` | `fastcgi_pass unix:/run/php/php8.3-fpm.sock;` más `include snippets/fastcgi-php.conf;` dentro de `location ~ \.php$` |
| Arranque sin systemd | `.venv/bin/gunicorn --bind 127.0.0.1:8000 app:app` | `php-fpm8.3 -F` |
| Instalación | `pip` dentro de un entorno virtual (`.venv`, una carpeta con un Python propio del proyecto) | `apt-get install php-fpm` |
| Comprobar | `ps aux \| grep gunicorn`, `curl -I http://127.0.0.1:8000/` | `ps aux \| grep php-fpm`, `ls /run/php/` |
| Si está parado | 502 | 502 |

`app:app` significa "módulo `app` (el fichero `app.py`), objeto `app`".

### 10.7 IaaS, PaaS y SaaS

La **nube** es usar por Internet servidores, discos y redes de un proveedor y pagar por lo que gastas. Lo contrario es **on-premise**: tener las máquinas en tu propia organización.

| Modelo | El proveedor te da | Tú gestionas | Ejemplos |
|---|---|---|---|
| IaaS (infraestructura) | Máquinas virtuales, disco y red | Sistema operativo, software y aplicación | AWS EC2, Azure Virtual Machines, Google Compute Engine |
| PaaS (plataforma) | La plataforma lista: solo subes la aplicación | El código y su configuración | AWS Elastic Beanstalk, Heroku, Google App Engine |
| SaaS (software) | La aplicación terminada | Solo usarla | Gmail, Microsoft 365, Salesforce |

- **AWS básico**: EC2 (máquinas virtuales), S3 (almacenamiento de objetos: ficheros guardados en buckets), Route 53 (DNS), VPC (red privada), IAM (permisos), CloudWatch (métricas y logs). El Security Group es el cortafuegos de la instancia.
- **Terraform** describe la infraestructura en ficheros de texto. Flujo: `terraform init`, `terraform plan`, `terraform apply`, `terraform destroy`.

### 10.8 Comandos de Docker y Compose

- **Imagen**: plantilla de solo lectura (`ubuntu:24.04`, `nginx:1.30`).
- **Contenedor**: una imagen en marcha. De una imagen salen tantos como quieras.
- **Volumen**: almacenamiento que sobrevive aunque borres el contenedor.
- **Compose**: levanta varios contenedores descritos en un fichero (`compose.yaml`).

| Comando | Qué hace |
|---|---|
| `docker run -d --name web -p 8080:80 nginx:1.30` | Crea y arranca un contenedor en segundo plano (`-d`), con nombre y puerto publicado (para un Ubuntu que se quede encendido, como `dpl-lab`, se usa `-dit`) |
| `docker ps` / `docker ps -a` | Contenedores en marcha / todos, también los parados |
| `docker exec -it dpl-lab bash` | Abre una terminal dentro del contenedor |
| `docker exec -d dpl-lab nginx -g 'daemon off;'` | Lanza un programa dentro del contenedor y te devuelve la terminal |
| `docker logs dpl-lab` | Salida del proceso principal del contenedor |
| `docker stop dpl-lab` / `docker start dpl-lab` | Para / vuelve a arrancar sin perder nada |
| `docker rm -f dpl-lab` | Borra el contenedor aunque esté en marcha |
| `docker build -t app:v1 .` | Construye una imagen desde un Dockerfile (fichero con las instrucciones para fabricarla) |
| `docker compose up -d` | Levanta los servicios del `compose.yaml` en segundo plano |
| `docker compose ps` | Estado de los servicios y sus puertos |
| `docker compose logs --tail=20 servicio` | Últimas líneas del log de un servicio |
| `docker compose run --rm jekyll` | Ejecuta un servicio una vez y lo borra al acabar (en mi práctica, generar el blog) |
| `docker compose down` | Para y borra los contenedores (con `-v`, también los volúmenes) |

### 10.9 Estructura del README del profesor

```markdown
# Nombre del proyecto

Descripción en una o dos líneas: qué es y para qué sirve.

## Índice

- [Instalación](#instalacion)
- [Configuración](#configuracion)
- [Comprobación](#comprobacion)
- [Problemas encontrados y solución](#problemas-encontrados-y-solucion)

## Instalación

## Configuración

## Comprobación

## Problemas encontrados y solución
```

- Un README por repositorio, con un único `#` (el nombre del proyecto).
- Las secciones `##` coinciden con los criterios de la rúbrica y el índice enlaza a ellas.
- Comandos reales y copiables en bloques de código, con sus salidas reales. Nada de capturas: las evidencias van en Markdown y diagramas Mermaid.
- Sin credenciales reales (usuario `alumno`, contraseña `CAMBIAR_ESTO`).
- Incluye el enlace al repositorio remoto (`## Repositorio remoto`) y los RA y CE que trabaja (en mi práctica, `## Relación curricular`).
- Las anclas del índice van como en la web, sin tilde (`#instalacion`), porque así las genera Zensical. En un README que se lee en GitHub, la tilde se conserva (`#instalación`): ver apartado 5.2.11.
- Los problemas encontrados son evidencia de que sabes, no un defecto.

### 10.10 Convención de commits del profesor

| Qué | Cómo |
|---|---|
| Subject | Línea corta en imperativo que resume el paso. El prefijo `feat:`, `fix:` o `docs:` es opcional. Ejemplos de la web: `Instalar nginx y verificar el servicio`, `Añade server block HTTPS del despliegue` |
| Cuerpo | Va tras una línea en blanco y explica cómo y por qué, con comandos y resultados |
| Comando | `git commit -m "subject" -m "cuerpo"` (dos `-m`; Git pone solo la línea en blanco entre los dos) |
| Cuántos | Un commit por paso o cambio lógico. "Entrega final" o "final" no acreditan nada |
| Autoría | Nombre y apellidos y correo del aula virtual; sin eso, la entrega puntúa cero. Se comprueba con `git log --format='%an <%ae>' \| sort -u` |
| Errores | Los errores corregidos que quedan en la historia se valoran a favor |
| Issues | `Closes #N` en el PR o en el commit que llega a `main` cierra la issue N |
| Entrega | ZIP con la carpeta `.git` dentro; sin ella la práctica no se valora |

### 10.11 Trampas típicas

1. **401 frente a 403**: 401 es "no sé quién eres" (falta usuario y contraseña); 403 es "sé quién eres o lo que pides, y no te dejo" (permisos).
2. **root frente a alias**: con `root /srv/web;` en `location /fotos/`, `/fotos/a.jpg` sale de `/srv/web/fotos/a.jpg` (añade la URI); con `alias /srv/imagenes/;`, de `/srv/imagenes/a.jpg` (sustituye la parte de la `location`).
3. **fetch frente a pull**: `fetch` descarga sin tocar tu rama; `pull` descarga y fusiona (`fetch` + `merge`).
4. **Fast-forward frente a `--no-ff`**: si la rama destino no ha cambiado, Git solo adelanta el puntero (fast-forward, sin commit de fusión); `--no-ff` crea siempre el commit de fusión y la rama se ve en el grafo (es lo que se usa en las prácticas).
5. **Imagen frente a contenedor**: la imagen es la plantilla (la clase); el contenedor es esa imagen en marcha (el objeto).
6. **502 frente a 504**: 502, el servidor de aplicaciones no contesta o no está; 504, está, pero tarda más de lo permitido.
7. **Entrega continua frente a despliegue continuo**: en la entrega continua todo queda listo y una persona decide cuándo publicar; en el despliegue continuo se publica en producción solo, sin botón.
8. **`uses` frente a `run`**: `uses` usa una acción ya hecha (`actions/checkout@v4`); `run` ejecuta comandos tuyos en el runner.
9. **`--global` frente a `--local`**: `--global` vale para todos tus repositorios; `--local` solo para el actual, y si están las dos, manda la local.
10. **`revert` frente a `reset`**: `git revert` deshace un commit con otro commit nuevo y no reescribe la historia (seguro en lo ya subido); `git reset --hard` mueve la rama atrás y tira cambios (reescribe la historia).

### 10.12 Durante el examen

- **Lee todo el examen primero** (2 o 3 minutos) y marca las preguntas que sabes seguro.
- **Empieza por lo que sabes.** Coges confianza y aseguras puntos. Reparte el tiempo según lo que vale cada pregunta.
- **En las preguntas de comandos, escribe el comando exacto**, con sus opciones y comillas: `git push -u origin rama`, no "subo la rama".
- **En configuración de NGINX, no olvides el `;`** al final de cada directiva ni cerrar cada `{` con su `}`. En YAML, cuida las sangrías.
- **Si piden explicar algo**, da una definición en una frase y un ejemplo, mejor si es de tu práctica.
- **Lee bien los números**: `anfitrión:contenedor`, 401 o 403, 502 o 504.
- **Repasa al final**: puntos y coma, llaves, códigos de estado y que no te dejas ninguna pregunta.
- **No dejes nada en blanco si los fallos no restan.** Si el enunciado no lo dice, pregúntalo al empezar.
- **Si un enunciado es ambiguo, pregunta al profesor.** Mejor una pregunta que contestar a otra cosa.

## 11. Registro de fallos

Aquí apuntas todo lo que fallas esta semana: en el test de diagnóstico, en las preguntas de cada día, en el simulacro 2 y también lo que no supiste explicar en voz alta. Es la lista de lo que de verdad tienes que repasar.

Cómo usarlo:

1. **Cada fallo, una fila**: fecha, tema (Git, CI, HTTP, NGINX...), la pregunta (su número, como D7, o una frase), qué respondiste, qué era lo correcto y por qué te confundiste.
2. **"Por qué me confundí" es la columna más importante.** "Mezclé 403 con 404" o "no sabía que `-I` hace HEAD" te dice qué vigilar. "No lo sabía" no te dice nada: escribe qué confundiste.
3. **Al empezar cada día (10 minutos)** tapa "Lo correcto" y vuelve a contestar las filas sin marcar.
4. **En "Superado"** apunta la fecha de cada acierto. Cuando lo aciertes **dos veces seguidas** en días distintos, escribe "Sí" y ya no hace falta repasarla. Si vuelves a fallar, borra las fechas y empieza de nuevo.
5. **El viernes por la mañana**, solo las filas sin "Sí".

Si se llenan las 15 filas, sigue en un papel con las mismas columnas.

| Fecha | Tema | Pregunta | Lo que puse | Lo correcto | Por qué me confundí | Superado |
|---|---|---|---|---|---|---|
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
| | | | | | | |
