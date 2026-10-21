# Guía 1 — La práctica: 15 minutos

Vas a encargarle a Claude Code una tarea de verdad. Elige **un** ejercicio, el
que más se parezca a tu trabajo. Si te sobra tiempo, haz otro.

Todos los materiales están en la carpeta `practica/` y son **inventados**. No
uses datos reales de clientes ni de compañeros, tampoco "solo para probar".

---

## Antes de empezar (2 minutos)

1. En la pestaña **Code**, elige **Local** → **Select folder** → la carpeta
   `workshops/02-claude-code-en-tu-trabajo`.
2. En el selector que hay junto al botón de enviar, pon el modo **Manual**.
   Claude te pedirá permiso antes de crear cada archivo: léelo antes de
   aceptar.
3. Deja el modelo que viene por defecto.

**Para darle un archivo**, escribe `@` en la caja del mensaje y empieza a
teclear su nombre: te aparece una lista y eliges el archivo. También puedes
arrastrarlo a la caja del mensaje.

**La receta de un buen encargo**, que vas a usar en todos los ejercicios:

1. **Quién eres y para qué es**
2. **La tarea**, concreta
3. **El material**: el archivo o los datos
4. **Cómo quieres el resultado**: formato, extensión, tono
5. **Cuándo está bien**: lo que tiene que cumplir sí o sí

Cuando acabe, Claude te dará **un consejo** para pedirlo mejor la próxima vez.

---

## A · Comparar dos tarifas

*Para compras, producto, dirección o cualquiera que trabaje con Excel.*

Tienes las tarifas de dos proveedores inventados. Los productos se parecen,
pero cada uno los llama a su manera, y hay alguna trampa.

- `practica/tarifa-proveedor-ejemplo-norte.csv`
- `practica/tarifa-proveedor-ejemplo-sur.csv`

Un encargo de ejemplo, para que lo adaptes:

> Soy del equipo de compras y tengo que decidir a qué proveedor le compro cada
> producto. En @tarifa-proveedor-ejemplo-norte.csv y
> @tarifa-proveedor-ejemplo-sur.csv están sus tarifas. Empareja los productos
> equivalentes aunque se llamen distinto y dime cuáles no has sabido emparejar.
> Hazme un CSV separado por punto y coma, que se abra en Excel, con: producto,
> precio de cada proveedor, diferencia en euros, plazo de entrega de cada uno
> en días y cuál recomiendas. Guárdalo en practica/resultados/. Antes de
> empezar, pregúntame lo que necesites.

**Revisa:**

- ¿Se ha dado cuenta de que un proveedor da el plazo en **días** y el otro en
  **semanas**?
- ¿Ha emparejado bien "piel sintética" con "polipiel"?
- ¿Qué productos se han quedado sin pareja? ¿Te lo ha dicho?
- Abre el CSV en Excel y comprueba dos precios a mano.

## B · Resumir un documento largo

*Para tiendas, atención al cliente, logística o cualquiera que tenga que
explicar un procedimiento.*

`practica/procedimiento-entregas.md` es un procedimiento de entregas inventado.
Tiene algún error escondido.

> Trabajo en una tienda y los clientes me preguntan mucho por las entregas.
> Lee @procedimiento-entregas.md y hazme tres cosas: un resumen en cinco puntos
> que se lea en un minuto; las seis preguntas que más probablemente hará un
> cliente, con una respuesta corta y en lenguaje de cliente; y una lista de lo
> que se contradiga o no esté claro en el documento. Di de qué sección sale
> cada dato. Guárdalo en practica/resultados/.

**Revisa:**

- ¿Ha encontrado las **dos contradicciones**? Hay una sobre cuándo se confirma
  la cita y otra sobre el plazo para avisar de un daño.
- ¿Todas las respuestas salen del documento, o se ha inventado alguna?
- ¿Lo entendería un cliente que no sabe qué es un albarán?

## C · Mejorar una respuesta a una clienta

*Para atención al cliente, marketing o cualquiera que escriba a clientes o
proveedores.*

En `practica/borrador-respuesta-cliente.md` hay un correo de una clienta
inventada y el borrador de respuesta de un compañero. El borrador es mejorable.

> Soy de atención al cliente. En @borrador-respuesta-cliente.md está el correo
> de una clienta y el borrador de respuesta de un compañero. Reescribe la
> respuesta con un tono cercano y profesional: pide disculpas concretas por lo
> que ha pasado, no culpes al transportista y termina con un siguiente paso
> claro. Lo que podemos ofrecer: enviar una pata nueva en 5 días laborables o
> cambiar el sofá, y que un técnico revise la mancha. No prometas nada más.
> Máximo 150 palabras. Dame dos versiones y dime en qué se diferencian.

**Revisa:**

- ¿Promete algo que tú no le has dicho? Plazos, descuentos, regalos…
- ¿Cabe en 150 palabras?
- ¿La enviarías tal cual? Si no, díselo y pídele que la cambie.

## D · Tu propia tarea

Algo de tu trabajo que te lleve tiempo: un correo que te cuesta escribir, una
lista que ordenar, unas notas que convertir en un procedimiento, ideas para una
campaña.

**Sin datos personales.** Si tu tarea necesita datos de clientes, invéntatelos
o quítalos antes. Y si no se te ocurre nada, pregúntale a Claude:

> Trabajo en [tu departamento] de una empresa que vende muebles, sofás y
> colchones. Propónme cinco tareas de mi día a día en las que me podrías
> ayudar, sin usar datos de clientes.

---

## Si te sobra tiempo: pedir mal a propósito

Abre una sesión nueva (en la barra lateral) y pide el mismo ejercicio en una
sola frase: *"compara estas tarifas"*, *"resume esto"*, *"contesta a esta
clienta"*. Compara el resultado con el de antes. Esa diferencia es lo que
cuenta el bloque 5 de la presentación.
