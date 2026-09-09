# Guía 2 — OpenSpec

## Qué problema resuelve

La forma habitual de trabajar con una IA para programar es pedirle cosas y ver
qué sale. Funciona para algo pequeño. Cuando la cosa crece, pasa esto: le pides
un cambio, te lo hace, y de paso rompe algo que ya funcionaba, porque nadie
escribió en ningún sitio que eso tenía que seguir funcionando.

OpenSpec mete un paso antes de picar código: **primero se acuerda qué se va a
hacer, por escrito, y luego se implementa a partir de ese acuerdo.** A eso se le
llama desarrollo dirigido por especificación.

El acuerdo son archivos Markdown normales dentro de tu repositorio. Sin sintaxis
rara, sin herramientas propietarias: texto que puedes leer, corregir y discutir.
Y como está en el repositorio, es contexto — que es justo de lo que iba la
[guía anterior](01-conceptos.md).

La ventaja que vas a notar hoy es esta: **puedes corregir el plan antes de que se
escriba una sola línea de código**. Cambiar un párrafo cuesta treinta segundos;
cambiar una decisión de arquitectura ya implementada, una tarde.

## Instalación

Ya lo hiciste en la [guía de preparación](00-preparacion.md). Por si acaso —
requiere Node 20.19 o superior:

```bash
npm install -g @fission-ai/openspec@latest
```

## Poner en marcha OpenSpec

**Desde la raíz del repositorio**, no desde la carpeta del taller:

```bash
openspec init
```

Esto crea una carpeta `openspec/` con tres cosas dentro:

- `specs/` — cómo se comporta el sistema tal y como está hoy.
- `changes/` — las propuestas de cambio en las que estás trabajando.
- `archive/` — las propuestas ya terminadas.

Y además instala los comandos que vas a usar dentro de Claude Code.

> **Ojo con dónde lo ejecutas.** En este taller: `openspec init` en la raíz del
> repositorio, código de la aplicación en `workshops/01-ia-contexto-openspec/proyecto/`.
> Si lo lanzas en otro sitio, los comandos no te aparecerán en Claude Code.

## El ciclo

Cuatro comandos, que se escriben **en el chat de Claude Code**, no en la
terminal. Empiezan por barra, como los comandos de Slack: escribe `/` en la caja
del mensaje y te salen todos los disponibles.

### `/opsx:explore`

Para pensar en voz alta antes de comprometerte. Le cuentas qué quieres hacer y
te devuelve opciones, preguntas y cosas que no habías considerado. **No escribe
nada todavía.**

Aquí es donde decides el lenguaje, la base de datos y la forma de la aplicación.
Úsalo de verdad: pregúntale las ventajas y los inconvenientes de cada opción y
haz que se moje. La decisión es tuya, pero es tonto tomarla sin escuchar.

### `/opsx:propose`

Convierte lo que habéis acordado en una propuesta escrita: qué se va a construir,
cómo, y la lista de tareas para conseguirlo. Esto sí crea archivos, dentro de
`openspec/changes/`.

**Este es el momento importante del taller.** Léete la propuesta entera antes de
seguir. De verdad, entera. Si algo no te cuadra, si falta un caso del enunciado,
si ha elegido algo que no entiendes o si se ha saltado una restricción, dilo
ahora y que la corrija. Es la parte más barata de arreglar y la que más
determina cómo va a salir el resto.

Preguntas útiles para revisarla:

- ¿Cubre todos los casos del [enunciado](../brief/app-de-notas.md)?
- ¿Cumple las cinco restricciones del [`CLAUDE.md`](../CLAUDE.md) del taller?
- ¿Hay algo aquí que yo no sabría explicar? Si lo hay, pregunta qué es y por qué.
- ¿Hay algo de más? Recuerda la restricción de "lo más simple que funcione".

### `/opsx:apply`

Implementa las tareas de la propuesta. Aquí sí se escribe código.

Ve mirando lo que hace en vez de esperar al final. Si algo se tuerce, pararlo a
la tercera tarea es mucho mejor que descubrirlo en la última.

### `/opsx:archive`

Cuando el cambio está terminado y probado, esto lo da por cerrado: mueve la
propuesta al archivo y actualiza las especificaciones para que reflejen cómo
funciona el sistema ahora.

Es el paso que la gente se salta y el que hace que esto sirva para algo a la
larga: sin archivar, `specs/` deja de describir la realidad y vuelves al punto
de partida.

## El flujo completo

```
/opsx:explore   →   decides qué y con qué
     ↓
/opsx:propose   →   se escribe el plan  ←── AQUÍ REVISAS Y CORRIGES
     ↓
/opsx:apply     →   se escribe el código
     ↓
     pruebas que funciona de verdad
     ↓
/opsx:archive   →   se cierra el cambio
```

## Consejos

**No te saltes `explore` para ir directo a `propose`.** Es la tentación
principal y es donde se pierde el valor: acabas implementando la primera idea
que se te ocurrió.

**Trata la propuesta como un documento tuyo.** No es la salida de una máquina que
hay que aceptar; es un borrador que estás revisando. Edítalo, discútelo, pide
cambios.

**Si te pierdes, pregunta.** Escribe en Claude Code "explícame qué acaba de pasar"
o "por qué has decidido esto". Está para eso.

**Un cambio cada vez.** Hoy solo hay uno: la aplicación de notas. En un proyecto
real tendrías varios en `changes/` a la vez.

## Si algo falla

- **Los comandos `/opsx:...` no aparecen en Claude Code.** Casi seguro que
  `openspec init` se ejecutó en otra carpeta. Comprueba que existe una carpeta
  `openspec/` en la raíz del repositorio y que la carpeta que seleccionaste en
  Claude Code es esa raíz, no la del taller. Si está bien pero siguen sin salir,
  empieza una sesión nueva en la aplicación para que los recargue.
- **`openspec: command not found`.** No se instaló globalmente o Node es
  demasiado antiguo. Comprueba `node --version` (mínimo 20.19) y reinstala.

Documentación oficial: [github.com/Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec)
