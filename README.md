# 📘 Manuale Operativo GitHub - [Beam Me Up]

**Benvenuti a bordo\!**
In Beam Me Up usiamo GitHub per conservare tutto il nostro codice. Immaginate GitHub come un "Google Drive per programmatori", ma molto più potente: tiene traccia di ogni singola modifica fatta nel tempo.
Se hai bisogno di una mano con le operazioni base di Git, dai un'occhiata alla [guida rapida](https://github.com/beam-me-up-consulting/beam-me-up-consulting/blob/main/guida_git.md). 

La sicurezza e l'organizzazione sono importanti quanto il codice. Per questo abbiamo diviso gli accessi in tre squadre distinte. Ecco dove ti posizioni tu e cosa puoi fare.

## 👥 I Nostri Team

### 1. 👑 Owners (Amministratori)
* **Chi sono:** I fondatori, il CTO o i responsabili tecnici.
* **Cosa vedono:** Tutto. Hanno le chiavi dell'intera "casa".
* **Poteri:**
    * Creare nuovi repository per nuovi prototipi.
    * Invitare o rimuovere persone dall'azienda.
    * Gestire i pagamenti e le impostazioni di sicurezza.
    * *Attenzione:* Sono gli unici che possono **cancellare** definitivamente un progetto (azione irreversibile!).

### 2. 🚀 Developers (Team Interno)
* **Chi sono:** Tutti i dipendenti e collaboratori stabili dell'azienda.
* **Cosa vedono:** Tutti i progetti interni dell'azienda. Se viene creato un nuovo prototipo domani, il team Developers lo vedrà automaticamente.
* **Poteri:**
    * Accesso in **Scrittura** (Write): possono modificare il codice, creare branch e aprire Pull Request.
    * Non possono cancellare i repository o cambiare le impostazioni dell'organizzazione.

### 3. 🎯 Contractors (Collaboratori Esterni)
* **Chi sono:** Freelancer, agenzie esterne o consulenti su progetti specifici.
* **Cosa vedono:** **Solo** i progetti a cui sono stati esplicitamente invitati. Non vedono gli altri prototipi, non vedono il codice "core" dell'azienda e non vedono chi sono gli altri contractor.
* **Poteri:**
    * Accesso limitato al singolo progetto.
    * Devono sottostare a controlli più rigidi (es. le loro modifiche devono essere sempre approvate da un Developer interno).

---

## ⚙️ I Flussi di Lavoro (Workflow)

Come ci muoviamo nella pratica quotidiana? Ecco due scenari tipici.

### Scenario A: Workflow standard (Per Developers)
*Situazione: Devi aggiungere una funzionalità al "Prototipo Alpha".*

1.  **Sync:** Scarichi le ultime novità (`git pull`).
2.  **Branch:** Crei il tuo ramo di lavoro (es. `feature-nuovo-menu`).
3.  **Code:** Lavori sul tuo PC.
4.  **Push & PR:** Carichi il ramo su GitHub e apri una **Pull Request**.
5.  **Review:** Chiedi a un collega (su Slack/Teams o direttamente su GitHub) di controllare.
    * *Collega:* "Tutto ok, approvato".
6.  **Merge:** Tu (o il collega) cliccate su **Merge**. Il codice è ora ufficiale.
7.  **Cleanup:** Cancelli il ramo `feature-nuovo-menu` (non serve più).

### Scenario B: Workflow "Ospite" (Per Contractors)
*Situazione: Un freelancer entra per sistemare un bug specifico sul "Prototipo Beta".*

1.  **Invito:** Un Owner invita il freelancer su GitHub e lo aggiunge *solo* al repository `prototipo-beta`.
2.  **Lavoro:** Il freelancer clona il repo, crea un branch `fix-bug-esterno`, lavora e fa il push.
3.  **Pull Request:** Il freelancer apre la Pull Request.
4.  **Blocco:** Il freelancer **NON può** fare il merge da solo. Il sistema lo blocca.
5.  **Controllo Interno:** Un membro del team **Developers** riceve la notifica, controlla il codice del freelancer per assicurarsi che rispetti gli standard aziendali e che non ci siano problemi di sicurezza.
6.  **Approvazione:** Solo il Developer interno può cliccare **Merge**.

---

## 🏷️ Regole di Nomenclatura (Come chiamiamo le cose)
Per mantenere l'ordine ed evitare di impazzire cercando i progetti, in [Nome Azienda] seguiamo una regola ferrea per i nomi dei repository.

### Le 3 Regole d'Oro della Sintassi:
1. Solo minuscolo (lowercase).
2. Usa i trattini (-) per separare le parole. Mai spazi o underscore.
3. Sii descrittivo ma breve.

Ecco gli schemi da usare in base al tipo di lavoro:

### 1. Progetti per Clienti
Usiamo il nome del cliente come prefisso per raggruppare i lavori.

  **Schema**: [nome-cliente]-[progetto]
  * ✅ valdichiana-chatbot-front-office
  * ✅ cimea-wiki
  * ❌ Sito Barilla Natale (No spazi, no maiuscole)
  * ❌ dashboard (Troppo generico, di chi è?)

### 2. Strumenti Interni
Per tutto ciò che serve a noi e non è venduto a terzi (gestionali, script, sito aziendale).

  **Schema**: internal-[nome-tool]
  * ✅ internal-chatbot-faq
  * ✅ internal-dashboard-demo

### 3. Esperimenti e R&D
Per i prototipi "usa e getta", i test di nuove tecnologie o idee che non hanno ancora un cliente.

**Schema**: exp-[nome-tecnologia-o-idea]
  * ✅ exp-test-realtavirtuale
  * ✅ exp-nuovo-sensore-lidar
  * ✅ poc-chat-ia (POC = Proof of Concept)

---

## 🛡️ La Regola di Sicurezza (Branch Protection)

Potreste notare che GitHub vi impedisce di fare alcune cose. Non è un errore, è una protezione che abbiamo attivato sul ramo principale (`main`).

**Le 3 Regole d'Oro del ramo `main`:**
1.  ⛔ **Divieto di Push Diretto:** Se provi a fare `git push origin main` dal tuo PC, GitHub rifiuterà il comando con un errore. *Devi sempre passare da una Pull Request.*
2.  👀 **Regola dei 2 Occhi:** Nessun codice entra nel `main` se non è stato approvato da almeno un'altra persona (Code Review). Non puoi approvare le tue stesse modifiche.
3.  ✅ **Check Passati:** Se in futuro aggiungeremo test automatici, il codice non potrà essere unito se i test falliscono (diventa rosso).

---

### 💡 Consiglio per tutti: Come scrivere una buona Pull Request
Quando aprite una Pull Request, aiutate chi deve controllarla. Non lasciate la descrizione vuota!

**Usa questo schema mentale:**
* **Cosa:** "Ho aggiunto il sensore di temperatura."
* **Perché:** "Serviva per il prototipo del cliente X."
* **Note:** "Ho dovuto modificare anche la libreria Y, verificate se va bene."
