# Taller 1 — IA, contexto y OpenSpec

Construir una aplicación de notas completa, de principio a fin, sin escribir
código a mano. Por el camino vas a entender cómo funciona el contexto de una IA,
por qué un repositorio bien montado cambia el resultado, y qué es trabajar a
partir de una especificación en lugar de a base de pedir cosas sueltas.

**Duración:** unas 2 horas
**Hace falta saber programar:** no
**Al terminar tendrás:** una aplicación de notas funcionando en tu portátil que se levanta con un solo comando

---

## Antes del día del taller

Haz la [guía de preparación](guias/00-preparacion.md). Son 20 minutos de
instalaciones. Si lo dejas para el momento, te pasas media sesión mirando barras
de progreso.

## Qué vas a construir

Una aplicación de notas: crear, ver, editar y borrar, con los datos guardados en
una base de datos que sobrevive a apagar el ordenador.

**Con qué tecnología, lo decides tú durante el taller.** El [enunciado](brief/app-de-notas.md)
dice qué tiene que hacer la aplicación, no cómo construirla. Elegir el cómo es
parte del ejercicio.

---

## El guion de la sesión

### Bloque 0 · Los conceptos (20 min)

Lee la [guía de conceptos](guias/01-conceptos.md) y lo comentamos juntos. Qué es
un modelo, qué es el contexto, qué es un repositorio y cómo se le da información
a Claude Code con `CLAUDE.md` y con skills.

Abre mientras tanto los dos `CLAUDE.md` de este repositorio — el de la raíz y
el de esta carpeta. Están escritos para que los leas.

### Bloque 1 · Preparar el terreno (15 min)

**1. Abre el repositorio en Claude Code.** En la aplicación de escritorio:
pestaña **Code** → **Local** → **Select folder**, y elige **la carpeta raíz del
repositorio**, no la de este taller. Si eliges la carpeta equivocada, ni las
skills ni las reglas del repo estarán disponibles.

**2. Abre la terminal integrada** con `Ctrl` + `` ` ``. Ahí vas a escribir los
comandos, sin salir de la aplicación.

**3. Crea tu rama.** En esa terminal, sustituyendo `<tu-nombre>`:

```bash
git checkout -b taller1/<tu-nombre>
```

**4. Inicializa OpenSpec.** También desde la raíz del repositorio:

```bash
openspec init
```

**5. Elige el modo de permisos.** En el selector que hay junto al botón de
enviar, pon **Accept edits**. Así Claude aplica los cambios sin pararse a
preguntar en cada archivo, y tú los revisas después en la vista de diferencias
(el indicador `+12 -1` que aparece sobre el chat). En **Manual** te pasarías el
taller dando a "aceptar".

**6. Comprueba que las skills están cargadas.** Escríbele en el chat:

> me he liado con git, ayúdame

Si te responde mirando en qué rama estás y explicándotelo en lenguaje llano en
vez de soltarte una lista de comandos, la skill está funcionando. Eso es un
archivo de este repositorio cambiando cómo se comporta.

> ✅ **Checkpoint 1** — tienes tu rama creada, existe una carpeta `openspec/` en
> la raíz, y Claude Code responde con las skills cargadas.

### Bloque 2 · Explorar y decidir (30 min)

Lee primero la [guía de OpenSpec](guias/02-openspec.md), sobre todo la parte del
ciclo de cuatro comandos.

Ahora, dentro de Claude Code:

```
/opsx:explore
```

Dile que quieres construir la aplicación del enunciado y que te ayude a decidir
con qué construirla. Para pasarle el enunciado, escribe `@` en la caja del
mensaje y empieza a teclear `app-de-notas`: te lo autocompleta y así lo lee
entero.

**Este bloque no es un trámite.** Pregunta de verdad: qué opciones hay, qué
ventajas tiene cada una, cuál es más fácil de levantar con Docker, cuál
entenderías mejor tú si mañana tienes que tocarla. Haz que se moje con una
recomendación. Y luego **decide tú**.

Después:

```
/opsx:propose
```

Y aquí viene lo importante del taller: **léete la propuesta entera**. Sin saltar.
Compárala con el enunciado y con las restricciones. Si falta un caso, si hay algo
que no entiendes, si ha metido cosas de más — dilo ahora y que lo corrija.
Corregir un párrafo cuesta treinta segundos; corregirlo cuando ya está
implementado, una tarde.

> ✅ **Checkpoint 2** — tienes una propuesta escrita en `openspec/changes/` que
> has leído entera y que cubre los seis casos del enunciado. **Lo revisamos
> juntos antes de seguir.**

### Bloque 3 · Implementar (50 min)

```
/opsx:apply
```

Ve mirando lo que va haciendo en vez de esperar al final. Si algo se tuerce,
pararlo pronto sale mucho más barato.

Cuando toque levantar el entorno, ahí entra la skill `entorno-local`. Si algo no
arranca, describe el error tal cual y deja que te lo diagnostique. Pero **pide
que te explique la causa**, no solo el arreglo: "¿por qué pasaba esto?" es la
pregunta que hace que el taller sirva para algo.

Guarda tu trabajo por el camino:

```bash
git add -A && git commit -m "avance del taller 1"
```

> ✅ **Checkpoint 3** — la aplicación levanta y puedes crear una nota desde el
> navegador.

### ☕ Pausa (10 min)

### Bloque 4 · Probar de verdad (25 min)

Que arranque no es que funcione. Recorre la lista de "cuándo está terminada" del
[enunciado](brief/app-de-notas.md), en el navegador, punto por punto. Especial
atención a estas dos, que son las que suelen fallar:

- Guardar una nota sin título: tiene que impedírtelo con un mensaje claro.
- Apagar los contenedores (`docker compose down`), volver a levantarlos y
  comprobar que **tus notas siguen ahí**.

Cuando creas que está, pídele a Claude Code:

> revisa mi entrega

Eso dispara la skill `revision-de-entrega`, que comprueba tu proyecto contra las
restricciones y te devuelve una lista de qué pasa y qué no. Arregla lo que salga
en rojo.

> ✅ **Checkpoint 4** — la revisión sale limpia y has hecho la prueba de apagar y
> encender sin perder datos.

### Bloque 5 · Cerrar y entregar (20 min)

**1. Archiva el cambio en OpenSpec:**

```
/opsx:archive
```

**2. Sube tu rama y abre el Pull Request.** Si te lías, pídeselo a Claude Code:
la skill `git-basico` lo cubre.

```bash
git add -A && git commit -m "Taller 1 completado"
git push -u origin taller1/<tu-nombre>
```

> ✅ **Checkpoint 5** — tu Pull Request está abierto.

### Bloque 6 · Puesta en común (10 min)

Comparamos qué ha elegido cada uno y por qué. Va a haber propuestas distintas
para el mismo enunciado, y esa es justo la parte interesante.

---

## Lo que te quieres llevar del taller

- El resultado de una IA depende sobre todo de la información que le das.
- El `CLAUDE.md` es contexto que se lee siempre; las skills, contexto que se
  carga cuando hace falta. Los dos son archivos de texto normales en tu repositorio.
- Acordar por escrito qué se va a hacer, y revisarlo, es más barato que corregir
  código ya escrito.
- El repositorio no es donde guardas el código: es donde vive el contexto que
  hace que la IA trabaje bien.

## Si te atascas

Pregúntale a Claude Code. Está configurado para explicar en lenguaje llano y
tiene tres skills preparadas para los atascos típicos: Git, entorno local y
revisión de la entrega. Si sigues bloqueado más de cinco minutos, levanta la
mano.

## Material del taller

- [Preparación](guias/00-preparacion.md) — instalar todo, antes del día
- [Conceptos](guias/01-conceptos.md) — modelos, contexto, repositorios, skills
- [OpenSpec](guias/02-openspec.md) — para qué sirve y cómo se usa
- [Enunciado de la aplicación](brief/app-de-notas.md) — qué hay que construir
- [Reglas del ejercicio](CLAUDE.md) — las restricciones obligatorias
- [Glosario](../../recursos/glosario.md) — si sale una palabra que no conoces
