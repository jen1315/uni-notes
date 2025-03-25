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

> Un **Automa a Stati Finiti Deterministico (DFA)** è quintupla $$A=(Q,\Sigma,\delta,q_{0},F)$$- Q è un insieme finito di stati
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

**Operazioni sui linguaggi**
- Intersezione 
  $L\cap M=\{w:w\in L\text{ and }w\in M\}$
- Unione 
  $L\cup M=\{w:w\in L\text{ or }w\in M\}$
- Complemento 
  $\overline{L}=\{w:w\not\in L\}$
- Concatenazione 
  $L.M=\{uv:u\in L\text{ e }v\in M\}$
- Chiusura (o Star) di Kleene 
  $L^{*}=\{w_{1}w_{2}...w_{k}:k\geq0,\forall w_{i}\in L\}$
  L'insieme di tutte le parole possibili L ripetuti.

Se L e M sono linguaggi regolari, allora è $L\oplus M$ un linguaggio regolare? (*proprietà di chiusura*)

> Teorema: Se L e M sono regolari, allora anche $L\cap M$ è linguaggio regolare.

Dimostrazione: 
Con $A_{L}=\{Q_{L},\Sigma,\delta_{L},q_{L},F_{L}\}$ e $A_{M}=\{Q_{M},\Sigma,\delta_{M},q_{M},F_{M}\}$,

|       | 0   | 1   |     |       | 0   | 1   |
| ----: | --- | --- | --- | ----: | --- | --- |
| -> r0 | r1  | r0  |     | -> s0 | s0  | s1  |
|  * r1 | r1  | r1  |     |  * s1 | s1  | s1  |
vale la funzione di transizione, ovvero se $A_{L}$ va dallo stato p allo stato s leggendo a, e $A_{M}$ va dallo stato q allo stato t leggendo a, allora $A_{L\cap M}$ andrà dallo stato (p,q) allo stato (s,t) leggendo a ($A_{L}\times A_{M}$).

|           | 0      | 1      |
| --------- | ------ | ------ |
| -> r0, s0 | r1, s0 | r0, s1 |
| r1, s0    | r1, s0 | r1, s1 |
| r0, s1    | r1, s1 | r0, s1 |
| \*r1, s1  | r1, s1 | r1, s1 |
$A_{L\cap M}$ accetta una parola solo quando sia $A_{L}$ che $A_{M}$ accettano
$\Longleftrightarrow A_{L\cap M}$ accetta solo quando (p,q) è coppia di stati finali
L'insieme di stati è prodotto cartesiano.

> Un **Automa a Stati Finiti Non Deterministico (NFA)** ha
> - più transizioni con lo stesso simbolo
> - simboli senza transizioni uscenti
> - $\varepsilon$-transizioni che non consumano simboli
> Data una parola, ci sono più percorsi possibili. Si accetta se esiste *almeno un percorso* che arriva allo stato finale.
> 
> E' definito nello stesso modo del DFA. $$A=(Q,\Sigma,\delta,q_{0},F)$$- $\Sigma$ è un alfabeto finito che non contiene $\varepsilon$. Definiamo $\Sigma_\varepsilon=\Sigma\cup\{\varepsilon\}$
> - $\delta:Q\times\Sigma_\varepsilon\mapsto2^{Q}$ è una funzione di transizione che prende in input (q, a) e restituisce un sottoinsieme di Q

![](img/Pasted%20image%2020250305143823.png)

Data una parola $w=w_{1}w_{2}...w_{m}\text{ dove }w_{i}\in\Sigma_\varepsilon$,
una computazione di un NFA A con input w è una sequenza di stati $f_{0}f_{1}...f_{m}$ che rispetta due condizioni:
1. $r_{0}=q_{0}$ inizia dallo stato iniziale
2. $f_{i+1}\in\delta(r_{i},w_{i+1})$ per ogni $i=0,...,m-1$ rispetta la funzione di transizione
La computazione accetta la parola w se
3. legge tutti i simboli della stringa
4. termina in uno stato finale
Per nondeterminismo, ci possono essere più di una computazione!
La parola è accettata se esiste almeno una computazione che l'accetta.

DFA e NFA sono in grado di riconoscere lo stesso linguaggio. L'equivalenza si dimostra con la costruzione a sottoinsiemi. L'insieme di stati è l'insieme di tutti i sottostati possibili.

| NFA    | a           | b           | $\epsilon$  |
| ------ | ----------- | ----------- | ----------- |
| ->\*q1 | $\emptyset$ | q2          | q3          |
| q2     | q2, q3      | q3          | $\emptyset$ |
| q3     | q1          | $\emptyset$ | $\emptyset$ |

|           DFA | a             | b             |
| -------------:| ------------- | ------------- |
|  ->\*{q1, q3} | {q1, q3}      | {q2}          |
|          {q2} | {q2, q3}      | {q3}          |
|      {q2, q3} | {q1, q2, q3}  | {q3}          |
|  \*{q1,q2,q3} | {q1,q2,q3}    | {q2, q3}      |
|          {q3} | {q1, q3}      | {$\emptyset$} |
| {$\emptyset$} | {$\emptyset$} | {$\emptyset$} |

Per gestire le $\epsilon$ transizioni introduciamo la **$\epsilon$-chiusura** degli stati, ovvero tutti gli stati raggiungibili da q in una sequenza $\epsilon,\epsilon,...,\epsilon$.
$\begin{cases}r\in ECLOSE(q)&\text{se }p\in ECLOSE(q)\text{ e }r\in\delta(p,\epsilon)\\ q\in ECLOSE(q)&\text{altrimenti}\end{cases}$

> Teorema: Un linguaggio L è accettato da un DFA se e solo se è accettato da un NFA.

|   NFA | a             | b     | c   |
| ----: | ------------- | ----- | --- |
| -> q0 | q0            |       |     |
|    q1 | {$\emptyset$} | q1,q2 |     |
|  \*q2 |               |       | q2  |

|            DFA | a             | b             | c             |
| --------------:| ------------- | ------------- | ------------- |
| ->\*{q0,q1,q2} | {q0,q1,q2}    | {q1,q2}       | {q2}          |
|      \*{q1,q2} | {$\emptyset$} | {q1,q2}       | {q2}          |
|         \*{q2} | {$\emptyset$} | {$\emptyset$} | {q2}          |
|  {$\emptyset$} | {$\emptyset$} | {$\emptyset$} | {$\emptyset$} |

### Espressioni regolari
Un FA (NFA o DFA) è un metodo per costruire una macchina che riconosce linguaggi regolari.
Una **espressione regolare** è un modo dichiarativo per descrivere un linguaggio regolare.

$(0+1)\cdot(0\cdot1)^{*}=(\{0\}\cup\{1\}).(0.1)^{*}$
$\begin{align*}=\{&0,001,00101,0010101,\\&1,101,10101,1010101\}\end{align*}$

Le Espressioni Regolari sono costruite usando
costanti
- $\epsilon$ per stringa vuota
- $\emptyset$ per linguaggio vuoto
- $a,b,...$ per i simboli $a,b,...\in\Sigma$
collegati da operatori, qua ordinati per precedenza
1. \* per la chiusura di Kleene
2. . per concatenazione
3. + per unione
ragruppati usando le parentesi ( )

Sappiamo già che DFA e NFA sono equivalenti. Le espressioni regolari RE sono anche loro equivalenti ai FA.

*Conversione per eliminazione di stati*
Ogni volta che uno stato q viene eliminato, i cammini che passano per q scompaiono. Dobbiamo quindi sostituire ogni informazione che eliminiamo con nuove transizioni etichettate da espressioni regolari.

Automi nondeterministici generalizzati (GNFA)
1. c'è una transizione dello stato iniziale verso ogni altro stato e nessuna transizione entrante
2. unico stato finale senza transizioni uscenti e con una transizione da ogni altro lato
3. una transizione per ogni coppia di stati e un self loop verso se stesso
   $\delta'(q_{i},q_{j})=(\delta(q_{i},q_{rip})(\delta(q_{rip},q_{rip}))^{*}\delta(q_{rip},q_{j}))+\delta(q_{i},q_{j})$

> Un Automa a **Stati Finiti Non Deterministico Generalizzato (GNFA)** è una quintupla $$A=(Q,\Sigma,\delta,q_{start},q_{accept})$$- Q è un insieme finito di stati
> - $\Sigma$ è un alfabeto finito
> - $\delta:(Q\backslash\{q_{accept}\})\times(Q\backslash\{q_{start}\})\mapsto\mathcal{R}$ è una funzione di transizione che prende in input due stati e ritorna una espressione regolare
> - $q_{start}$ è lo stato iniziale
> - $q_{accept}$ è lo stato finale


Quanti stati ci sono nell'automa che riconosce il linguaggio $\{0^{n}1^{n}|n\geq0\}$?
Supponiamo $L_{01}$ sia regolare. Allora esiste un DFA $A=(Q,\Sigma,\delta,q_{0},F)$ che riconosce $L_{01}$. 
Sia k il numero di stati di A. Trova in input ad A la parola $0^{k}$
$\underbrace{q_{0}q_{1}q_{2}......\overbrace{q_{i}...q_{j}}^{p}...q_{k}}_{k+1\text{ stati}}$ la computazione di A
c'è uno stato che si ripete $p=q_{i}=q_{j}$
Cosa succede se A legge partendo da p?
Se l'automa finisce in uno stato finale, allora accetta, sbagliando $0^{j}1^{i}$
Se l'automa non finisce in uno stato finale, allora rifiuta, sbagliando $0^{i}1^{i}$

>Teorema: *Pumping Lemma per Linguaggi Regolari*
>Sia L un linguaggio regolare. Allora esiste una lunghezza k>0 tale che
>ogni parola $w\in L$ di lunghezza $|w|\geq k$ può essere spezzata in w=xyz tale che:
>1. $y\neq\epsilon$ (il secondo pezzo è non vuoto)
>2. $|xy|\leq k$ (i primi due pezzi sono lunghi max k)
>3. $\forall i\geq0,xy^{i}z\in L$ (possiamo "pompare" y rimanendo in L)