---
name: entorno-local
description: Levantar, parar y diagnosticar el entorno local de un taller con Docker y variables de entorno. Úsala cuando haya que arrancar o reiniciar la aplicación o la base de datos, cuando algo no levante, cuando aparezcan errores de puerto ocupado, de conexión a base de datos o de contenedor que se reinicia solo, y cuando haya dudas sobre el archivo .env, las variables de entorno o los datos que desaparecen al reiniciar.
---

# Entorno local con Docker

Levantar el entorno es donde más gente se atasca y donde menos se aprende
peleando a ciegas. Diagnostica rápido, explica la causa, sigue adelante.

## Antes de tocar nada: mira

No propongas soluciones sin haber mirado el estado real. En este orden:

1. ¿Está Docker corriendo? (`docker info` falla si el demonio está parado —
   en Mac y Windows normalmente es que Docker Desktop no está abierto.)
2. ¿Qué contenedores hay y en qué estado? (`docker compose ps`)
3. ¿Qué dicen los logs? (`docker compose logs --tail=50`)

Los logs son la respuesta el 80% de las veces. Léelos antes de teorizar, y
enseña la línea concreta del error, no todo el volcado.

## Comandos base

| Qué quieres | Comando |
|---|---|
| Levantar todo | `docker compose up -d` |
| Levantar viendo los logs | `docker compose up` |
| Ver qué está corriendo | `docker compose ps` |
| Ver los logs | `docker compose logs -f` |
| Logs de un solo servicio | `docker compose logs -f <servicio>` |
| Parar todo | `docker compose down` |
| Parar y **borrar los datos** | `docker compose down -v` |
| Reconstruir tras cambiar el Dockerfile | `docker compose up -d --build` |

El `-v` de `down -v` borra los volúmenes, o sea la base de datos entera. Avisa
antes de usarlo y no lo ejecutes sin confirmación.

## Errores habituales y qué significan

**"port is already allocated" / "address already in use"**
Otro proceso ya está usando ese puerto. O es otro proyecto que se quedó
levantado (`docker compose down` en la otra carpeta), o es algo instalado en la
máquina, típicamente un Postgres local ocupando el 5432. La salida fácil es
cambiar el puerto del lado del host en el `docker-compose.yml`: el `5433:5432`
significa "el 5433 de mi máquina apunta al 5432 del contenedor".

**La aplicación no conecta con la base de datos**
Casi siempre es el nombre del host. Dentro de Docker, los servicios se llaman
entre sí por el **nombre del servicio** del `docker-compose.yml`, no por
`localhost`. Si el servicio se llama `db`, la cadena de conexión de la
aplicación tiene que apuntar a `db`, no a `localhost`. Desde fuera del contenedor
(por ejemplo un cliente de base de datos en tu portátil) sí es `localhost`.

**La aplicación arranca antes que la base de datos y se cae**
Postgres tarda unos segundos en aceptar conexiones. `depends_on` a secas solo
espera a que el contenedor exista, no a que esté listo. La solución correcta es
un `healthcheck` en el servicio de base de datos y un `depends_on` con
`condition: service_healthy`.

**El contenedor se reinicia en bucle**
Mira los logs de ese servicio. Suele ser una variable de entorno que falta o un
error de arranque de la aplicación.

**Los datos desaparecen al reiniciar**
No hay un volumen declarado para la base de datos, o se usó `down -v`. Sin
volumen, los datos viven dentro del contenedor y mueren con él.

**Cambio el código y no se ve el cambio**
O la imagen hay que reconstruirla (`--build`), o falta montar el código como
volumen para desarrollo.

## Variables de entorno

Explica el concepto la primera vez que salga: son valores de configuración que
viven **fuera** del código, para que el mismo código funcione en tu portátil y
en el servidor sin tocar nada, y para que las contraseñas no acaben en GitHub.

Reglas que se aplican siempre en estos talleres:

- El repositorio incluye un `.env.example` con todas las variables necesarias y
  valores de ejemplo, sin secretos reales. Ese archivo **sí** se commitea.
- Cada persona copia `.env.example` a `.env` y lo rellena. El `.env` **nunca**
  se commitea; ya está en el `.gitignore` de la raíz.
- Si añades una variable nueva, añádela también al `.env.example` en el mismo
  commit. Si no, al siguiente que clone el repo no le arranca.
- Si ves una contraseña, un token o una cadena de conexión escrita a fuego en el
  código, dilo y ofrece moverla a una variable de entorno.

Antes de dar por bueno un arranque, comprueba que las variables que pide el
`.env.example` están todas en el `.env`.

## Comprobación final

El entorno está bien montado si, partiendo de cero:

1. `docker compose up -d` levanta todo sin errores.
2. La aplicación responde en el navegador.
3. Creas un dato, haces `docker compose down` y luego `up -d`, y el dato sigue ahí.

Ese punto 3 es el que demuestra que la persistencia funciona de verdad. Hazlo
siempre antes de decir que está terminado.
