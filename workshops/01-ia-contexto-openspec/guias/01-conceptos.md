# Guía 1 — Los cuatro conceptos que necesitas

Esto se lee en diez minutos y explica *por qué* el ejercicio está montado como
está. No hace falta que te lo aprendas: vuelve aquí cuando algo no te cuadre.

---

## 1. Qué es un modelo de IA (y qué no es)

Un modelo de lenguaje como Claude es un programa que ha leído una cantidad
enorme de texto y ha aprendido a continuarlo de forma sensata. Cuando le
escribes, no busca la respuesta en una base de datos: la **compone**, palabra a
palabra, a partir de lo que le has dado.

De ahí salen tres consecuencias que van a explicar casi todo lo que te pase hoy:

**No sabe nada de ti ni de tu proyecto si no se lo cuentas.** No tiene acceso
mágico a tu empresa, a tus decisiones ni a lo que hablasteis ayer. Solo sabe lo
que tiene delante en ese momento.

**No recuerda entre conversaciones.** Cada conversación nueva empieza de cero.
Lo que le explicaste el martes no está el miércoles.

**Puede equivocarse con mucha seguridad.** Cuando le falta información, no dice
"no sé": rellena el hueco con lo que le parece más probable. A eso se le llama
*alucinar*. No es que mienta, es que su trabajo literalmente es continuar el
texto de la forma más plausible. Por eso darle buena información no es una
cortesía, es lo que determina si el resultado sirve.

La conclusión práctica: **la calidad de lo que sale depende sobre todo de la
calidad de lo que entra**. Y a eso que entra se le llama contexto.

## 2. Qué es el contexto

El contexto es todo lo que el modelo tiene delante cuando responde: tu mensaje,
lo que lleváis hablado en esa conversación, y los archivos que ha leído.

Imagínate que entra a trabajar alguien nuevo, buenísimo técnicamente, pero con
amnesia cada mañana. Cada día tienes dos opciones: explicárselo todo otra vez de
viva voz, o **dejarlo escrito en un sitio donde sepa que tiene que mirar**. El
contexto es lo segundo.

Dos cosas importantes:

**El contexto es limitado.** Cabe mucho, pero no infinito. Si le metes el
proyecto entero, lo importante se diluye entre el ruido. Contexto bueno no es
contexto abundante, es contexto *relevante*.

**Todo lo que lee cuenta.** Si en tu repositorio hay documentación vieja que
contradice a la nueva, el modelo la va a leer y le va a hacer caso. La
documentación desactualizada no es neutra: hace daño activamente.

## 3. Qué es un repositorio, y por qué la IA trabaja mejor dentro de uno

Un **repositorio** es una carpeta de proyecto con historial: Git va guardando una
foto (un *commit*) cada vez que dices "guarda esto", y puedes volver a cualquier
foto anterior. Eso te da dos cosas: una red de seguridad, y un registro de qué
cambió, cuándo y por qué.

Para trabajar con IA es todavía más útil, por una razón que no es obvia: **te
deja aceptar cambios sin miedo**. Si le pides a Claude que modifique quince
archivos y el resultado no te gusta, vuelves atrás en un comando. Sin Git,
cada cambio grande da vértigo. Con Git, puedes experimentar.

Y una segunda razón: el repositorio es *donde vive el contexto*. Los archivos que
le explican el proyecto al modelo están ahí dentro, versionados, y mejoran con el
tiempo igual que el código.

Tres términos que vas a oír hoy:

- **Rama** — una línea de trabajo paralela. Hoy cada uno trabaja en la suya, así
  que lo que hagas no pisa lo de nadie.
- **Commit** — una foto guardada, con un mensaje que dice qué cambiaste.
- **Pull Request** — pedir que tu trabajo se incorpore al proyecto principal para
  que alguien lo revise antes. Así entregarás el taller.

## 4. Cómo se le da contexto a Claude Code

Aquí está el truco de todo el montaje. Hay dos mecanismos y los dos son solo
archivos de texto.

### `CLAUDE.md` — lo que siempre debe saber

Un archivo `CLAUDE.md` en una carpeta se lee **automáticamente** cuando trabajas
ahí. No hay que mencionarlo ni pedirlo: está siempre.

Y funciona **en cascada**. Ahora mismo, en este taller, hay dos:

```
CLAUDE.md                                    ← reglas de todo el repositorio
└── workshops/01-ia-contexto-openspec/
    └── CLAUDE.md                            ← reglas de este ejercicio
```

Cuando trabajas en la carpeta del taller, Claude lee los dos: lo general y lo
específico. Ábrelos ahora, están escritos para que los leas tú también. Vas a ver
que el de la raíz dice cosas como "explica lo que haces en lenguaje llano" y que
el del taller lleva las restricciones del ejercicio.

Eso significa algo que conviene entender bien: **las restricciones del ejercicio
no son un texto decorativo del enunciado, son contexto activo**. Claude las
respeta porque están en un archivo que lee siempre. Si te pones a proponer una
arquitectura que se las salta, te lo va a decir.

Lo que va bien en un `CLAUDE.md`: convenciones, restricciones, dónde está cada
cosa, cómo se trabaja aquí, qué no hacer. Lo que no: documentación larga que
solo hace falta a veces (para eso, un archivo aparte que se lea cuando toque) y
cualquier secreto o contraseña.

### Las skills — lo que debe saber *a veces*

Una **skill** es un manual de instrucciones para una tarea concreta, que Claude
carga **solo cuando hace falta**. Vive en `.claude/skills/<nombre>/SKILL.md` y
empieza con una descripción de cuándo usarla. Claude lee esas descripciones y
decide sola cuál aplica según lo que le pidas.

Este taller trae tres ya preparadas, y hoy las vas a usar sin escribir ninguna:

| Skill | Se activa cuando... |
|---|---|
| `git-basico` | te lías con Git, quieres guardar tu trabajo o abrir el Pull Request |
| `entorno-local` | algo no levanta, hay un error de Docker o dudas con las variables de entorno |
| `revision-de-entrega` | crees que has terminado y quieres comprobarlo |

Pruébalo cuando llegues al ejercicio: escribe *"me he liado con git, ayúdame"* y
verás que responde siguiendo un guion. Ese guion es la skill.

**Por qué existen las skills si ya existe el `CLAUDE.md`:** porque el contexto es
limitado. Si metieras todo lo que Claude podría llegar a necesitar en un único
archivo que se lee siempre, lo llenarías de cosas irrelevantes el 95% del tiempo.
Las skills separan "lo que siempre aplica" de "lo que aplica en una situación
concreta".

Hoy solo las usas. Escribirlas es otro taller.

---

## La idea de fondo

Trabajar bien con IA no va de escribir prompts ingeniosos. Va de **montar el
entorno para que la IA no tenga que adivinar**: las reglas escritas donde las
lee siempre, los manuales donde los encuentra cuando toca, y el historial de Git
por si hay que volver atrás.

Eso es exactamente lo que tienes delante en este repositorio. El repositorio del
taller *es* el ejemplo.

Ahora, a la [guía de OpenSpec](02-openspec.md).
