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
- untracked
- unmodified
- modified
- staged
- committed