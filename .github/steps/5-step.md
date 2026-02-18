## Step 5: Crea Workflow & Consuma Output

Ben fatto! :clap: Hai creato la GitHub Action Dad Jokes e definito i suoi metadati.

La action dovrebbe essere pronta per l'uso in qualsiasi repository GitHub ora!

### ⌨️ Activity: Crea Workflow

Vediamo la action Dad Jokes in azione creando un workflow GitHub Actions che la utilizza!

1. Crea un nuovo file workflow GitHub Actions con il seguente nome

   ```txt
   .github/workflows/joke-action.yml
   ```

1. Aggiungi il seguente contenuto al file workflow:

   ```yaml
   name: Joke Action
   run-name: {% raw %}Dad Joke for issue ${{ github.event.issue.number }} by ${{ github.event.comment.user.login }}{% endraw %}

   on:
    issue_comment:
      types: [created]

   permissions:
    issues: write
    contents: read
  
   jobs:
     joke:
       if: startsWith(github.event.comment.body, '/joke')
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v5
         - name: Get Joke
           id: get-joke
           uses: ./
         - name: Create comment
           uses: peter-evans/create-or-update-comment@v5
           with:
            issue-number: {% raw %}${{ github.event.issue.number }}{% endraw %}
            body: {% raw %}${{ steps.get-joke.outputs.joke }}{% endraw %}
   ```

   Questo workflow si attiva per tutti i nuovi commenti alle issue nel repository.

   A causa del condizionale `if`, il job `joke` viene eseguito solo se il commento inizia con `/joke`.

1. Esegui il commit e il push del file workflow sul branch `main`:

   ```sh
   git add .github/workflows/joke-action.yml
   git commit -m "Add workflow to test joke action"
   git push
   ```


1. Con il workflow pushato su GitHub, Octocat controllerà il tuo lavoro e condividerà i passaggi successivi.