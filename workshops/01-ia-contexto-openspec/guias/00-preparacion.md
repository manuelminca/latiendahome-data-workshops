# Guía 0 — Preparación

**Haz esto antes del día del taller.** Son unos 30 minutos, casi todo esperando
descargas. Si lo dejas para el momento, te pasas media sesión instalando cosas
en vez de haciendo el ejercicio.

Si algo falla, no te pelees: apúntalo y lo vemos al empezar.

Para los pasos que llevan comandos necesitas una terminal: en Mac, la aplicación
**Terminal**; en Windows, **PowerShell**. Búscala por el nombre y ábrela. A
partir del taller ya no la necesitarás, porque Claude Code trae una dentro.

---

## 1. Git

Comprueba si ya lo tienes:

```bash
git --version
```

Si responde con un número de versión, ya está. Si no:

- **Mac:** `xcode-select --install`
- **Windows:** descarga [Git for Windows](https://git-scm.com/download/win). En
  Windows es obligatorio: sin Git, Claude Code no puede trabajar en carpetas
  locales.
- **Linux:** `sudo apt install git`

**Dile quién eres.** Git firma cada cambio que guardas con un nombre. Pon el tuyo
real, aunque luego todos entremos a GitHub con la misma cuenta — así en el
historial se sabe quién hizo qué:

```bash
git config --global user.name "Tu Nombre Real"
git config --global user.email "tu.email@megashops.com"
```

## 2. Docker

Es lo que va a levantar la aplicación y la base de datos sin que tengas que
instalarlas en tu ordenador.

Descarga **Docker Desktop** desde [docker.com](https://www.docker.com/products/docker-desktop/),
instálalo y **ábrelo**. Tiene que estar abierto y en marcha; si no, todo lo demás
falla con errores raros.

Comprueba que funciona:

```bash
docker --version
docker compose version
```

Ojo: es `docker compose` (dos palabras), no `docker-compose`. La versión antigua
con guion ya no se usa.

## 3. Claude Code

Vamos a usar la **aplicación de escritorio**, no la terminal. Trae editor,
terminal, vista de cambios y navegador integrados, así que no tienes que ir
saltando entre ventanas.

1. Descárgala desde [claude.ai/download](https://claude.ai/download) e instálala.
2. Ábrela desde Aplicaciones (Mac) o el menú Inicio (Windows).
3. **Inicia sesión** con la cuenta de Anthropic que te hayamos dado.
4. Pincha en la pestaña **Code**, arriba en el centro.

> **Importante:** la pestaña Code necesita un plan de pago (Pro, Max, Team o
> Enterprise). Si al pincharla te pide mejorar el plan, avísanos antes del
> taller: es un problema de tu cuenta, no algo que puedas arreglar tú.

No hace falta instalar Node ni la versión de terminal de Claude Code: la
aplicación ya lo lleva todo dentro.

## 4. Node.js

Esto **sí** hace falta, pero solo porque lo necesita OpenSpec. Versión **20.19 o
superior**:

```bash
node --version
```

Si no lo tienes o tienes una versión anterior, descárgalo de
[nodejs.org](https://nodejs.org/) (la versión LTS) e instálalo.

## 5. OpenSpec

```bash
npm install -g @fission-ai/openspec@latest
```

Comprueba:

```bash
openspec --version
```

## 6. La cuenta de GitHub del taller

Para estos talleres usamos **una cuenta de GitHub común** para todo el mundo. Te
vamos a dar por separado el nombre de usuario y un *token de acceso* (una
contraseña larga que GitHub genera para usar desde la terminal).

> ⚠️ Ese token es una contraseña. No lo pegues en ningún archivo del
> repositorio, ni en un chat de grupo, ni en un documento compartido. Si acaba
> dentro de un commit, se queda en el historial de GitHub para siempre.

**Configúralo con la CLI de GitHub**, que es la forma más limpia:

1. Instala la [CLI de GitHub](https://cli.github.com/): en Mac,
   `brew install gh`; en Windows, `winget install GitHub.cli`.
2. Ejecuta:

   ```bash
   gh auth login
   ```

3. Responde así:
   - *What account do you want to log into?* → **GitHub.com**
   - *What is your preferred protocol?* → **HTTPS**
   - *Authenticate Git with your GitHub credentials?* → **Yes**
   - *How would you like to authenticate?* → **Paste an authentication token**
4. Pega el token que te hemos dado.

Es posible que salga un aviso diciendo que no puede determinar los permisos del
token, o algo sobre *scopes*. **Es normal, ignóralo**: pasa con el tipo de token
que usamos y no impide nada.

Comprueba que ha funcionado:

```bash
gh auth status
```

Tiene que decir que estás autenticado como el usuario del taller.

**Recuerda:** la cuenta de GitHub es compartida, pero tu identidad de Git (el
paso 1) es la tuya. Los commits van a llevar tu nombre real aunque la cuenta sea
común, así que en la revisión se sabe qué ha hecho cada uno.

## 7. El repositorio

Clónalo donde guardes tus proyectos:

```bash
git clone https://github.com/magashops/latiendahome-data-workshops.git
```

Apunta en qué carpeta te lo has dejado: el día del taller vas a tener que
seleccionarla desde Claude Code.

---

## Comprobación final

Ejecuta esto en la terminal. Si las cuatro líneas responden con una versión,
tienes las herramientas listas:

```bash
git --version && docker compose version && node --version && openspec --version
```

Y además:

- [ ] **Docker Desktop abierto** (tendrá que estarlo también el día del taller).
- [ ] **Claude Code abierto**, con sesión iniciada y la pestaña **Code**
      accesible sin que te pida mejorar el plan.
- [ ] **`gh auth status`** dice que estás autenticado.
- [ ] Sabes **en qué carpeta** has clonado el repositorio.
