# Talleres de desarrollo con IA — La Tienda HOME

Este repositorio recoge los talleres internos para aprender a trabajar con
herramientas de desarrollo asistido por inteligencia artificial: Claude Code,
Git, especificaciones, entornos locales y despliegue.

No hace falta ser desarrollador para seguirlos. Cada taller explica lo que
necesitas saber en el momento en que lo necesitas.

## Talleres disponibles

| Taller | Qué aprendes | Duración |
|---|---|---|
| [01 · IA, contexto y OpenSpec](workshops/01-ia-contexto-openspec/) | Qué es un modelo, qué es el contexto, cómo se estructura un repositorio para que la IA trabaje bien, y construir una aplicación completa de principio a fin con OpenSpec | ~3 h |

## Antes de empezar

1. **Clona el repositorio** (una sola vez):

   ```bash
   git clone https://github.com/magashops/latiendahome-data-workshops.git
   ```

2. **Crea tu rama.** Nunca trabajes directamente sobre `main`. Cada participante
   tiene la suya, con el número de taller y su nombre:

   ```bash
   git checkout -b taller1/manuel
   ```

3. **Abre Claude Code** (la aplicación de escritorio), ve a la pestaña **Code**,
   elige **Local** y selecciona **la carpeta raíz del repositorio** — no la
   carpeta del taller. Esto importa: es lo que hace que las skills y el contexto
   común estén disponibles.

4. Entra en la carpeta del taller que toque y sigue su `README.md`.

## Qué hay en cada sitio

```
.claude/skills/     Skills compartidas por todos los talleres
recursos/           Glosario y material de consulta
workshops/          Un directorio por taller
```

## Cómo está montado cada taller

Todos siguen la misma estructura, para que a partir del segundo ya sepas dónde
está cada cosa:

```
workshops/NN-nombre/
├── README.md      El guion de la sesión: qué haces y en qué orden
├── CLAUDE.md      Las reglas del ejercicio (las lee la IA automáticamente)
├── guias/         Material de referencia: preparación, conceptos, herramientas
├── brief/         Qué hay que construir
└── proyecto/      Tu espacio de trabajo, vacío al empezar
```

## Si te atascas

Pregúntale a Claude Code. En serio: está configurado para explicar las cosas en
lenguaje llano y hay skills preparadas para los atascos más habituales, sobre
todo con Git y con Docker. Prueba a escribir literalmente "me he liado con git,
ayúdame" y verás.
