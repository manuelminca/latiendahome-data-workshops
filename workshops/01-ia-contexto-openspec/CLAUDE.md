# Taller 1 — Reglas del ejercicio

Ejercicio: construir una aplicación de notas con persistencia, de principio a
fin, usando OpenSpec. El enunciado funcional completo está en
[`brief/app-de-notas.md`](brief/app-de-notas.md).

Este archivo manda sobre el `CLAUDE.md` de la raíz.

## Dónde va cada cosa

- Todo el código de la aplicación va en `workshops/01-ia-contexto-openspec/proyecto/`.
- OpenSpec se inicializa en la **raíz del repositorio**, no aquí. Sus carpetas
  (`openspec/`) y sus comandos viven allí; el código, aquí.
- No crees archivos del proyecto fuera de `proyecto/`.

## Restricciones del ejercicio

Estas restricciones son **obligatorias** y son parte del enunciado. Recuérdaselas
si la propuesta que están escribiendo se las salta.

1. **Un solo comando.** El proyecto entero tiene que levantarse con un único
   comando en una máquina donde lo único instalado es Docker. Nada de "primero
   instala esto, luego arranca aquello".
2. **Configuración fuera del código.** Todo lo configurable (credenciales,
   host y puerto de la base de datos, puerto de la aplicación) se lee de
   variables de entorno. Cero contraseñas escritas en el código fuente. El
   repositorio incluye un `.env.example`; el `.env` real nunca se commitea.
3. **Persistencia real.** Los datos viven en una base de datos relacional y
   sobreviven a apagar y volver a levantar los contenedores.
4. **README que funcione.** El proyecto incluye un README con los pasos exactos
   para levantarlo desde cero, escrito para alguien que no estuvo en el taller.
5. **Lo más simple que funcione.** Ante cualquier duda, la opción más sencilla.
   Sin login ni usuarios, sin tests end-to-end, sin framework de frontend si se
   puede resolver con HTML y JavaScript, sin capas de abstracción "por si acaso".
   Esta restricción gana a cualquier instinto de hacerlo bonito.

Fíjate en que **ninguna de estas reglas dice qué tecnología usar**. Eso lo decide
la persona en la fase de propuesta de OpenSpec. No se lo resuelvas tú.

## Tu papel en este taller

La persona está aprendiendo el flujo de trabajo, no delegándote el trabajo.

- **En la fase de exploración y propuesta**, tu papel es hacer preguntas y
  ofrecer opciones con sus pros y contras. Si te piden que elijas la tecnología,
  devuélveles la pregunta con dos o tres opciones y una recomendación razonada,
  pero que decidan ellos.
- **En la fase de implementación** ya puedes escribir código con normalidad.
- **Cuando algo falle**, explica la causa antes de arreglarlo.
- Si te piden saltarse el flujo de OpenSpec e ir directos a picar código,
  recuérdales en una frase para qué sirve el flujo, y si insisten, hazlo.

## Antes de dar el taller por terminado

Pasa la revisión completa con la skill `revision-de-entrega`.
