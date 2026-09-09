# Glosario

Las palabras que van a salir en los talleres, explicadas en una o dos frases.
No hace falta leerlo entero: ven aquí cuando alguien suelte un término y te
quedes con cara rara.

## Inteligencia artificial

**Modelo de lenguaje** — Un programa que ha aprendido de muchísimo texto a
continuar texto de forma sensata. Claude es uno.

**Contexto** — Todo lo que el modelo tiene delante al responder: tu mensaje, la
conversación y los archivos que ha leído. Es lo único que sabe de tu proyecto.

**Ventana de contexto** — Cuánto cabe ahí dentro. Es grande, pero no infinita:
si la llenas de cosas irrelevantes, lo importante se diluye.

**Alucinación** — Cuando el modelo se inventa algo con toda seguridad porque le
faltaba información. No es que mienta: rellena el hueco con lo que le parece más
probable.

**Prompt** — Lo que le escribes.

**Agente** — Una IA que además de responder puede hacer cosas: leer archivos,
ejecutar comandos, editar código. Claude Code es un agente.

**CLAUDE.md** — Un archivo de texto que Claude Code lee automáticamente al
trabajar en esa carpeta. Ahí van las reglas y convenciones del proyecto. Se leen
en cascada: el de la raíz más el de la subcarpeta donde estés.

**Skill** — Un manual de instrucciones para una tarea concreta que Claude carga
solo cuando hace falta. Vive en `.claude/skills/<nombre>/SKILL.md`.

**MCP** — Un estándar para conectar a la IA con herramientas externas (una base
de datos, Figma, GitHub). No hace falta en el taller 1.

**Modo de permisos** — Cuánto puede hacer Claude Code sin pedirte permiso.
*Manual* pregunta antes de cada cambio, *Accept edits* los aplica y tú los
revisas después, *Plan* solo propone sin tocar nada. En el taller usamos
*Accept edits*.

**Sesión** — Una conversación con Claude sobre tu proyecto. Cada una lleva su
propio contexto, así que puedes tener varias en paralelo sin que se mezclen.

**Vista de diferencias (diff)** — La pantalla que te enseña exactamente qué
líneas ha cambiado Claude: en verde lo añadido, en rojo lo quitado. Se abre
pinchando en el indicador tipo `+12 -1`.

## Git y GitHub

**Git** — El programa que guarda el historial de tu proyecto en tu ordenador.

**GitHub** — La web donde se alojan los repositorios para compartirlos. Git y
GitHub no son lo mismo.

**Repositorio (repo)** — Una carpeta de proyecto con historial.

**Clonar** — Descargarte una copia completa de un repositorio.

**Commit** — Una foto guardada del proyecto, con un mensaje que dice qué cambiaste.

**Rama (branch)** — Una línea de trabajo paralela. Lo que haces en la tuya no
toca la de los demás.

**main** — La rama principal, la versión buena. En estos talleres nadie trabaja
directamente sobre ella.

**Staging (`git add`)** — Elegir qué cambios entran en el próximo commit.

**Push / Pull** — Subir tus commits a GitHub / bajarte los de los demás.

**Remoto (origin)** — La copia del repositorio que vive en GitHub.

**Conflicto** — Dos personas cambiaron las mismas líneas y Git no sabe cuál vale.
Lo resuelves tú eligiendo.

**Pull Request (PR)** — Pedir que los cambios de tu rama se incorporen a `main`,
para que alguien los revise antes.

**.gitignore** — La lista de archivos que Git debe ignorar: dependencias,
archivos temporales y, sobre todo, secretos.

**Token de acceso** — Una contraseña larga que genera GitHub para identificarte
desde la terminal, en lugar de escribir tu contraseña real. Se trata como una
contraseña: nunca va dentro del repositorio.

**gh (CLI de GitHub)** — El programa que te deja hablar con GitHub desde la
terminal: autenticarte, abrir Pull Requests y poco más que necesitemos aquí.

## Docker y entorno local

**Docker** — Permite ejecutar programas dentro de cajas aisladas, con todo lo que
necesitan dentro. Así levantas una base de datos sin instalarla en tu ordenador.

**Imagen** — La plantilla de una de esas cajas. Como el instalador.

**Contenedor** — Una caja en marcha. Como el programa ya abierto.

**Docker Compose** — Describe en un archivo varios contenedores que trabajan
juntos (por ejemplo tu aplicación y su base de datos) y los levanta de una vez.

**docker-compose.yml** — Ese archivo.

**Volumen** — Un almacén que vive fuera del contenedor, para que los datos no
desaparezcan cuando el contenedor muere. Sin volumen no hay persistencia.

**Puerto** — El número por el que se accede a un servicio. En `5433:5432`, el
primero es el de tu máquina y el segundo el de dentro del contenedor.

**Healthcheck** — Una comprobación que dice si un contenedor está realmente listo,
no solo encendido. Es lo que evita que tu aplicación arranque antes que la base
de datos.

## Configuración y desarrollo

**Variable de entorno** — Un valor de configuración que vive fuera del código,
para que el mismo código funcione en tu portátil y en el servidor, y para que las
contraseñas no acaben en GitHub.

**.env** — El archivo donde guardas esas variables en tu máquina. **Nunca se
sube al repositorio.**

**.env.example** — La plantilla del anterior, con los nombres de las variables y
valores de ejemplo, sin secretos. Esta sí se sube.

**README** — El archivo que explica qué es el proyecto y cómo levantarlo.

**Dependencias** — Las librerías de terceros que tu proyecto necesita.

**API** — La forma en que dos programas se hablan entre sí. En el taller, cómo
la pantalla le pide los datos al servidor.

**Base de datos relacional** — Guarda los datos en tablas con filas y columnas.
Postgres y MySQL son las más habituales.

**Frontend / Backend** — Lo que ves en el navegador / lo que corre en el servidor
y habla con la base de datos.

## OpenSpec

**Desarrollo dirigido por especificación** — Acordar por escrito qué se va a
construir antes de escribir el código.

**Spec** — El documento que describe cómo se comporta el sistema hoy.

**Change (propuesta)** — Un cambio que quieres hacer: qué, cómo y las tareas para
conseguirlo. Vive en `openspec/changes/`.

**Archivar** — Dar un cambio por terminado: se guarda y las specs se actualizan
para reflejar cómo funciona ahora el sistema.

## Despliegue (taller 2)

**Desplegar** — Poner la aplicación en un servidor para que sea accesible desde
fuera de tu ordenador.

**Dokploy** — El servidor donde desplegamos en La Tienda HOME.

**Local / Producción** — Tu portátil / el servidor de verdad, con datos reales.
