# Guía 2 — La chuleta

Todo el taller en una página, para tenerla a mano cuando empieces a usar Claude
Code en tu trabajo.

---

## La receta de un buen encargo

1. **Quién eres y para qué es.** "Soy de atención al cliente y es para
   contestar a una clienta."
2. **La tarea, concreta.** "Reescribe esta respuesta", no "mira esto".
3. **El material.** El archivo con `@`, o arrastrado a la caja del mensaje.
4. **Cómo quieres el resultado.** Formato, extensión, tono.
5. **Cuándo está bien.** Lo que tiene que cumplir sí o sí, y lo que no puede
   hacer.

Plantilla para copiar:

```text
Soy [tu puesto] y necesito [para qué].
[La tarea, en una frase.]
El material está en @[archivo].
Quiero el resultado como [formato, extensión, tono].
Tiene que [lo imprescindible] y no puede [lo que no debe hacer].
Antes de empezar, pregúntame lo que necesites.
```

Y después: **revisa siempre**. Pídele de dónde sale cada dato y comprueba tú lo
importante.

## Qué modelo uso

| Modelo | Para qué | Precio relativo* |
|---|---|---|
| **Opus 5.5** | El que viene por defecto. Sirve para casi todo | 4× |
| **Sonnet 5.5** | Rápido y resolutivo, para el día a día | 2× |
| **Haiku 4.5** | Lo más rápido, para tareas sencillas y repetitivas | 1× |
| **Fable 5.1** | Solo para lo más difícil. Es más lento y, según el plan, se cobra aparte | 10× |

\* Precio por uso en la API de Anthropic, tomando Haiku como referencia. En tu
plan se nota en que la cuota se gasta antes.

Regla práctica: **empieza por el que viene**. Si falla, antes de cambiar de
modelo, mejora el encargo.

## El contexto

- **No pases del 30 % del contexto disponible.** Cuanto más lleno, más fácil
  que se le escape un detalle. Lo ves en el anillo que hay junto al selector de
  modelo, o con `/context`.
- **Si llegas:** `/compact` para resumir y seguir con la misma tarea, o una
  sesión nueva si vas a hacer otra cosa.

## Botones y comandos

| Para qué | En la aplicación | Escribiendo |
|---|---|---|
| Darle un archivo | Arrastrarlo a la caja del mensaje | `@nombre-del-archivo` |
| Ver cuánto contexto llevas | El anillo que hay junto al selector de modelo | `/context` |
| Resumir la conversación y liberar espacio | | `/compact` |
| Empezar de cero | Sesión nueva, en la barra lateral | `/clear` |
| Cambiar de modelo | El desplegable junto al botón de enviar | `/model` |
| Que piense más o menos | El menú de esfuerzo | `/effort` |
| Ver las skills y los comandos | Botón **+** → **Slash commands** | `/` |
| Conectar otras herramientas | Botón **+** → **Connectors** | |
| Instalar plugins | Botón **+** → **Plugins** | |
| Pararlo | El botón de parar | |

Puedes escribirle mientras trabaja para corregirlo: lo lee en cuanto termina
el paso en el que está.

## Modos de permiso

Se eligen en el selector que hay junto al botón de enviar.

| Modo | Qué hace |
|---|---|
| **Manual** | Te pregunta antes de cambiar un archivo o ejecutar algo. **Empieza aquí.** |
| **Accept edits** | Cambia los archivos sin preguntar y tú lo revisas después |
| **Plan** | Lee y te propone un plan, pero no cambia nada |
| **Auto** | Decide solo, con comprobaciones de seguridad. Para cuando tengas soltura |

## Local o en la nube

| | Local | Nube |
|---|---|---|
| Dónde trabaja | En tu portátil | En un ordenador de Anthropic |
| Qué archivos ve | Los de la carpeta que eliges | Una copia de un repositorio de GitHub |
| Si cierras el portátil | Se para | Sigue |
| Para qué | Tus documentos del día a día | Tareas largas sobre repositorios compartidos |

## Reglas de casa

- **Nada de datos personales** de clientes ni de compañeros: nombres con
  teléfono, DNI, direcciones, correos, exportaciones del CRM. Quita esas
  columnas antes o usa datos inventados.
- **Nunca contraseñas, claves ni tokens.**
- **Claude prepara, tú envías.** Nada llega a un cliente sin que lo lea una
  persona.
- **Lee lo que apruebas.** Aceptar sin leer es como firmar un albarán sin mirar
  el sofá.
- **Antes de instalar un plugin o conectar una herramienta, pregunta** al equipo
  de Data.

## Si te atascas

Pregúntale a Claude: *"¿cómo hago para…?"*. Si sale una palabra que no conoces,
está en el [glosario](../../../recursos/glosario.md). Y si no sale, escribe al
equipo de Data.
