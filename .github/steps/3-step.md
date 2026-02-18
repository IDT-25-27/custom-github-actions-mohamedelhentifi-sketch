## Step 3: Bundle dell'Action

Ottimo lavoro! 🫡

Ora che hai creato i file sorgente per la GitHub Action Dad Jokes, ed è stata testata localmente, è tempo di pacchettizzare la action in modo che possa essere utilizzata nei GitHub workflows.

### 📖 Theory: Pacchettizzare la tua Action

Quando qualcuno usa la action nel proprio workflow, GitHub la scarica ed esegue come un pacchetto completo di codice. Ciò significa che devi includere tutte le dipendenze del pacchetto necessarie per eseguire il codice JavaScript, come i pacchetti `@actions/core` e `request-promise` utilizzati dalla action.

Piuttosto che committare la directory `node_modules` (che causa problemi di dimensioni del repository e prestazioni), puoi utilizzare strumenti di bundling come `@vercel/ncc` per combinare il tuo codice e le dipendenze in un singolo file `dist/index.js` per la distribuzione.

### ⌨️ Activity: Configurazione Build & Bundle

1. Aggiungi un nuovo script `build` nel `package.json` (all'interno dell'oggetto `scripts`):

   ```json
   "scripts": {
      // Script esistenti...
     "build": "ncc build src/main.js -o dist"
   }
   ```

1. Esegui il comando di build. Questo dovrebbe creare una directory `dist/` con un file `index.js` pacchettizzato:

   ```sh
   npm run build
   ```

1. Esegui la action pacchettizzata per verificare che funzioni:

   ```sh
   node dist/index.js
   ```

1. Esegui il commit e il push delle modifiche sul branch `main`:

   ```sh
   git add .
   git commit -m "Add ncc build script and bundled dist/index.js"
   git push
   ```

1. Con le modifiche pushate su GitHub, Octocat controllerà il tuo lavoro e condividerà i passaggi successivi.