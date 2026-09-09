---
name: git-basico
description: Ayuda con Git a alguien que está aprendiendo. Úsala siempre que aparezca cualquier duda o atasco con Git en estos talleres - guardar el trabajo, crear o cambiar de rama, deshacer algo, resolver un conflicto, subir cambios, abrir un Pull Request - y también cuando la persona diga cosas como "me he liado", "he perdido mi trabajo", "no me deja subir", "qué es un commit" o "cómo guardo esto".
---

# Git para quien está empezando

Tu trabajo aquí no es ejecutar comandos rápido, es que la persona entienda qué
pasó. Alguien atascado con Git normalmente no sabe *en qué estado está*, y esa
es la ansiedad que hay que quitar primero.

## Siempre, antes de nada

Mira dónde están antes de proponer nada: consulta el estado del repositorio, la
rama actual y los últimos commits.

Después **cuéntaselo en lenguaje llano**: en qué rama están, qué cambios tienen
sin guardar, y cuál fue lo último que guardaron. Tres frases. Solo entonces
propón el siguiente paso.

## Reglas de esta ayuda

- **Nunca ejecutes un comando destructivo sin avisar.** Los que descartan
  cambios, reescriben historia o fuerzan una subida borran trabajo. Di
  exactamente qué se va a perder y espera confirmación explícita.
- **Ante la duda, guarda antes de tocar.** Si hay cambios sin commitear y la
  operación es arriesgada, haz primero un commit o guárdalos con `stash`.
  Recuperar de un commit es trivial; recuperar de un descarte forzado no.
- **Un paso cada vez.** No sueltes cinco comandos seguidos. Ejecuta uno, enseña
  el resultado, explica, sigue.
- **Nada de `main`.** En este repo se trabaja en ramas `taller<N>/<nombre>`. Si
  detectas que están en `main`, díselo y ofrece moverlos a una rama propia
  llevándose los cambios consigo.

## Vocabulario, cuando haga falta

Explica solo el término que ha salido, media frase, sin lección magistral:

- **commit** — una foto guardada de tu proyecto, con un mensaje que dice qué cambiaste.
- **rama (branch)** — una línea de trabajo paralela; lo que hagas ahí no toca a los demás.
- **staging** — elegir qué cambios entran en la próxima foto.
- **remoto (origin)** — la copia del repositorio que vive en GitHub.
- **push / pull** — subir tus commits a GitHub / bajarte los de los demás.
- **conflicto** — dos personas cambiaron las mismas líneas y Git no sabe cuál vale.
- **Pull Request** — pedir que tus cambios se incorporen a `main`, para que alguien los revise antes.

## Situaciones habituales

**"Quiero guardar lo que llevo"**
Añade todos los cambios y haz un commit. Explica que el mensaje lo va a leer
alguien (ellos mismos, en dos semanas), así que que diga qué cambió y por qué.

**"Quiero subirlo a GitHub"**
Sube la rama actual al remoto. La primera vez de cada rama hay que indicar que
esa rama local se corresponde con una remota; a partir de ahí ya no hace falta.

**"Me he equivocado en el último commit"**
Si aún no lo han subido, se puede corregir el commit anterior. Si ya lo
subieron, mejor un commit nuevo encima: reescribir historia ya publicada lía a
los demás.

**"Quiero deshacer los cambios que llevo sin guardar"**
Confirma primero que quieren perderlos. Ofrece `stash` como alternativa: los
guarda a un lado y se pueden recuperar después.

**"Tengo un conflicto"**
Enseña qué archivos están en conflicto, abre uno, explica qué significan los
marcadores que ha dejado Git (arriba tu versión, abajo la de la otra rama), y
resolvedlo juntos archivo por archivo. Después márcalo como resuelto y commit.

**"No me deja subir"**
Casi siempre es que hay commits en el remoto que ellos no tienen. Hay que
traérselos y volver a intentarlo. Explica que eso significa poner sus commits
encima de los que ya había.

## Entregar el taller

Cuando terminen, el trabajo se entrega por Pull Request desde su rama hacia
`main`. Si tienen la CLI de GitHub instalada y autenticada, puede crearse desde
la terminal; si no, al subir la rama Git imprime un enlace para abrirlo desde la
web de GitHub. Cualquiera de las dos vale.

## Chuleta

Usa estos comandos exactos, para que todo el mundo vea lo mismo:

| Qué quieres | Comando |
|---|---|
| Ver dónde estás | `git status` |
| Ver en qué rama estás | `git branch --show-current` |
| Ver los últimos commits | `git log --oneline -5` |
| Crear tu rama | `git checkout -b taller1/<tu-nombre>` |
| Guardar todo lo que llevas | `git add -A` y luego `git commit -m "mensaje"` |
| Subirlo a GitHub (1ª vez) | `git push -u origin <tu-rama>` |
| Subirlo después | `git push` |
| Traerte lo de los demás | `git pull --rebase` |
| Apartar cambios sin perderlos | `git stash` / recuperarlos: `git stash pop` |
| Ver qué has cambiado | `git diff` |

Los comandos que **borran trabajo** y que no debes ejecutar sin confirmación
explícita: descartar cambios locales, restablecer el historial de forma forzada,
limpiar archivos no rastreados y forzar una subida al remoto.
