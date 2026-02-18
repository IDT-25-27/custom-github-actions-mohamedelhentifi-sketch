## Step 6: Attiva & Prova

Fantastico! :rocket: Hai creato la GitHub Action Dad Jokes, definito i suoi metadati e creato un workflow per usarla.

L'unica cosa rimasta da fare è testarla!

### ⌨️ Activity: Prova la tua action

1. Crea un commento in questa issue (o crea una nuova issue) con il testo `/joke`

1. Monitora la scheda **Actions** finché il workflow `Joke Action` venga completato:

   <img width="400" alt="Screenshot of the Joke Action workflow run showing a successful completion" src="../images/joke-action-workflow-run.png" />


1. Torna alla issue e dovresti vedere un nuovo commento postato da `github-actions[bot]` contenente una dad joke casuale!

1. Octocat posterà la revisione dell'esercizio una volta che il tuo nuovo workflow Dad Joke sarà completato **con successo**!

   <details>
   <summary>Hai problemi? 🤷</summary><br/>

   Se il workflow non si attiva o fallisce:
   - Assicurati che il tuo commento inizi esattamente con `/joke`
   - Controlla la scheda Actions per messaggi di errore
   - Verifica che il tuo file `dist/index.js` esista e sia stato committato
   - Se hai fatto aggiornamenti al codice, assicurati di aver rimpachettato con `npm run build` e pushato le modifiche
   - Assicurati che il tuo file `action.yml` sia formattato correttamente

   </details>
