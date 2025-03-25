### Issue Tracking System (ITS)
*Issue* (criticità) = attività/evento da gestire
*Tracking* = registrare, lasciare delle tracce

> Un Issue Tracking System (ITS), detto anche support ticket issue system, gestisce e mantiene una lista di criticità. E' solitamente usata in un contesto collaborativo.

E' simile a un bugtracker e vengono spesso usati insieme.

A cosa serve?
- condivisione di informazioni con il team di sviluppo, il project manager e il cliente
- unico repository dove trovare le informazioni
- processo per misurare la qualità del progetto
- istantanea dello stato del progetto: attività da fare, in corso e completare
- assegnare priorità alle attività
- segna il tempo impiegato sulle attività (utile per stime)
- ogni attività ha un proprio responsabile
- memoria storica di tutti i cambiamenti del progetto

Un *Work Item* è un'attività "atomica" del progetto gestito mediante un workflow e mantenuto in un unico repository.

Un *Workflow* è l'insieme di stati e transizioni che un Work Item attraversa durante la sua vita. Permette di implementare il processo da seguire per completare un'attività e di definire la relazione tra work item.

![](img/Pasted%20image%2020250303125435.png)
### Version Control System (VCS)

> Il Version Control System (VCS) gestisce il versionamento offrendo un'informazione univoca del file. Anche detto Source Code Management System (SCM).
> - registrano tutte le modifiche di un insieme di file
> - condivisione del codice e modifiche
> - trecciamento e merge

Perché li usiamo?
- offrono l'intera storia del codice, possibile rollback
- facilita l'individuazione e risoluzione di conflitti
- collaborare senza interferenze (branching)

Ci sono 3 diverse versioni di VCS
1. locali, database dentro l'IDE
2. centralizzati, in un server
3. distribuiti
Ora vengono usati solo quelli distribuiti

I VCS locali registrano solo la storia del codice e non gestiscono la condivisione.
I VCS centralizzati sono come quelli locali ma in un server, offrendo la condivisione. Tuttavia quando essa cade, tutto il sistema VCS cade ed è solo possibile fare commit al master.

I VCS distribuiti è duplicato per ogni nodo. Offre diversi metodi di issue tracking e workflow che favoriscono la condivisione.
#### Terminologia
Ogni insieme di righe modificate in un singolo file è detta *DIFF*.
Un insieme di diff che sono esplicitamente convalidate sono un *COMMIT*.
L'ultimo commit sulla storia è *HEAD*.

![](img/Pasted%20image%2020250303090654.png)
*BRANCH* sono i rami in cui si trova il codice. Per integrare un branch al master, si ha un *merge*.
*Pull Request* chiede di seguire un merge al branch master. Permette di commentare.

Ci sono diverse tipologie di workflow
- **centralizzato**, non ha funzionamento di merge e si deve gestire conflitti in locale pausando commit al server con un *checkout*
- **feature branch**, abbiano un branch per feature
	- <u>gitflow</u>
	  il *master branch* viene solo usato per codice rilasciato
	  il *development branch* viene usato per codice da portare a rilascio
	  ci sono *feature branches* per ogni feature da mergere quando pronta
	  il *release branch* è usato per i testing
	- <u>github</u>, simile a gitflow ma che merge i feature branch direttamente al master dopo una pull request
	- <u>gitlab</u>, simile a github ma con pre-produzione e poi produzione
- **forking branch**, usato nei progetti open-source
  si fa fork ovvero copia del repository open-source dove lavorare. Non si ha accesso diretto al master. Si deve fare pull request al master per contribuire al codice, dove viene giudicato dall'amministratore del progetto.
### Git
E' piccolo e veloce, sviluppato in C. Usa il modello distribuito.

**working directory** -git add-> **staging area** -git commit-> **repository (locale)**
nello staging area vengono convalidati i file prima del commit

A differenza dei diff, git fa uno snapshot di tutti i file in un dato momento a cui poi fa link.

un file può avere uno dei 3 stati
- untracked, nuovo e non versionat
- unmodified, non modificato rispetto alla versione precedente
- modified, modificato rispetto alla versione precedente
- staged, salvata come snapshot nella staging area
- committed, salvato dalla staging area alla repository locale

![](img/git-transport.webp)

non si possono chiudere le issue via commit
git config pull.rebase false
git pull origin master > sistemo conflitti
`> git merge [--no-ff] new-feature` 
`[--no]` per bypassare  al main locale quando vengono solo aggiunti file

### SCRUM
E' un metodo agile per la quale si producono anche poche righe di codice alla volta per rispondere subito agli obiettivi e per presentare al cliente qualcosa di funzionante per ogni sessione (*sprint*).

Il metodo inverso a quello agile è chiamato waterflow per la quale si ritorna al cliente solo quando si è finito tutto.

I requisiti sono trattati come elementi di una lista detta *product backlog*.
Si basa su attività empiriche per cui si risolvono solo cose a cui si hanno le conoscenze necessarie.

Persone e iterazioni > Processi e strumenti
Software funzionante > Documentazione ampia
Collaborazione con il cliente > Negoziazione del contratto
Risposta al cambiamento > Seguire un piano

![](img/Scrum-Process-414428007.jpg)
Per ogni punto del Product Backlog ne scrivo n per lo Sprint Backlog.

Prodotto progettato, realizzato e testato durante lo sprint.
Requisiti -> Progetto -> Codifica -> Test
Piuttosto che fare di tutto, si fa un pezzetto del tutto alla volta

Non si cambia durante lo sprint
Alla fine dello sprint c'è una fase di revisione e rischio per cui lo sprint backlog può essere chiarito e rinegoziato con il product owner.

**Ruoli**
- *Product Owner*
  può essere o lato cliente o lato dell'azienda
  è responsabile della redditività del prodotto (ROI) ovvero se siamo in positivo o negativo
  responsabile del product backlog
  accetta o rifiuta i risultati del lavoro
- *Scrum Master*
  rappresenta la conduzione del progetto SCRUM
  protegge il gruppo di lavoro da interferenze esterne e assicura che il gruppo di lavoro è pienamente operativo e produttivo
  mediatore tra product owner e il development team
- *Development Team*
  tipicamente di 5-9 persone
  competenze trasversali: programmatori, tester, progettisti di user experience, sistemisti, etc

**Eventi**
- *Sprint Planning*
  8 ore prima dello sprint
  scompongo i punti del product backlog in user stories e poi in punti per lo sprint backlog
  si definiscono il cosa, il come e si stima il tempo necessario
- *Daily Scrum Meeting*
  breve incontro giornaliero di 15 minuti (circa) in piedi
  aggiornamenti della situazione per lo scrum master
  non serve per risolvere problemi
  si rispondono a 3 domande
  1. cosa hai fatto ieri?
  2. cosa farai oggi?
  3. c'è qualcosa che ti impedisce di farlo?
- *Sprint Review*
  4 ore al termine dello sprint
  si presenta il lavoro compiuto al cliente, tipicamente con una demo
  informale: si evitano slides
  partecipa tutto il gruppo e anche esterni
- *Sprint Retrospective*
  3 ore dopo lo sprint review
  si valuta lo sprint appena concluso e si parla di cosa ha funzionato o no
  partecipa tutto il gruppo (anche product owner)

Sprint goal: obiettivo che assegnamo a uno sprint
Definizione di Done: ogni gruppo assegna una definizione di done
Criterio di accettazione: permette di confermare se la storia è completa e funziona come dovuto; frasi semplici condivise tra product owner e development team

#### Build automation

#### Software testing
La fase di testing e quella di sviluppo devono andare di passo a passo.
Il test è un'indagine che da informazioni sulla qualità del software e del servizio messo a test.

> Testing (nella definizione di International Software Testing Qualification Board):
> Il processo che consiste su tutte le attività del ciclo di vita, sia *statiche* che *dinamiche*, interessate con la pianificazione, preparatione ed evaluazione di prodotti software e lavori correlati per determinare che soddisfino i requisiti specificati, dimostrare che sono adatti per lo scopo e trovare difetti.

**Categorie di testing**
- *Funzionale*: condotti per valutare la conformità a requisiti funzionali. Reappresentano cosa fa la nostra applicazione.
  *Non funzionale*: condotti per valutare la conformità a requisiti non funzionali come performance, sicurezza, usabilità e accessibilità. Rappresentano come la nostra applicazione risponde alle esigenze.
- *Statico*: analisi del prodotto senza l'esecuzione del codice
  *Dinamico*: collaudo con esecuzione del software
- *Verifica*: realizzato secondo le specifiche tecniche e funziona correttamente. Conforme ai suoi obiettivi 
  *Validazione*: realizzato rispettando le specifiche dell'utente

Definizione di caso di test
I casi di test aiutano a ridurre l'ambiguità nei requisiti, migliorando la descrizione. Sono i testable requirements.

**Processo di test**
1. *Test planning*, creare o aggiornare un test plan
2. *Test control*, controllare se il piano è rispettato
3. *Test analysis*, cosa testare
4. *Test design*, come testare
5. *Test implementation*, definizione casi di test
6. *Test execution*, esecuzione
7. *Checking result*, verificare che i risultati e capire se il test è superato
8. *Evalutating exit criteria*, verificare se sono stati raggiunti gli exit criteria definiti nel test plan
9. *Test results reporting*, segnare il progresso rispetto agli exit criteria
10. *Test closure*, chiusura del processo e definizione di azioni di miglioramento

7 principi di un test
1. Test rivelano presenza di difetti
2. Test esautivi non esistono
   il rischio(risk based) e le priorità(priority based) vengono usati per concentrarsi sugli aspetti più importanti
3. Test il prima possibile
4. Clustering dei difetti
   regola del 80/20, 80% degli errori nel 20% del codice
5. Il paradosso dei pesticidi
   rifare i test passati con l'evoluzione del sistema
6. Test dipendono dal contesto
7. Assenza di errori non è garanzia

V-model

Unit testing
Test sul sottosistema più piccolo possibile. 
E' un test white box, ovvero abbiamo accesso al codice.

Integration testing
Verificano che i contratti di interfaccia tra più moduli e sottinsiemi siano rispettati e se i sottoinsiemi atomici sono ben integrati. E' white box.

System testing
Verificano il comportamento dell'intero sistema rispetto alle specifiche tecniche. Può essere white o black box.

Acceptance testing (UAT, User Acceptance testing)
Relativo agli use cases e ai requisiti concordati con il cliente.
E' un test black box.