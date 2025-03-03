Programma:
1. linguaggi regolari
	- automi a stati finiti
	- espressioni e linguaggi regolari
2. linguaggi liberi da contesto
	- grammatiche e linguaggi liberi dal contesto
	- automi a pila
3. indecidibilità e intrattabilità
	- macchine di Turing
	- concetto di indecidibilità
	- problemi intrattabili
	- classi P e NP

**Linguaggi formali**
- astrazione della nozione di problema
- problemi espressi come linguaggi (insieme di stringhe)
- o trasformazioni tra linguaggi
Tutti i processi computazionali possono essere ridotti in determinazione dell'appartenenza a un insieme e mappatura tra insiemi.

**Automi** sono dispositivi matematici astratti che possono
- determinare l'appartenenza di una stringa in un insieme
- trasformare una stringa in un'altra
Hanno tutti gli aspetti di un computer: i/o, memoria, capacità di prendere decisioni.
E' cruciale decidere se hanno *memoria finita o infinita*, con *accesso limitato o illimitato*.
## Automi a Stati Finiti
Hanno una quantità di memoria finiti.

*Alfabeto:* insieme finito e non vuoto di simboli ($\Sigma$)
*Stringa:* sequenza finita di simboli da un alfabeto
*Stringa vuota:* stringa con zero occorrenze di simboli da $\Sigma$
*Lunghezza di una stringa:* numero di simboli nella stringa

*Potenze di un alfabeto $\Sigma^{k}$:* insieme delle stringhe di lunghezza k con simboli da $\Sigma$
L'insieme di tutte le stringhe su $\Sigma$ è denominato $\Sigma^{*}=\bigcup\limits_{i=0}^{\infty}\Sigma^{i}$
*Linguaggio:* dato un alfabeto $\Sigma$, chiamiamo linguaggio ogni sottoinsieme $L\subseteq\Sigma^{*}$

> Un **Automa a Stati Finiti Deterministico (DFA)** è quintupla $$A=\{Q,\Sigma,\delta,q_{0},F\}$$- Q è un insieme finito di stati
> - $\Sigma$ è un alfabeto finito (= simboli di input)
> - $\delta:Q\times\Sigma\mapsto Q$ è una funzione di transizione
> - $q_{0}\in Q$ è lo stato iniziale
> - $F\subseteq Q$ è un insieme di stati finali

Possiamo rappresentare gli automi sia come *diagramma di transizione* che come *tabella di transizione*.

Data una parola $w=w_{1}w_{2}...w_{n}$ la computazione dell'automa A con input w è una sequenza di stati $r_{0}r_{1}...r_{n}$ che rispetta due condizioni:
1. $r_{0}=q_{0}$, inizia dallo stato iniziale
2. $\delta(r_{1},w_{i+1})=r_{i+1}$ per ogni $i=0,...,n-1$, rispetta la funzione di transizione
La computazione accetta la parola w se
3. $r_{n}\in F$, la computazione termina in uno stato finale