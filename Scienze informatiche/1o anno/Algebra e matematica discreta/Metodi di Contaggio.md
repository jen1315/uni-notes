(Matematica Discreta)

Il conteggio si basa su due principi fondamentali
1. Il principio di ADDIZIONE
	Dati un insieme con $r_{1}$ oggetti (si sottointende distinti tra loro),
		un insieme con $r_{2}$ oggetti, …
		un insieme con $r_{m}$ oggetti.
	Se questi insiemi sono A DUE A DUE DISGIUNTI (partiziono) allora
	Il numero di modi di selezionare un oggetto da uni degli $m$ oggetti è
	$r_1+r_2+…+r_m$
2. Il principio di MOLTIPLICAZIONE
	Dati un insieme con $r_{1}$ possibili esiti (si sottointende distinti tra loro),
		un insieme con $r_{2}$ possibili esiti, …
	    un Insieme con $r_3$ possibili esiti. Se
	1. Il numero di esiti di ciascuna fase è indipendente dagli esiti delle fasi precedenti
	2. Gli esiti finali delle procedure (“esiti finali” sono una composizione di esiti parziali) sono tutti distinti allora il numero di esiti finali è
	$r_{1}\cdot r_{2}…r_{m}$
	
	**NB.** È da tenere conto se si tenga conto se l’esito è ordinato o no.
### Permutazioni e Combinazioni semplici
Dato $n$ oggetti <u>DISTINTI</u>, $n\in\mathbb{N}$
> Una _PERMUTAZIONE SEMPLICE_ è una disposizione ordinata (un allineamento) di questi $n$ oggetti. Il numero di tutte le possibili permutazioni di $n$ oggetti è $P(n,n)=n!$

**NB.** Per convenzione si pone $0!=1$.

Sia $r\in\mathbb{N}\qquad0\leq r\leq n$
> Una _$r-$PERMUTAZIONE_ è un disposizione ordinata di $r$ degli $n$ oggetti.
> Il numero delle $r-$permutazioni di $n$ oggetti è $P(n,r)=n(n-1)(n-2)…(n-r+1)$.

**NB1.** $\displaystyle P(n,r)=n(n-1)(n-2)…(n-r+1)\cdot\frac{(n-r)!}{(n-r)!}$
	Quindi $\boxed{P(n,r)=\frac{n!}{(n-r)!}}$

**NB2.** Prendendo $r=n$ in NB1. 
	$\displaystyle P(n,n)=\frac{n!}{(n-n)!}=\frac{n!}{0!}=\frac{n!}{1}=n!$

> Una _$r-$COMBINAZIONE_ è una selezione <u>NON ORDINATA</u> di $r$ degli $n$ oggetti.
> Il numero delle possibili $r-$combinazioni di $n$ oggetti si indica $C(n,r)$.

In una $r-$permutazione
- prima scelgo $r$ oggetti da $n$, e lo posso fare in $C(n,r)$ modi
- poi ordino gli $r$ oggetti scelti, e lo posso fare in $r!$ modi

$\begin{align*}\text{Dunque }P(n,r)&=C(n,r)\cdot r!\\\Longrightarrow C(n,r)&=\frac{P(n,r)}{r!}\\&=\frac{n!}{(n-r)!}\cdot\frac{1}{r!}\underset{\text{si indica}}{=}\left({n\atop r}\right)\text{ coefficiente binomiale}\end{align*}$

**NB.** Per convenzione si pone 
	$\displaystyle\left({n\atop k}\right)=0\quad\text{se}\quad0\leq n<k$.

**La formula binomiale**
I coefficienti binomiali compaiono nella formula: 

$\boxed{\begin{align*}&\forall a,b\in\mathbb{Z},\ n\in\mathbb{N}\\&(a+b)^{n}=\sum_{k=0}^{n}\left({n\atop k}\right)n^{n-k}b^{k}\end{align*}}$
Infatti:
$(a+b)^{n}=\underbrace{(a+b)(a+b)…(a+b)}_{n\text{ volte}}$
usando la proprietà distributiva si scrive questo prodotto come somma di stringhe lunghe $n$ composte dalle lettere $a,b$.
La stringa $a\cdot a\cdot a …\cdot a$ compare in quanti modi puoi scegliere $b:\left({n\atop 0}\right)$ MAI
La stringa $a\cdot a\cdot a …\cdot b$ compare in quanti modi puoi scegliere $b:\left({n\atop 1}\right)$ 
La stringa $a\cdot a\cdot a …\cdot a$ compare in quanti modi puoi scegliere $b:\left({n\atop 0}\right)$ MAI

Corollario <u>TEOREMA (binomiale)</u>
$(1+x)^{n}=\sum_{k=0}^{n}\left({n\atop k}\right)x^{k}$

##### Identità binomiali
$n,x\in\mathbb{N},\quad k\leq n$
1. $\displaystyle\left({n\atop k}\right)=\left({n\atop n-k}\right)$
	\[Scegliere $k$ oggetti\] = \[scegliere gli $n-k$ oggetti da tralasciare\]
2. Sia $k\leq n-2$
	$\displaystyle\left({n\atop k}\right)=\left({n-1\atop k}\right)+\left({n-1\atop k-2}\right)$
	”Etichetto” uno degli $n$ oggetti in “oggetto giallo”
	Le scelte di $k$ oggetti tra quegli $n$ oggetti si dividono in 
	X = {scelte in cui l’oggetto giallo compare}
	Y = {scelte in cui l’oggetto giallo non compare}
	Allora $X\cap Y=\emptyset\qquad X\cup Y=$
	|X| = |{scelte di $k-1$ in }|
	|Y| = |{scelte di $n$ in }| 
3. $0\leq m\leq k\leq n$
	$\displaystyle\left({n\atop k}\right)\cdot\left({k\atop m}\right)=\left({n\atop m}\right)\left({n-m\atop k-m}\right)$
	1 modo 
	$\left({n\atop k}\right)\cdot\left({k\atop m}\right)=\left({\text{k elettori }\atop\text{}}\right)\left({k\atop m}\right)$

**Triangolo di Pascal (o Tartaglia)**
$n,k\in\mathbb{N}\quad k\geq0$
$\begin{array}{lcc}n=0&\left({0\atop 0}\right)&1\\ n=1&\left({1\atop 0}\right)\left({1\atop 1}\right)&1\ 1\\ n=2&\left({2\atop 0}\right)\left({2\atop 1}\right)\left({2\atop 2}\right)&1\ 2\ 1\\ n=3&\left({3\atop 0}\right)\left({3\atop 1}\right)\left({3\atop 2}\right)\left({3\atop 3}\right)&1\ 3\ 3\ 1\end{array}$

Ogni $\left({n\atop k}\right)$ “dentro” il triangolo, si trova tra 2 coefficienti binomiali nella riga precedente $\left({n-1\atop k-1}\right)\text{ e }\left({n-1\atop k}\right)$ ed è la loro somma.

### Permutazione e Combinazione con ripetizione

> Una _PERMUTAZIONE con RIPETIZIONI_ è una disposizione allineata di oggetti di cui <u>ALCUNI NON SONO DISTINGUIBILI</u>.

<u>TEOREMA</u> (numero di permutazioni con ripetizioni)
Dati $n$ oggetti, di cui
$r_1$ del tipo 1 (identici),
$r_2$ del tipo 2, …
$r_m$ del tipo $m$, tale che $r_1+r_2+…+r_m=n$
Il numero delle permutazioni di questi oggetti è
$\begin{align*}P(n;r_{1},r_{2},…,r_{m})&=\left({n\atop r_{1}}\right)\left({n-r_{1}\atop r_{2}}\right)\left({n-r_{1}-r_{2}\atop r_{3}}\right)…\left({r_{m}\atop r_{m}}\right)\\&=\frac{n!}{r_1!r_2!r_3!…r_m!}\end{align*}$

_COMBINAZIONE con RIPETIZIONI_
Quante sono le stringhe di lunghezza $r+(n-1)$
Composta da $X$ in numero di $r$ e
		  da $I$ in numero di $(n-1)$?
Diventa:
In quanti modi posso scegliere $r$ oggetti (la posizione delle $X$ nella stringa) ha $r+(n-1)$ oggetti 

**NB.** $\displaystyle C\left({r+(n-1)\atop r}\right)=C\left({r+(n-1)\atop n-1}\right)$
Data l’identità $\left({n\atop k}\right)=\left({n\atop n-k}\right)$

<u>TEOREMA </u>
Il numero di combinazioni con ripetizioni di $r$ oggetti di $n$ tipi diversi è$$C(r+(n-1),r)$$
##### Distribuzione di oggetti distinti
$r$ oggetti distinti
$n$ scatole distinte
1. In quanti modi si possono distribuire gli $r$ oggetti nelle scatole se ogni scatola può contenere un numero infinito di oggetti?
	NUMERO LE SCATOLE DA 1 A $n$
	$\underbrace{\begin{array}{cccc}n\text{ scelte}\\\downarrow\\\boxed{\ }&\boxed{\ }&…&\boxed{\ }\\\text{pos 1}&\text{pos 2}&&\text{pos }r\end{array}}_{\text{in tutto}}$
	Risposta: numero delle stringa di lunghezza $r$ in cui in posizione $i$ metto il nome della scatola che contiene l’oggetto $i$
2. In quanti modi si possono distribuire gli $r$ oggetti, richiedendo che nella scatola $i-$esima vengano posti $r_i$ oggetti.
	NUMERO LE SCATOLE DA 1 A $n$
	$\displaystyle\left({r\atop r_1}\right)\left({r-r_1\atop r_2}\right)…\left({r_n\atop r_n}\right)$
	
	RISPOSTA: il numero delle permutazioni di $n$ oggetti è 

##### Distribuzione di oggetti identici
$r$ oggetti identici
$n$ scatole distinte
In quanti modi si possono distribuire $r$ oggetti nelle $n$ scatole?

RISPOSTA: numero delle combinazioni con ripetizione di $r$ oggetti scelti tra $n$ variabili
$\displaystyle=C(r+(n-1),r)=\left({r+n-1\atop r}\right)$

### Relazione di Ricorrenza
Una _RELAZIONE DI RICORRENZA_ è una formula ricorsiva che conta il numero di modi per seguire una procedura con $n$ oggetti in funzione del numero di modi di eseguirla con un numero minore di oggetti. $$a_k=\text{ il numero di modi di eseguire la procedura con k oggetti}$$

NON POSSIAMO CALCOLARE RICORSIVAMENTE $a_n$ CON SE NON ABBIAMO LA CONDIZIONE INIZIALE.

La soluzione di una relazione di ricorrenza è una formula esplicita per $a_n$ e dipende da $n$ (e non $a_k$ precedenti).

Relazione di Fibonacci 
$\boxed{a_{n}=a_{n-2}+a_{n-1}}$  relazione di ricorrenza
Condizione iniziale: $a_{1}=1,\quad a_{2}=1$
$a_n=-\frac{1-\sqrt{5}}{2\sqrt{5}}(\frac{1-\sqrt{5}}{2})^{n}+\frac{1+\sqrt{5}}{2\sqrt{5}}(\frac{1+\sqrt{5}}{2})^n$
#### Relazioni di ricorrenza lineari omogenee
Sono relazioni di ricorrenza in cui $a_{n}$ viene espresso SOLO in funzione di alcuni $a_{k}$ con $k<n$.
Sono del tipo$$a_{n}+c_{1}\cdot a_{n-1}+c_{2}\cdot a_{n-2}+…+c_{r}\cdot a_{n-r}$$dove $c_{1},c_{2},…,c_{n}$ SONO COSTANTI E $c_{r}\neq0$.
Per poterle risolvere, occorrono <u>r condizioni iniziali</u> che permettono di calcolare $c_1,c_2,…,c_r$
$r=$ grado della relazione di ricorrenza

 Per risolvere:
 1. Porre $x^k$ al posto di $a_k$ relazione $x^n=c_{1}x_{r-1}+c_{2}x^{r-2}+…+c_{r}x^{k-r}$
 2. Divido per $x^{n-r}$
	 $x^r=c_{1}x^{r-1}+c_{2}x^{r-2}+…+c_{r-1}x+c_r$
	“EQUAZIONE CARATTERISTICA” DELLA RELAZIONE È
3. $x^{r}-c_{1}x^{r-1}-c_{2}x^{r-2}-…-c_{r-1}x-c_{r}=0$
	 ha grado $r$, per il Teorema Fondamentale dell’Algebra, ha $r$ soluzioni (in $\mathbb{C}$)

Siano $d_1,d_2,…,d_n$ le soluzioni DISTINTE dell’equi-caratteristica cin molteplicità $m_1,m_2,…,m_k$
$\begin{align*}0&=c_{1}x^{r-1}+c_{2}x^{r-2}+…+c_{r-1}x+c_r=&\\&=(x-\alpha_{1})^{m_{1}}(x-\alpha_{2})^{m_{2}}…(x-\alpha_{k})^{m_{k}}&\\&&m_1+m_2+…+m_k=r\end{align*}$

**NB.** $r=m_1+m_2+…+m_k$

 4. La soluzione generale della relazione di ricorrenza è l’insieme delle combinazioni lineari delle seguenti soluzioni:
	$\alpha_{1}^{n},n\alpha_{1}^{n},n^{2}\alpha_{1}^{n},…,n^{m_{1}-1}\alpha_{1}^{n}\leftarrow$ in questa riga ci sono $m_1$ soluzioni della relazione
	$\alpha_{2}^{n},n\alpha_{2}^{n},n^{2}\alpha_{2}^{n},…,n^{m_{2}-1}\alpha_{2}^{n}\leftarrow$ in questa riga $m_2$ soluzioni
	$\vdots$
	$\alpha_{k}^{n},n\alpha_{k}^{n},n^{2}\alpha_{k}^{n},…,n^{m_{k}-1}\alpha_{k}^{n}\leftarrow$ in questa riga $m_k$ soluzioni

    LA SOLUZIONE GENERALE: $a_{n}=A_{1}\alpha_{1}^{n}+A_{2}\alpha_{1}^{n}+…+A_{m_{1}}n^{m_{1}-1}\alpha_{1}^{n}+A_{m_{1+1}}\alpha_{2}^{n}+…+A_{r}n_{m_{k}-1}^m\alpha_{k}^{n}$
    dove $A_1,A_2,…A_r$ sono costanti
5. A questo punto determiniamo il valore delle costanti $A_1,A_2,…,A_r$ imponendo le $r$ condizioni iniziali
#### Relazioni di ricorrenza lineari non omogenee di 1o grado
Sono relazioni di ricorrenza del tipo:$$(*)\ a_n=ca_{n-1}+f(n)$$dove c’è una costante, $c\neq0$ e $f(n)$ è una funzione (in $n$) 
Per risolverle:
1. Si trova la soluzione generale della relazione di ricorrenza omogenea apposta a $(*)$
	$(**)\ a_n=ca_{n-1}$
	La soluzione generale di $(**)$ è $Ac^n$ CHE DETERMINERÒ SOLO ALLA FINE
2. Si somma alla soluzione generale di $(**)$, cioè a $Ac^n$, una “SOLUZIONE PARTICOLARE” $p(n)$ di $(*)$
	La soluzione generale di $(*)$ è $Ac^n+p(n)$

CI LIMITIAMO AI SEGUENTI 3 CASI:
- $f(n)=d\Longrightarrow p(n)=B$
- $f(n)=dn\Longrightarrow p(n)=B_1n+B_0$
- $f(n)=dn^{2}\Longrightarrow p(n)=B_2n^2+B_1n+B_0$

3. Le costanti vengono determinate alla fine imponendo le condizioni iniziali
#### Relazioni “Divide and Conquer”
Le relazioni _DIVIDE AND CONQUER_ sono relazioni di ricorrenza del tipo:$$a_{n}=ca_\frac{n}{2}+f(n)$$dove $c$ è una costante e $f(n)$ è una funzione di $n$.
LE SOLUZIONI DI ALCUNI CASI

| $c$         | $f(n)$ | $a_n$                                                       |
| ----------- | ------ | ----------------------------------------------------------- |
| $c=1$       | $d$    | $d[\log_{2}n]+A$                                            |
| $c=2$       | $d$    | $An-d$                                                      |
| $2\neq c>0$ | $dn$   | $\displaystyle An^{\log_{2}c}+\left(\frac{2d}{2-c}\right)n$ |
| $c=2$       | $dn$   | $dn+(\log_{2}n+A)$                                          |
