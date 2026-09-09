# Enunciado — Aplicación de notas

Este es el documento que vas a usar como punto de partida en OpenSpec. Describe
**qué** tiene que hacer la aplicación. No dice **cómo** construirla: el lenguaje,
el framework, la base de datos y la forma de la interfaz los decides tú en la
fase de propuesta.

---

## En una frase

Una aplicación web sencilla para tomar notas: se pueden crear, ver, editar y
borrar, y siguen ahí cuando vuelves al día siguiente.

## Qué es una nota

Una nota tiene:

| Campo | Descripción |
|---|---|
| Identificador | Único, lo genera el sistema. La persona nunca lo escribe. |
| Título | Texto corto. Obligatorio. Máximo 120 caracteres. |
| Contenido | Texto largo. Opcional: una nota puede tener solo título. |
| Fecha de creación | La pone el sistema al crear la nota. No se puede modificar. |
| Fecha de última modificación | La actualiza el sistema cada vez que se edita la nota. |

## Qué tiene que poder hacer la persona que la usa

**Ver todas sus notas.** La pantalla principal muestra la lista de notas. Cada
una enseña al menos el título y la fecha de última modificación. Las más
recientemente modificadas aparecen primero.

**Crear una nota.** Hay una forma clara de crear una nota nueva desde la pantalla
principal. Al guardarla, aparece en la lista.

**Ver una nota entera.** Desde la lista se puede abrir una nota y leer su
contenido completo.

**Editar una nota.** Se pueden cambiar el título y el contenido de una nota que
ya existe. Al guardar, se actualiza su fecha de modificación.

**Borrar una nota.** Se puede eliminar una nota. Antes de borrarla, se pide
confirmación: borrar sin querer y no poder recuperarlo es una mala experiencia.

## Reglas y casos que hay que resolver

Estas son las situaciones que separan una aplicación terminada de una a medias.
Tu especificación tiene que decir qué pasa en cada una:

1. **Título vacío.** No se puede guardar una nota sin título, ni con un título
   que sean solo espacios. La aplicación lo impide y explica por qué; no se
   rompe ni guarda una nota en blanco.
2. **Título demasiado largo.** Más de 120 caracteres no se acepta. La persona se
   entera antes de perder lo que ha escrito.
3. **Lista vacía.** La primera vez que alguien abre la aplicación no hay notas.
   La pantalla no puede quedarse en blanco: dice que no hay notas todavía e
   invita a crear la primera.
4. **Contenido largo.** Una nota puede tener varios párrafos. La lista no debe
   descolocarse por eso: en la lista se ve un resumen, no el texto entero.
5. **Nota que ya no existe.** Si alguien abre el enlace de una nota que se ha
   borrado, la aplicación lo dice con claridad en lugar de dar un error feo.
6. **Los saltos de línea se respetan.** Si escribes el contenido en varios
   párrafos, al volver a leerlo siguen siendo varios párrafos.

## Cómo tiene que verse

No hace falta que sea bonita, pero sí que se entienda:

- Se usa desde el navegador.
- Se entiende sin instrucciones: al abrirla, queda claro qué es y qué puedes hacer.
- Cuando algo va mal, la aplicación lo dice con un mensaje en castellano
  entendible, no con un código de error.
- No hace falta que funcione bien en móvil, ni que tenga modo oscuro, ni
  animaciones.

## Restricciones técnicas

Están en el [`CLAUDE.md`](../CLAUDE.md) de este taller y son obligatorias.
Resumidas: un solo comando para levantarlo, configuración en variables de
entorno, persistencia real en base de datos relacional, README que funcione, y
la opción más simple que resuelva el problema.

## Fuera de alcance

Esto **no** entra. Si tu propuesta lo incluye, la estás complicando de más:

- Usuarios, login, registro o permisos. La aplicación es de una sola persona.
- Compartir notas, colaborar en tiempo real o notificaciones.
- Etiquetas, carpetas, favoritos o búsqueda.
- Adjuntar imágenes o archivos.
- Editor de texto enriquecido. Texto plano basta.
- Aplicación móvil.
- Despliegue en un servidor. Eso es el taller 2.

## Cuándo está terminada

Cuando puedas hacer esto de principio a fin sin tocar nada más:

1. Levantas el proyecto con un solo comando en una máquina limpia.
2. Abres el navegador y ves la pantalla de "no hay notas todavía".
3. Creas una nota, la editas, la abres y la ves bien.
4. Intentas guardar una nota sin título y la aplicación te lo impide con un
   mensaje claro.
5. Apagas los contenedores, los vuelves a levantar, y tus notas siguen ahí.
6. Borras una nota, te pide confirmación, y desaparece de la lista.
