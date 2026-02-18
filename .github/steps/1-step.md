## Step 1: Configurazione del progetto

Immagina di avere un compito ripetitivo che vorresti automatizzare. Hai cercato nel [**GitHub Marketplace**](https://github.com/marketplace?type=actions) per actions esistenti che potrebbero aiutarti, ma non hai trovato nulla...

Forse perché il tuo compito è più _unico_ che raro 💀

**GENERARE DAD JOKES**! 🎭

<img width="600" alt="dadjoke-mona" src="https://github.com/IDT-25-27/idt-25-27-classroom-173794-custom-github-actions-custom-github-actions/blob/main/.github/images/dadjoke-mona.png?raw=true" />

Poiché non esiste alcuna action pre-fabbricata per queste stravaganti esigenze di automazione, è tempo di rimboccarsi le maniche e crearne una tua!

### ⌨️ Activity: Configura il tuo ambiente di sviluppo

Usiamo **GitHub Codespaces** per configurare un ambiente di sviluppo nel cloud e lavorarci per il resto dell'esercizio!

1. Clicca con il tasto destro sul pulsante qui sotto per aprire la pagina **Create Codespace** in una nuova scheda. Usa la configurazione predefinita.

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

1. Conferma che il campo **Repository** sia la tua copia dell'esercizio, non l'originale, quindi clicca sul pulsante verde **Create Codespace**.

   - ✅ La tua copia: `/{{full_repo_name}}`
   - ❌ Originale: `/custom-github-actions`

1. Attendi un momento che Visual Studio Code si carichi nel tuo browser.

1. Verifica che **Node.js** sia disponibile aprendo un terminale ed eseguendo:

   ```sh
   node --version
   npm --version
   ```

   <details>
   <summary>Hai problemi? 🤷</summary><br/>

   - Assicurati di aver selezionato la tua copia personale del repository, non il template originale.
   - Se il Codespace non si avvia, prova ad aggiornare la pagina e a crearne uno nuovo.
   - Node.js e npm dovrebbero essere preinstallati nell'ambiente di sviluppo.

   </details>

### ⌨️ Activity: Inizializza il progetto

Ora che il tuo Codespace è pronto, inizializziamo un nuovo progetto Node.js e installiamo le dipendenze necessarie per la tua action Dad Jokes.

1. All'interno della finestra del terminale del tuo GitHub Codespace inizializza un nuovo progetto:

   ```sh
   npm init --init-type=module -y
   ```

1. Installa le librerie richieste:

   ```sh
   npm install request request-promise @actions/core @vercel/ncc
   ```

   > 🪧 **Nota:** Imparerai lo scopo di ogni libreria nei prossimi passaggi

1. Controlla `package.json` per confermare che le librerie siano elencate nella sezione `dependencies`.

1. Apri il file `.gitignore` e aggiungi una voce per escludere la directory `node_modules` dal tracciamento di Git:

   ```text
   node_modules/
   ```

   Non vogliamo aggiungere al commit `node_modules` perché contiene migliaia di file che appesantirebbero il repository.

   > 🪧 **Nota:** Invece, più avanti nell'esercizio pacchettizzerai la tua action in un singolo file JavaScript con tutte le dipendenze incluse.

1. Esegui il commit e il push delle tue modifiche:

   ```sh
   git status
   git add .
   git commit -m "Initialize project"
   git push
   ```

1. Con le modifiche pushate su GitHub, Octocat controllerà il tuo lavoro e condividerà i passaggi successivi.

<details>
<summary>Hai problemi? 🤷</summary><br/>

- Assicurati di essere nella root del repository prima di eseguire `npm init -y`.
- Non eseguire il commit di `node_modules/` nel repository; assicurati che sia elencato in `.gitignore`.

</details>
