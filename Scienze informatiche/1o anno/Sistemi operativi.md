A. S. Tanenbaum, H. Bos, I Moderni Sistemi Operativi

All’inizio il sistema operativo era l’operatore.
PDP-8 usabile con più terminali, quindi utenti in semi-parallelo.
Si gestisce la priorità e con I/O avviene esecuzione offline (indipendente dall’elaboratore) perché troppo lente.
Spooling (Simultaneous Peripheral Operation On-Line)

1969: primo messaggio da un computer all’altro
TCP/IP
Suddivisione pacchetti, Verifica errori, Controllo congestione

Data Lock-in: dati in formato proprietario apribile solo dalla casa produttrice.

Gestione delle interruzioni può essere polling, ovvero chiedere la conferma di pronto dei dispositivi ogni tanto (poco efficiente)
#### Definizione Sistema Operativo S/O
**Processo** è un programma in esecuzione.
- l’insieme ordinato di tutti i stati assunti nel corso dell’esecuzione o 
- l’insieme ordinato di tutte le azioni eseguite dal programma in corso dell’esecuzione
È una struttura dati formato da Codice, Dati temporanei e Stati.
Esso occupa uno spazio di indirizza mento logico/virtuale.

I diversi processi avanzano concorrentemente; devono comunicare e sincronizzarsi.
![[Pasted image 20240229134137.png]]Nella coda di Pronto, i processi hanno accesso a tutte le risorse tranne il processore.
Il KERNEL gestisce ed assicura l’avanzamento dei processi. La scelta dell’ordine ricade allo *scheduler*.
Si segue una politica di ordinamento fair

La Risorsa è un elemento hardware o software necessario al processo. Può essere
- durevoli
- consumabili
- accesso divisibile e indivisibile
- accesso individuale o molteplice

**CPU**, risorsa indispensabile per ogni processo
a livello logico può essere vista come **macchina virtuale** per ogni processo

**Memoria**
Write: risorsa accesso individuale
Read: risorsa accesso multiplo
Gestione software lo virtualizza (base-limite, usata insieme alla memoria secondaria)
Virtualizzata, diventa riutilizzabile e prerilasciabile

**Input/Output**
Generalmente riutilizzabile, non prerilasciabile, ad accesso individuale
Software specifici per dispositivi specifici (driver)
Controller nei dispositivi ha le sue informazioni fisiche

**Caricamento del S/O**
Viene caricato in RAM il sistema operativo all’avvio (Bootstrap)
ROM: i suoi contenuti sono permanenti e non modificabili. Ha il bootstrap loader.

Alla creazione del processo, viene creato anche il suo PCB (Process Control Block)
Il PCB sta nel Process Table e contiene
- Identificatore processo
- Contesto di esecuzione
- Priorità (iniziale e attuale)
- Diritti di accesso alle risorse e privilegi
- Puntatore al PCB padre e figli
- Puntatore alla lista delle risorse assegnate al processo
## Sincronizzazione
I processo spesso condividono risorse. Per gestirne l’accesso abbiamo bisogno di meccanismi di sincronizzazione.
 
Problema di **_Race Condition_**, quando il risultato finale dipende dalla temporizzazione della sequenza di processi.

Lo si risolve creando una situazione di _mutual exclusion_, ovvero nessun altro processo può accedere alla risorsa.

Possiamo risolverlo con
- Funzione di Peterson
```
	IN(int i) :: {
	int j = (1-i);
	flag[i] = TRUE;
	turn = i;
	while(flag[j] && turn==1)
	{ // attesa attiva };
	OUT(int) 
	}	
``` 
- Disabilitazione delle interruzioni,
	non conviene lasciare un controllo così potente all’utente
- _Test-and-Set-Lock_,
	supporto hardware con cui puoi leggere e cambiare il valore lock in una singola funzione atomica

Sia Peterson che TSL hanno un problema di busy-wait e possibile inversion priority, ovvero 
- Sleep and Wake
- 
**da Semaforo a Monitor**
W. Dijkstra propone una soluzione con l’oggetto Semaforo, 

_Message Passing_

Situazioni di rischio
- Stallo con blocco (**deadlock**)
- Stallo senza blocco (**starvation**)
- Esecuzioni non predicibili (**race condition**)

Le condizioni necessarie e sufficienti di uno _STALLO_ sono
1. Accesso esclusivo a risorsa condivisa
2. Accumulo di risorse
	processi accumulano risorse senza rilasciarne altre
3. Inibizione di pre-rilascio
	la risorsa deve essere rilasciata volontariamente
4. Condizione di attesa circolare
	processo in attesa di una risorsa in possesso da un processo successivo, a sua volta in attesa di una risorsa in possesso dal suo successivo così via ricorsivamente finché l’ultimo che va in attesa per quello del primo
	
Prevenzione
Riconoscimento
Indifferenza

Verifica Deadlock
- disegnando Grafo dell’Assegnazione delle Risorse
- verifica Stato Sicuro
	(Disponibili$_n$ + Assegnate$_{m\times n}$ + Necessità$_{m\times n}$) - Massimo$_{m\times n}$ >=0

Problemi classici di sincronizzazione
- **Filosofi a cena**, risorse condivise 
- **Lettori e scrittori**, database condiviso con accesso di lettori simultanei e del scrittore unico
- **Barbiere che dorme**, processi (clients) rimangono in attesa fino un numero limitato e vengono serviti (server)
- **Produttore e consumatore**, inserimento e prelevamento da buffer condiviso

## Ordinamento 
**Switch di processi**
- scambio cooperativo (senza pre-rilascio)
	scambio deciso dal processo
- scambio a pre-rilascio; processo corrente rimpiazzato per
	- un processo a priorità maggiore
	- tempo assegnato esaurito
_Scheduler_
Decide la politica di ordinamento dei processi.
_Dispatcher_
Esegue lo scambio tra processi seguendo le istruzioni dello scheduler.

L’efficienza delle politiche viene calcolata in base a
- Percentuale di impiego della CPU
- *Throughput*
	Processi completati per unità di tempo
- Tempo di *turn-around*
	Tempo di completamento
- Tempo di attesa
	Durata di permanenza in pronto
- Tempo di risposta 
	all’avvio di un processo
 
 I processi possono essere 
- **Batch**, ordinamento predeterminato, lavori di lunga durata e limitata urgenza, pre-rilascio non necessario
	Priorità: throughput, turn-around
	Politiche: FCFS (First Come First Serve), SJF (Shortest Job First), 
	SRTN (Shortest Remaining Time Next) 
	- SJF con pre-rilascio,
	- riordina i nuovi processi con quelli che rimangono da eseguire,
	- minimizza il tempo di attesa
- **Interattivo**, tempo di risposta rapido alle attività utente, pre-rilascio essenziale
	Priorità: tempo di risposta, user experience
	Politiche: Round Robin con priorità
	- Priorità con o senza pre-rilascio (entra al context-switch)
	GP (Garanzia per Processo), GU (Garanzia per Utente)
	- con pre-rilascio e garanzia di una dato tempo di esecuzione
	- esegue quelli con garanzie più importanti
	SG (Senza Garanzia)
	- ordine assegnato a lotteria, quelli con priorità più alta hanno più tiri
	- si stabilizza nella lunga durata
- **Real time**, ordinato per priorità, lavori di durata limitata e elevata urgenza, pre-rilascio possibile
	Priorità: deadline, predictability
	
Politiche Real time
- cyclic executive, $U=\sum_i(C_i/T_i)$ 
- ordinamento priorità fissa
	- problema di inversione priorità
	 Innalzamento della priorità 
BPI, il processo di priorità bassa necessari a una di priorità alta, eredita la priorità del processo alto
Non impedisce deadlock
ICP, 

Calcolo tempo di attesa($T_{\text{att}}$) e tempo di _turn-around_($T_{\text{ta}}$) medio.
$T_x(i)=$ Tempo di $x$ del processo $i$
$T_{\text{ta}}(i)=T_{\text{att}}(i)+T_{\text{esec}}(i)$

| Processo | $T_{\text{arrivo}}$ | $T_{\text{esecuzione}}$ | priorità |
| -------- | ------------------- | ----------------------- | -------- |
| A        | 0                   | 9                       | 3        |
| B        | 2                   | 1                       | 2        |
| C        | 5                   | 7                       | 4        |
| D        | 8                   | 3                       | 5        |
| E        | 11                  | 5                       | 1        |
<u>Politica FCFS (First Come First Serve)</u>
Esegui tutto il processo nello stesso ordine di arrivo.
```
[A A A A A A A A A]                          [] in esecuzione
 - - b b b b b b b[B]
 - - — - - c c c c c[C C C C C C C]
 - - - - - - - - d d d d d d d d d[D D D]
 - - - - - - - - - - - e e e e e e e e e[E E E E E]
```
$T_{att}(i)=(\sum_{j=1}^iT_{\text{esec}}(j))-T_{\text{arr}}(i)$
$T_{att}(\text{medio})=(7+5+9+9)/5=30/5=6$
$T_{ta}(\text{medio})=(9+(7+1)+(5+7)+(9+3)+(9+5))/5=54/5=10.8$

<u>Politica SJF (Shortest Job First)</u>
Esegui i processi ordinati con $T_{\text{esec}}$ crescente ($T_{\text{esec}}(i-1)<T_{\text{esec}}(i)\text{ e }T_{\text{arr}}(i)-T_{\text{arr}}(i-1)>=0\ \forall i\text{ processi}$).
```
[A A A A A A A A A]
 - - b b b b b b b[B]
 - - - - - c c c c c c c c c c c c c[C C C C C C C]
 - - - - - - - - d d[D D D]
 - - - - - - - - - - - e e[E E E E E]

A > B > D > E > C
```
$T_{att}(\text{medio})=(7+2+2+13)/5=24/5=4.8$
$T_{ta}(\text{medio})=(9+(7+1)+(2+3)+(2+5)+(13+7))/5=49/5=9.8$

<u>Politica SRTN (Shortest Remaining Time Next)</u>
```
[A A]a[A A A A A A A]
 - -[B]
 - - - - - c c c c c c c c c c c c c[C C C C C C C]
 - - - - - - - - d d[D D D]
 - - - - - - - - - - - e e[E E E E E]
```


<u>Politica Round-Robin</u>
Processi suddiviso in quanti di tempo($qt$) eseguite a rotazione.
```
\\ qt = 3ut
[A A A]a[A A A]a a a[A|A A]
 - - b[B]           | | in questa colonna A ha precedenza a D per attesa
 - - - - - c c[C C C]c|c c c c c c c c[C C C]c c c[C]
 - - - - - - - - d d|d|d d[D D D]
 - — - - - - - - - -|-|e e e e e e e e e e e[E E E]e[E E]
```
$qt_j(i)=(T_{\text{esec}}/qt)$
$T_{\text{att}}(i)=\sum_{j=1}^iqt(j)$
$T_{\text{ta}}(i)=T_{\text{att}}(i)+T_{\text{esec}}(i)$

<u>Politica Round-Robin con priorità</u>
La politica precedente alla quale vengono tenuti conto le priorità.
Senza pre-rilascio, finiscono il loro quanto di tempo
```
[A A A A A A]a a a a a a a a a a[A A A]
 - - b b b b b b b b b b b b b b b b b[B]
 - - - - - c[C C C]c c c[C C C C]
 - - - - - - - - d[D D D]
 - - - - - - - - - - - e e e e e e e e e[E E E E E]
```
Con pre-rilascio
```
[A A A A A]a a a a a a a a a a[A A A A]
 - - b b b b b b b b b b b b b b b b b[B]
 - - - - -[C C C]c c c[C C C C]
 - - - - - - - -[D D D]
 - - - - - - - - - - - e e e e e e e e e[E E E E E]
```
## Gestione memoria
I processi possono essere
1. allocati in modo fisso (MONOPROGRAMMATI)
2. allocati in momultiprocessi (MULTIPROGRAMMATI)

Mainframe, server robusto e grande
Supercomputer, elaboratore con grande capacità processuale

**Frammentazione**
- _Interna_, la memoria è suddivisa in blocchi uguali ma non tutti risultano del tutto riempiti
- _Esterna_, i blocchi variabili sono sparsi e non coprono tutta la memoria disponibile (anche lei segmentata)
Risultano in <u>sprechi di memoria</u>.

Multiprogrammati 
Blocchi suddivisi dall’inizio 

Rilocazione
Protezione, ci sono aree di memoria non permissibili.
- 4 bit di controllo
- rilocazione - protezione

#### Swapping
Spostare i processi in RAM per fare spazio.
Si possono rimuovere i processi già allocati e si salvano.

Per raffigurare la disposizione in memoria
- Bitmap, che mette 1 nei bit occupati e 0 nei bit liberi,
- Lista concatenata `[|bit inizio|lunghezza|punta lista successiva]`

Strategie allocazione con liste:
- _First Fit_, alla prima disponibilità
- _Next Fit_, alla prossima disponibilità
- _Best Fit_, nella disponibilità più adeguata
- _Worst Fit_, nella disponibilità più grande
- _Quick Fit_, liste diverse di ricerca per ampiezze ‘tipiche’

#### Memoria Virtuale
RAM insufficiente, processo caricato parzialmente con indirizzi relativi.
**MMU** li interpreta e mappa agli indirizzi fisici
Tutto trasparente alla CPU e programmatore

Tecniche
- Paginazione
	Memoria virtuale suddivisa in pagine
	RAM suddivisa in frame, grande quanto pagine
- Segmentazione

Thrashing, non c’è spazio per i processi necessari.
##### Paginazione
Politiche rimpiazzo
- **NRU** (Not Recently Used)
	Bit M (modified), R (referenced)
	- classe 0, non riferita e non modificata
	- classe 1, non riferita e modificata
	- classe 2, riferita e non modificata
	- classe 3, riferita e modificata
- **FIFO** (First In First Out)
	**Second Chance**, rimpiazza solo le pagine con R=0
- **Orologio**, lista circolare
- **LRU** (Least Recently Used)
	Ha bisogno di hardware dedicato
- **NFU** (Not Frequently Used)
	Contatore per l’uso della pagina, non viene mai resettato!
	**Aging**, NFU che resetta dopo N aggiornamenti

Nessuna delle politiche precedenti tengono conto 
> **Working Set** (WS), insieme di pagine che un processo usa in un dato istante.
- **WS approssimato**, simile a Aging
	Ogni page frame 
- **WS con orologio**

**_Anomalia di Belady_**, la possibilità per cui all’aumentare della RAM, aumentino anche i _page fault_.
Gli algoritmi immuni a questa anomalia (**stack algorithms**), soddisfano$$M(m,r)\supseteq M(m+1,r)$$dove m sono il numero di page frame e r i riferimenti.

Dobbiamo scegliere tra
- Politiche **Locali**
	Rimpiazzo del WS che ha 
- Politiche **Globali**

Come scegliere la dimensione della pagina?
**Calcolo dello spreco**$$f(\pi)=(\sigma/\pi)\cdot\epsilon+\pi/2$$$\sigma$ dimensione media di un processo
$\pi$ dimensione media di una pagina
$\epsilon$ grandezza di una riga in tabella delle pagine

Area SWAP
- Area per pagine temporaneamente rimpiazzate
- Usato per ibernazione

##### Segmentazione
Il programmatore deve esserne consapevole
Spesso i segmenti sono paginati.

Porta a problemi di.segmentazione esterna. Si deve ricompattatare.

## File System
Per accomodare
- Persistenza dei dati
- Condivisione dati
- Grandezza variabile dati
nella memoria secondaria.

Il _file_ è un concetto astratto di dato per la quale è utilizzabile indipendentemente dalla conoscenza della sua struttura.

File regolari
File catalogo (directory), descrive l’organizzazione dei file in cartelle
File speciali, indica i dispositivi I/O, usato in UNIX e GNU/Linux

Strutture di Directory
**a un livello**
Ogni file è elencato in una unica lista lineare.

**a due livelli**

 **ad albero**
 
 **a grafo**
 Il file può appartenere a più directory grazie all’uso di _collegamenti_

#### Realizzazione FS
L’unità su disco è un settore ma, vengono letti come blocchi.
C’è frammentazione.

Ogni partizione può avere un FS distinto ed è preceduto da una tabella descrittiva che specifica
- blocco boot
- superblocco
- lista liberi
- nodi indice
- root
- tutti gli altri file…

Un file è un insieme di blocchi su disco, possono allocati
- **Allocazione contigua**
	File memorizzati su blocchi consecutivi.
	Identificato dall’indirizzo del suo primo blocco e numero blocchi.
	Accesso sequenziale o diretto, letto in un solo accesso.
	Contro: ogni modifica ha rischio di frammentazione esterna.
- **Allocazione a lista concatenata**
	File in blocchi contenente puntatore al loro prossimo blocco File.
	Identificato dall’indirizzo al suo primo blocco (o ultimo).
	Accesso sequenziale ma, molti salti.
	Contro: un blocco corrotto, corrompe tutto il file.
- **Allocazione a lista indicizzata**
	File descritto dall’insieme dei puntatori ai suoi blocchi.
	Puntatori ai blocchi in struttura apposita.
	2 organizzazioni:
	- tabulazione **FAT** (File Allocation Table)
	- Indicizzata (**i-node**)
	Accesso sequenziale e diretto.
_FAT_


_i-node_
Usato da UNIX e GNU/Linux.

Gestione blocchi liberi
- bitmap, vettore di bit 0 (libero) o 1 (occupato) che indica lo stato dei blocchi a loro corrispondenti
- lista concatenata di blocchi liberi

Directory ha nome, collocazione e attributi.
