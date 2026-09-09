---
name: revision-de-entrega
description: Revisa si el proyecto de un taller cumple las restricciones del enunciado antes de darlo por terminado. Úsala cuando la persona diga que ha acabado, que quiere entregar, que quiere comprobar si le falta algo, o cuando pregunte si su proyecto está bien - y también antes de abrir el Pull Request de un taller.
---

# Revisión de entrega

Comprueba el trabajo contra las restricciones del taller y devuelve una lista
clara de qué pasa y qué no. **Esta skill revisa, no arregla**: primero enseña el
resultado completo, y solo arregla lo que la persona te pida después.

## Cómo hacerlo

Lee el `CLAUDE.md` de la carpeta del taller y el brief que hay en `brief/`. Esas
son las restricciones reales; lo que sigue es el mínimo común a todos los
talleres. Si el taller pide algo más, añádelo a la revisión.

Comprueba de verdad: ejecuta las cosas, no te fíes de que el archivo exista.

## Lista de comprobación

**Arranca desde cero**
Lo más importante y lo que más gente se salta. Simula a alguien que acaba de
clonar el repositorio: para todo (`docker compose down -v`), copia el
`.env.example` a `.env`, sigue **literalmente** los pasos del README y comprueba
que la aplicación levanta. Si tuviste que hacer algo que el README no dice, el
README está incompleto y eso es un fallo.

**Un solo comando**
Levantar el proyecto entero debe ser un comando, no una secuencia de siete.

**Configuración fuera del código**
Busca contraseñas, cadenas de conexión, hosts y puertos escritos a fuego en el
código fuente. Todo eso va en variables de entorno. Comprueba también que existe
`.env.example`, que están todas las variables que la aplicación usa de verdad, y
que **no** hay ningún `.env` a punto de commitearse (`git status`).

**Los datos persisten**
Crea un registro desde la interfaz, `docker compose down`, `docker compose up -d`,
y comprueba que sigue ahí. Si desaparece, no hay volumen y la persistencia es
falsa.

**La aplicación hace lo que pide el brief**
Recorre el brief funcional punto por punto y pruébalo en la interfaz, no en el
código. Incluye los casos raros que el brief mencione explícitamente.

**El README sirve**
Tiene que decir qué es el proyecto, qué necesitas instalado, cómo levantarlo y
en qué dirección se abre. Escrito para alguien que no estuvo en el taller.

**El repositorio está limpio**
Nada de `node_modules`, `.venv`, `__pycache__`, volúmenes de base de datos ni
archivos temporales en `git status`. Si aparecen, faltan reglas en el
`.gitignore`.

**Está todo dentro de la carpeta del taller**
Salvo lo que OpenSpec crea en la raíz, no debería haber archivos del proyecto
sueltos por el repositorio.

## Cómo dar el resultado

Un repaso corto, en este formato, sin adornos:

```
✅ Arranca desde cero con un solo comando
✅ Configuración en variables de entorno
❌ Los datos NO persisten — falta un volumen para Postgres en docker-compose.yml
⚠️  El README no dice en qué puerto se abre la aplicación
```

Usa ❌ solo para lo que incumple una restricción del enunciado y ⚠️ para lo
mejorable. Después de la lista, di en una frase si está listo para entregar o
qué falta. Si hay fallos, explica **por qué** cada uno importa antes de ofrecer
arreglarlo: el objetivo del taller es que se entienda, no que el marcador quede
en verde.
