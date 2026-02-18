## Step 4: Aggiungi i Metadati dell'Action

Ottimo lavoro! 🫡 Hai pacchettizzato con successo la GitHub Action Dad Jokes in un singolo file.

Ora è il momento di creare il **file di metadati della action** - questo file speciale dice a GitHub esattamente come usare la action quando qualcuno la include nel proprio workflow!

### 📖 Theory: Metadati dell'Action

Ogni GitHub Action richiede un file di metadati che definisce come la action deve essere eseguita e quali parametri accetta.

#### Requisiti del File di Metadati

Il file di metadati ha requisiti specifici:

- **Nome del file**: Deve essere `action.yml`
- **Richiesto per**: Tutti i tipi di action - JavaScript, [Docker container](https://docs.github.com/en/actions/tutorials/use-containerized-services/create-a-docker-container-action), e [action composta](https://docs.github.com/en/actions/tutorials/create-actions/create-a-composite-action)
- **Formato**: Scritto in formato YAML

#### Parametri Principali dei Metadati

| Parametro         | Descrizione                                                    | Richiesto |
| ----------------- | -------------------------------------------------------------- | :------: |
| **`name`**        | Il nome della action.                                          |    ✅    |
| **`description`** | Una breve descrizione di cosa fa la action.                    |    ✅    |
| **`author`**      | Il nome dell'autore della action.                              |    ○     |
| **`inputs`**      | Dati che la action si aspetta di ricevere.                     |    ○     |
| **`outputs`**     | Dati che i passaggi successivi nel workflow possono usare.     |    ○     |
| **`runs`**        | Dice a GitHub come eseguire la action.                         |    ✅    |
| **`branding`**    | Colore e icona per la action nel GitHub Marketplace.       |    ○     |

#### Configurazione `runs` per Action JavaScript

Per le action JavaScript, la sezione `runs` necessita di:

- **`using`**: Quale versione di Node.js usare
- **`main`**: Il file JavaScript principale da eseguire

> [!TIP]
> Per dettagli completi su tutti i parametri di metadati disponibili, campi opzionali e configurazioni avanzate, consulta la [documentazione ufficiale sulla sintassi dei metadati di GitHub Actions](https://docs.github.com/en/actions/reference/workflows-and-actions/metadata-syntax).

---

### ⌨️ Activity: Crea il File di Metadati

1. Crea `action.yml` nella root del repository (allo stesso livello di `package.json`).

   ```yaml
   name: "Joke Action"
   description: "Fetches a random joke and exposes it as an output"

   outputs:
     joke:
       description: "The fetched joke text"

   runs:
     using: node24
     main: dist/index.js
   ```

1. Esegui il commit e il push del file di metadati della action sul branch `main`:

   ```sh
   git add action.yml
   git commit -m "Add action metadata file"
   git push
   ```

1. Con le modifiche pushate su GitHub, Octocat controllerà il tuo lavoro e condividerà i passaggi successivi.