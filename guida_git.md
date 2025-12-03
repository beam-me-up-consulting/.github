# Rapida Guida a Git

## 🛠️ Fase 0: Preparazione (Da fare una volta sola)

Prima di iniziare a scrivere codice, dobbiamo configurare il vostro computer.

1.  **Installate Git:** Scaricate e installate Git da [git-scm.com](https://git-scm.com/).
2.  **Configurate la vostra identità:** Aprite il terminale (o Prompt dei comandi su Windows) e digitate questi due comandi, premendo Invio dopo ognuno:
    ```bash
    git config --global user.name "Il Tuo Nome e Cognome"
    git config --global user.email "latuaemail@esempio.com"
    ```
    *(Nota: Usa la stessa email con cui ti sei iscritto a GitHub)*

-----

## 🚀 Fase 1: Scaricare un progetto (Clone)

Per lavorare su un prototipo, devi prima scaricarne una copia sul tuo computer.

1.  Vai su GitHub, nella pagina del progetto (es. `github.com/beam-me-up-consulting/prototipo-alfa`).
2.  Clicca sul pulsante verde **Code**.
3.  Copia l'indirizzo HTTPS (quello che finisce con `.git`).
4.  Apri il terminale sul tuo computer, vai nella cartella dove vuoi salvare il progetto e scrivi:
    ```bash
    git clone INCOLLA_QUI_L_URL
    ```
5.  Ora hai una cartella con il progetto. Entraci dentro:
    ```bash
    cd nome-del-progetto
    ```

-----

## 🔄 Fase 2: Il lavoro quotidiano (La Regola d'Oro)

🔴 **IMPORTANTE:** Non lavoriamo mai direttamente sul ramo principale (`main`). Il ramo `main` è la versione "sacra" e funzionante del prototipo.
Per fare modifiche, creiamo sempre una copia parallela chiamata **Branch**.

### 1\. Crea il tuo spazio di lavoro (Branch)

Prima di scrivere anche solo una riga di codice, crea un nuovo ramo:

```bash
git checkout -b nome-tua-modifica
```

*Esempio:* `git checkout -b fix-colore-bottone` o `git checkout -b sensore-temperatura`.

### 2\. Lavora e Salva (Commit)

Ora modifica i file, scrivi codice, rompi le cose. Quando hai fatto un passo avanti:

  * **Prepara i file (Add):** Metti i file nella scatola.

    ```bash
    git add .
    ```

    *(Il punto `.` significa "aggiungi tutti i file modificati")*

  * **Sigilla la scatola (Commit):** Metti un'etichetta alla scatola.

    ```bash
    git commit -m "Descrivi qui cosa hai fatto"
    ```

    *Esempio:* `git commit -m "Aggiunta logica di lettura sensore"`

### 3\. Invia tutto online (Push)

Hai salvato sul tuo PC. Ora inviamolo su GitHub.

```bash
git push origin nome-tua-modifica
```

*(GitHub potrebbe chiederti di fare il login nel browser: fallo pure).*

-----

## 🤝 Fase 3: Unire il lavoro (Pull Request & Merge)

Ora il tuo codice è su GitHub, ma è isolato nel tuo ramo. Per portarlo nel progetto principale (`main`), devi chiedere il permesso.

1.  Vai sulla pagina GitHub del progetto.
2.  Vedrai un box giallo che dice **"Compare & pull request"**. Cliccaci.
3.  **Titolo:** Scrivi cosa fa la tua modifica.
4.  **Reviewers:** A destra, seleziona un collega che dovrà controllare il tuo lavoro.
5.  Clicca **Create Pull Request**.

### Cosa succede ora?

  * I tuoi colleghi riceveranno una notifica.
  * Guarderanno il codice e scriveranno commenti se c'è qualcosa da sistemare.
  * Una volta che tutto è ok, un collega (o tu, se autorizzato) cliccherà il pulsante verde **Merge Pull Request**.

🎉 **Fatto\!** Il tuo codice ora fa parte ufficialmente del prototipo.

-----

## 🔄 Fase 4: Tenersi aggiornati (Pull)

Mentre tu lavoravi, i tuoi colleghi potrebbero aver aggiornato il progetto principale. Prima di iniziare una nuova modifica, aggiorna sempre il tuo PC:

1.  Torna sul ramo principale:
    ```bash
    git checkout main
    ```
2.  Scarica le novità:
    ```bash
    git pull
    ```
3.  Ora puoi creare un nuovo branch e ricominciare il ciclo\!

-----

## 🆘 Glossario Rapido

  * **Repository (Repo):** La cartella del progetto.
  * **Branch (Ramo):** Una versione parallela del progetto dove puoi lavorare senza rompere nulla.
  * **Commit:** Un "salvataggio" con un messaggio.
  * **Push:** Caricare dal tuo PC -\> a Internet (GitHub).
  * **Pull:** Scaricare da Internet (GitHub) -\> al tuo PC.
  * **Merge:** Unire due rami (il tuo ramo -\> dentro il main).
