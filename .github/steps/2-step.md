## Step 2: Crea i file sorgente & Esegui localmente

Bene! Ora che il progetto è inizializzato e le dipendenze installate, è tempo di creare i file sorgente per la tua GitHub Action Dad Jokes.

### 📖 Theory: Il GitHub Actions Toolkit

La libreria `@actions/core` è la libreria principale del [GitHub Actions Toolkit](https://github.com/actions/toolkit), una raccolta di pacchetti per costruire GitHub Actions in JavaScript. Fornisce metodi essenziali per interagire con l'ambiente runtime di GitHub Actions, per accettare input e per produrre output per altri passaggi del workflow.

> [!TIP]
> Il [GitHub Actions Toolkit](https://github.com/actions/toolkit) include altre librerie utili come `@actions/github` per interagire con l'API di GitHub e `@actions/artifact` per caricare e scaricare artefatti.
>
> Puoi visitare il repository [actions/toolkit](https://github.com/actions/toolkit) per saperne di più.


### ⌨️ Activity: Implementa la Dad Jokes Action

Creiamo i file sorgente e implementiamo la logica per la action.

1. Crea la directory `src/` per contenere i file JavaScript:

1. Crea il file `src/joke.js` per contenere la logica per recuperare una battuta dall'API `icanhazdadjoke.com`:

   ```js
   const request = require("request-promise");

   const options = {
     method: "GET",
     uri: "https://icanhazdadjoke.com/",
     headers: {
       Accept: "application/json",
       "User-Agent": "Writing JavaScript action GitHub Skills exercise.",
     },
     json: true,
   };

   async function getJoke() {
     const res = await request(options);
     return res.joke;
   }

   module.exports = getJoke;
   ```

   La funzione `getJoke` effettua una richiesta HTTP GET all'API `icanhazdadjoke.com` e restituisce una dad joke casuale.

   Esportiamo la funzione `getJoke` in modo che possa essere utilizzata in altri file.

1. Crea `src/main.js` che sarà il punto di ingresso principale per la action:

   ```js
   const getJoke = require("./joke");
   const core = require("@actions/core");

   async function run() {
     const joke = await getJoke();
     console.log(joke);
     core.setOutput("joke", joke);
   }

   run();
   ```

   Chiamiamo la funzione `getJoke` e seguiamo con `core.setOutput()` per impostare l'output `joke` della GitHub Action.

1. Esegui la action localmente per verificare che funzioni:

   ```sh
   node src/main.js
   ```

1. Esegui il commit e il push:

   ```sh
   git add src/
   git commit -m "Add Dad Joke action source files"
   git push
   ```

1. Con le modifiche pushate su GitHub, Octocat controllerà il tuo lavoro e condividerà i passaggi successivi.
