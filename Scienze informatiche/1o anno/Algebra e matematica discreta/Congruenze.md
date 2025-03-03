Contenuto: 
- Algebra
	1. [[Congruenze#Classi di congruenza|Congruenze]] e sistemi di congruenze (1 comp)
		Interi moduli *n* (es. ore a 12)
	2. [[Matrici e Vettori|Matrici]], operazioni sulle matrici, uso nella risoluzione di sistemi naturali (1 comp)
	3. [[Matrici e Vettori#Spazi vettoriali complessi e reali|Spazi vettoriali]] (somma e moltiplicazione)
	4. Diagonalizzazione (2 comp) 
- Matematica discreta
	1. [[Grafi]] (1 comp)
	2. Metodi di conteggio (2 comp)
	3. Relazioni di ricorrenza (2 comp)

### Insieme numerici
$\begin{aligned}\mathbb{N}&=\text{Insieme di numeri naturali}\\ &=\{0,1,2,…\}\end{aligned}$ 
$\begin{aligned}\mathbb{Z}&=\text{Insieme di numeri interi}\\ &=\{…,-2,-1,0,1,2,…\}\end{aligned}$
$\begin{aligned}\mathbb{Q}&=\text{Insieme dei numeri razionali}\\ &=\Big\{\frac{m}{n}|m.n\in\mathbb{Z},n\neq0\Big\}\end{aligned}$
$\mathbb{R}=\text{Insieme dei numeri reali}$
tutti i numeri che corrispondono ai punti su una retta in cui si sia fissato un sistema di coordinate ascisse

Il problema della soluzione di equazioni
$x-1=0\Longrightarrow x=1$ In equazioni di 1o grado in $\mathbb{R}$
$x^2-1=0\Longrightarrow x^2=1$ 2 soluzioni distinte
$x^2-2x+1\Longrightarrow\underbrace{(x-1)^2}_{(x-1)(x-1)}=0\qquad x_1=x_2$
$x^2+1=0\Longrightarrow$ nessuna soluzione in $\mathbb{R}$

$\mathbb{N}\subseteq\mathbb{Z}\subseteq\mathbb{Q}\subseteq\mathbb{R}\subseteq …$
Amplifico $\mathbb{R}$, introducendo un insieme di numeri per risolvere $x^2+1$

#### Numeri complessi
Introduciamo un numero, che indichiamo con il simbolo $i$, e che chiamiamo UNITÀ IMMAGINARIA tale che $$i^2=-1$$$i$ è soluzione dell’equazione $x^2=-1$.
Quindi l’equazione $x^2=-1$ ha due soluzioni: $i$ e $-i$.

Un NUMERO COMPLESSO è una numero del tipo $$z=a+ib,\text{ con }a,b\in\mathbb{R}$$$a=$ parte reale di $z$
$b=$ parte immaginaria di $z$

Osservazione: tutti i numeri reali sono numeri complessi.

$\mathbb{C}=$ insieme dei numeri complessi $=\{a+ib|a,b\in\mathbb{R}\}$
$\mathbb{R}\subseteq\mathbb{C}$

**Somma e Prodotto**
$z,w\in\mathbb{C}$
$z+w=(a_z+a_w)+(ib_z+ib_w)$
$z\cdot w=(a_z+ib_z)(a_w+ib_w)=a_z\cdot a_w+a_z\cdot ib_w+ib_z\cdot a_w+ib_z\cdot ib_w$

N.B: $z=a+ib,\ w=c+id\qquad z=w\Longleftrightarrow\begin{cases}a=c\\ b=d\end{cases}$
N.B.: $z=a+ib\qquad z\neq 0\Longleftrightarrow\begin{cases}a=0\\ b=0\end{cases}$

**Rappresentazione di un numero complesso nel piano di Gauss**
Numeri reali nelle ordinate
Numeri immaginari puri($z=ib$) nelle ascisse

Definizione: se $z=a+ib\in\mathbb{C}$, si chiama **CONIUGATO** di $\mathbb{Z}$ il numero$$\bar{z}=a-ib$$ “ribalta il numero rispetto all’asse x”

Proprietà della coniugazione
1. somma $\overline{z_1+z_2}=\overline{z_1}+\overline{z_2}$
2. prodotto $\overline{z_1\cdot z_2}=\overline{z_1}\cdot\overline{z_2}$
3. $\bar{\bar{a}}=a$
4. $\bar{a}=a$ solo per $a$ reali

Con numero immaginario $z$, si chiama **MODULO** di $z$, la lunghezza del segmento $$|z|=\sqrt{a^2+b^2}$$Proprietà del modulo
1. $|z|^2=z\cdot\overline{z}$
2. prodotto $|z_1\cdot z_2|=|z_1|\cdot|z_2|\qquad\forall\ a_1,z_2\in\mathbb{C}$
3. somma $|z_1+z_2|\leq|z_1|+|z_2|\qquad\forall\ z_1,z_2\in\mathbb{C}$ 
	(disuguaglianza triangolare)

**Inverso di un numero complesso**
$\frac{1}{a-ib}=$

### Divisione nei numeri $\mathbb{N}$ e $\mathbb{Z}$
**Divisione nei $\mathbb{N}$**
Siano $a,b\in\mathbb{N},\ b\neq0$. Allora esistono e sono unici due numeri naturali
- $q$ detto QUOZIENTE e
- $r$ detto RESTO. Tali che $$a=b\cdot q+r\qquad\text{con }r<b$$
NB1. Dimostrabile con induzione.
NB2. 

**Divisione in $\mathbb{Z}$**
Siano $a,b\in\mathbb{Z},\ b\neq0$. Allora esistono e sono <u>unici</u> due numeri interi
- $q$ detto QUOZIENTE e
- $r$ detto RESTO. Tali che $$a=b+r\qquad\text{con }0\leq r<|b|$$
NB1. Senza la condizione di r, non c’è unicità.
NB2. La dimostrazione è simile a quella dei numeri naturali
NB3. Se $a,b\in\mathbb{Z},b\neq0$ allora $|a|,|b|\in\mathbb{N},|b|\neq0$
Non c’è nessun nesso tra il quoziente ed il resto della divisione di $a$ e $b$ e il modulo 

xcasa: es3 foglio 1

**Divisibilità in $\mathbb{N}$**
Siano $a,b\in\mathbb{N},\ b\neq0$. Si dice che $b$ è DIVISIBILE per $a$ se $a=b\cdot q$ per un opportuno $q\in\mathbb{N}$

NB. $a,b\in\mathbb{N},\quad a\neq0\neq b$
$\begin{cases}a/b\\ b/a\end{cases}\Longrightarrow a=b$

**Divisibilità in $\mathbb{Z}$**
Siano $a,b\in\mathbb{Z},\ b\neq0$. Si dice che $b$ è DIVISIBILE per $a$ se $a=b\cdot q$ per un opportuno $q\in\mathbb{Z}$.

NB. $a,b\in\mathbb{Z},\quad a\neq0\neq b$
$\begin{cases}a/b\\ b/a\end{cases}\Longrightarrow|a|=|b|$

### Massimo Comune Divisore per $\mathbb{N}$ e $\mathbb{Z}$
**MCD in $\mathbb{N}$**
Siano $a,b\in\mathbb{N}$ non entrambi nulli. Si dice che $d\in\mathbb{N}$ è il MASSIMO COMUNE DIVISORE di $a$ e $b$ se è
1. (un divisore comune di $a$ e $b$)
2. (un multiplo di tutti i divisori comuni di $a$ e $b$)

Osservazione: il numero 0 è diviso da ogni numero $\mathbb{N}$. Quindi non esiste un MCD di $0/0$.

NB1. In $\mathbb{N}$, il massimo comune divisore è <u>unico</u>.
NB2. Siano $a,b\in\mathbb{N}$, non entrambi nulli. $MCD(a,b) = MDC(b,a)$
NB3. Siano $a,b\in\mathbb{N}$, con $b\neq0$. Se $b/a$ allora b=MCD
NB4. Siano $a,b\in\mathbb{N}$, con $b\neq0$. Siano $q,r$ quoziente e resto della divisione $a/b$, $$a=b\cdot q+r\qquad0\leq r<|b|$$ allora $\boxed{MCD(a,b)=MCD(b,r)}$

Cushi
**MCD in $\mathbb{Z}$**
Siano $a,b\in\mathbb{N}$ non entrambi nulli. Si dice che $d\in\mathbb{N}$ è un MASSIMO COMUNE DIVISORE di $a$ e $b$ se è
1. $d|a$ e $d|b$ 
2. se $z|a$ e $z|b$ per qualche $z\in\mathbb{Z}$ allora $z|d$
Se $d$ è un massimo comune divisore di $a$ e $b$ si scrive

NB1. In $\mathbb{Z}$ “il” MCD è individuato a meno del segno. (Se $d=MCD(a,b)$ allora $-d=MCD(a,b)$).
NB2. In $\mathbb{Z}$, se $a,b\in\mathbb{Z},\ b\neq0$$$a=bq+r\quad\text{con }0\qquad\text{allora}\qquad\boxed{MCD(a,b)=MCD(b,r)}$$NB3. $a,b\in\mathbb{Z}$ NON ENTRAMBI NULLI
$MCD(a,b)=MCD(-a.b)=MCD(a,-b)=MCD(-a,-b)$
- se $a=0=b,\ \not\exists MCD(a,b)$

##### Calcolo del MCD in $\mathbb{N}$
(algoritmo di Euclide)
Dati $a,b\in\mathbb{N}$ con $a\neq0\neq b$, descriviamo un algoritmo che permette di calcolare $MCD(a,b)$ Consiste in una sequenza di divisioni successive.
<u>1o PASSAGGIO</u>: Si divide $a$ per $b:\exists q_1,r_1\in\mathbb{N}$ tali che$$a=b\cdot q_1+r_1\quad\text{con }0\leq r_1<b\quad\Longrightarrow MCD(a,b)=MCD(b,r_1)$$$\boxed{\text{SE }r_1=0}$ allora $MCD(a,b)=MCD(b,0)=b$ e l’algoritmo si ferma.
$\boxed{\text{SE }r_1\neq0}$ l’algoritmo continua.
<u>2o PASSAGGIO</u>: si divide $b$ per $r_1:\exists q_2,r_2\in\mathbb{N}$ tali che$$b=r_1\cdot q_2+r_2\quad\text{con }0\leq r_2<b\quad\Longrightarrow MCD(b,r_1)=MCD(r_1,r_2)$$$\boxed{\text{SE }r_1=0}$ allora $MCD(b,r_1)=MCD(r_1,0)=r_1$ e l’algoritmo si ferma.
$\boxed{\text{SE }r_1\neq0}$ l’algoritmo continua.
…
IL MCD È L’ULTIMO RESTO NON NULLO DELLA SEQUENZA DI DIVISIONI SUCCESSIVE.

##### Calcolo del MCD in $\mathbb{Z}$
<u>1o MODO</u>:
- $|a|,|b|\in\mathbb{N}$
- $MCD(|a|,|b|)=d\in\mathbb{N}$
- $d$ e $-d$ sono $MCD(a,b)$ in $\mathbb{Z}$
<u>2o MODO</u>: 
l’algoritmo di Euclide in $\mathbb{Z}$, ovvero una sequenza di divisioni successive in $\mathbb{Z}$ (tutti i resti siano $\geq0$) a cui si prende l’ultimo resto non nullo. Allora $d$ e $-d$ sono $MCD(a,b)$ di $\mathbb{Z}$.

### Polinomi
$S\in\{\mathbb{Z},\mathbb{Q},\mathbb{R},\mathbb{C}\}$
$S[x]=$ insieme dei polinomi nella indeterminata $x$ ed a coefficienti in $S$.
$f(x)\in S[x]$
$f(x)=a_0+a_1x+a_2x^2+…+a_nx^n$ per opportuni $\underbrace{a_0,a_1,…,a_n}_{\text{coefficienti di }f(x)}\in S$
SE $a_n\neq0$ il GRADO di $f(x)$ è $$\deg f(x)=n$$e $a_n$ si chiama il COEFFICIENTE DIRETTORE di $f(x)$.

NB1. $\begin{cases}c\in S\\ c\neq0\end{cases}\Longrightarrow\deg f(c)$
NB2. $c=0\Longrightarrow$ per CONVENZIONE $\deg 0=-\infty$

**Somma di polinomi**
$f(x),g(x)\in S[x]$ definisco $f(x)+g(x)$ nel seguente modo
$f(x)=a_0+a_1x+a_2x^2+…+a_nx^n$
$g(x)=b_0+b_1x+b_2x^2+…+b_mx^m$  dove $m\leq n$
$f(x)+g(x)=(a_0+b_0)+(a_1+b_1)x+…+(a_m+b_m)x^m+…+(a_n+b_n)x^n$

NB. $\boxed{\deg(f(x)+g(x))\leq\max\{\deg f(x),\deg g(x)\}}$ 

**Prodotto di polinomi**
$f(x),g(x)\in S[x]$ definisco $f(x)\cdot g(x)$ nel seguente modo
$\begin{align*}f(x)\cdot g(x)&=(a_0+a_1+a_2+…+a_n)(b_0+b_1+b_2+…+b_m)=\\ &=a_0b_0+(a_0b_1+a_1+b_0)x+(a_0b_2+a_1b_1+a_2b_0)x^2+…+a_nb_mx^{n+m}\\&=\sum_{j=0}^{m+n}\Big(\sum_{k=0}^ja_kb_{j-k}\Big)x^j\end{align*}$

NB. $\deg f(x)g(x)=\deg f(x)+\deg g(x)$
perché in $S$ vale LA LEGGE DELLA CANCELLAZIONE DEL PRODOTTO.

**Divisioni di polinomi**
$S\in\{\mathbb{Q},\mathbb{R},\mathbb{C}\}\qquad\text{NB.}S\not\in\mathbb{Z}$
$\forall f(x),g(x)\in S[x]\quad\boxed{\text{con }g(x)\neq0}$ 
ESISTONO e sono UNICI $q(x),r(x)\in S[x]$ tali che

$f(x)=g(x)\cdot q(x)+r(0)$

| $\begin{align*}&7x^4+0x^3+0x^2+3x-2\\ &7x^4+7x^3+7x^2\end{align*}$   | $x^2+x+1$ |
| -------------------------------------------------------------------- | --------- |
| $\begin{align*}/\quad &-7x^3-7x^2+3x-2\\ &-7x^3-7x^2-7x\end{align*}$ | $7x^2-7x$ |
| $\qquad/\qquad/\qquad\ \ \ 10x-2$                                    |           |
NB. Non si può fare in $\mathbb{Z}$ perché le sue soluzioni sarebbero $\not\in\mathbb{Z}$.

**Radice di polinomi**
$S\in\{\mathbb{Q},\mathbb{R},\mathbb{C}\}$
Un numero $x\in S$ è detto u
È una soluzione di $f$ solo se $f$

Teorema di Ruffini

##### Teorema fondamentale dell’algebra
Sia $f(x)=a_0+a_1x+a_2x^2+…+a_nx^n$, $\deg f(x)>0$ e coefficienti
Esistono $z_1,z_2,…,z_n\in\mathbb{C}$ tali che $$f(x)=a$$
Ogni polinomio di grado $n$ e a coefficiente complessi è prodotto di $n$ polinomio di grado 1.


Siano $a,b\in\mathbb{Z}$ dei coefficienti nulli e $d=MCD(a,b)$. Vogliamo trovare $m,n\in\mathbb{Z}$ tali che$$d=m\cdot a+n\cdot b$$
**Teorema Identità di Bezout**
Per ogni $a,b\in\mathbb{Z},(a,b)\neq(0,0),\exists m,n\in\mathbb{Z}$ tali che$$d=m\cdot a+n\cdot b$$dove $d=MCD(a,b)$.
NB. $m$ e $n$ non sono unici.

Per trovare $m$ e $n$ posso
1. Applicare l’ algoritmo di Euclide in $\mathbb{Z}$ e ripercorrerlo in ritroso.
2. a. Il calcolo $|a|,|b|\in\mathbb{N}$
	b. $MCD(a,b)=MCD(|a|,|b|)$
	c. Se $d$ è il $MCD(a,b)$ positivo, la calcola con l’ algoritmo di Euclide in $\mathbb{N}$, e ripercorrendo l’ algoritmo a ritroso trovo $m^*,n^*\in\mathbb{Z}$ tale che$$d=$$

#### Classi di congruenza
Siano $a,b\in\mathbb{Z},n\in\mathbb{N},n>0$. Si dice che $a$ è CONGRUO a $b\mod n$ se $n|(a-b)$.
Si scrive $a\equiv b$.

NB1. $a\equiv b\mod n\Longrightarrow$ \[il resto della divisione di $a$ per $n$\] = \[il resto della divisione di $b$ per $n$\]

NB2. Fissato $n\in\mathbb{N},n\neq0$, la relazione di Congruenza modulo $n$ gode delle seguenti proprietà
1. è RIFLESSIVA: $a\equiv a\mod n\qquad\forall a$
2. è SIMMETRICA: $a\equiv b\mod n\quad\Longrightarrow\quad b\equiv a\mod n$
3. è TRANSITIVA: $\begin{rcases}a\equiv b\mod n\\ b\equiv c\mod n\end{rcases}\Longrightarrow\quad a\equiv c\mod n$
Ogni relazione che soddisfa tutte le tre proprietà, si dice una RELAZIONE DI EQUIVALENZA.

Inoltre le relazioni di CONGRUENZA a $\mod n$ gode anche di
4. sono SOMMABILI: $\begin{rcases}a_1\equiv b_1\mod n\\ a_2\equiv b_2\mod n\end{rcases}\Longrightarrow a_1+a_2\equiv(b_1+b_2)\mod n$
5. sono MOLTIPLICABILI:
	$\begin{rcases}a_1\equiv b_1\mod n\\ a_2\equiv b_2\mod n\end{rcases}\Longrightarrow a_1\cdot a_2\equiv(b_1\cdot b_2)\mod n$


Si chiama CLASSE DI CONGRUENZA di $a\mod n$ e si indica $[a]_n$ oppure $[a]\mod n$.
$\begin{align*}[a]_n&=\text{ l’insieme di tutti i numeri interi che si sono congrui ad }a\mod n.\\ &=\{b\in\mathbb{Z}|b\equiv a\mod n\}\end{align*}$
Dunque
$b\in[a]_n\Longleftrightarrow b=a+nk$ per un opportuno $k\in\mathbb{Z}$$$\boxed{[a]_n=\{b\in\mathbb{Z}|b=a+\mod n\}=\{a+nk|k\in\mathbb{Z}\}}$$es1. $n=2$
$[0]_2=\{0+2x|x\in\mathbb{Z}\}=\{2x|k\in\mathbb{Z}\}$ insieme dei numeri pari
$[1]_2=\{1+2x|x\in\mathbb{Z}\}$ insieme dei numeri dispari
es2. $n=4$
$[0]_4=\{0+4x|x\in\mathbb{Z}\}=\{4x|\}$

OSS1. Sia $n\in\mathbb{N}$ e $n\neq0,\quad\forall a,k\in\mathbb{Z}$$$[a]_n=[a+kn]_n$$DIM: “C” $m\in[a]_n\Longrightarrow\exists x_1\in\mathbb{Z}|m=a+nk_1=m=a+nk+n(k_1-k)$
$\Longrightarrow m\in[a+nk]_n$

OSS2. $n\in\mathbb{N},n>0,a\in\mathbb{Z}$
$c\in[a]_n\Longleftrightarrow[a]_n=[c]_n$
DIM: $^“\Longleftarrow^”[a]_n=[c]_n\Longrightarrow c\in[a]_n$

OSS3. Da OSS1. segue che DIVIDENDO $a\in\mathbb{Z}$ per $n\in\mathbb{N},n>0$
$a=nq+r\quad\text{con }0\leq r<n$
$\Longrightarrow r=a+n(-q)$
$[a]_n=[r]_n$

OSS. $[0]_4=[4]_4=[-4]_4=[8]_4=[-8]_4=…$
$[1]_4=[5]_4=[-3]_4$

Definizione: Ogni elemento di $[a]_n$ si chiama RAPPRESENTANTE della classe di congruenza di $a$ modulo $n$.

**NB3.** Fissato $n$, non ci sono elementi in comune a due classi di congruenza modulo $n$ DIVERSE.
(cioè $a,b\in\mathbb{Z}\qquad[a]_n,[b]_n$
o $[a]_n=[b]_n$ oppure $[a]_n\neq[b]_n\Longrightarrow[a]_n\cap[b]_n=\emptyset$)

**NB4.** $\displaystyle\bigcup_{0\leq a<n}[a]_n=\mathbb{Z}$
$[0]_n\cup[1]_n\cup[2]_n\cup…\cup[n-1]_n$
(“$\subseteq$” ovvia
“$\supseteq$” $z\in\mathbb{Z}$ Divide $z$ per $n\qquad z=n\cdot q+r\quad\text{con }0\leq r<n$z
)

**NB2+NB3.** Le classi di congruenza modulo $n$ ($n$ fissato) sono una PARTIZIONE di $\mathbb{Z}$.

Definizione: L’insieme degli INTERI MODULO $n$, indicato con il simbolo $\mathbb{Z}_n$ è$$\mathbb{Z}_n=\{[0]_n,[1]_n,[2]_n,…,[n-1]_n\}$$In $\mathbb{Z}_n$ definiamo somma e prodotto nel seguente modo:
$\forall[a]_n,[b]_n\in\mathbb{Z}_n$
- $[a]_n+[b]_n=[a+b]_n$
- $[a]_n\cdot[b]_n=[a\cdot b]_n$

**NB5**. Se $\begin{rcases}a_1\in[a]_n\\ b_1\in[b]_n\end{rcases}\Longrightarrow[a_1+b_1]_n=[a+b]_n$
(Per vedere ”$\Longrightarrow$” basta provare che $a_1+b_1\in[a+b]_n$ (e poi usare NB2)
$a_1\in[a]_n\Longrightarrow\exists k_1\in\mathbb{Z}|a_1=a+nk_1$
$b_1\in[a]_n\Longrightarrow\exists k_1\in\mathbb{Z}|b_1=b+nk_1$)

Per cui la definizione di + (ed analogamente anche la definizione di $\cdot$) in $\mathbb{Z}_n$ NON DIPENDE DALLA SCELTA DEI RAPPRESENTANTI DELLE CLASSI (ma solo dalle classi).
(Si dice: + e $\cdot$ sono “ben definite”.)

**TAVOLE DI ADDIZIONE E DI MOLTIPLICAZIONE**
$\mathbb{Z}_2=\{[0]_2,[1]_2\}$

| +       | $[0]_2$ | $[1]_2$ |
| ------- | ------- | ------- |
| $[0]_2$ | $[0]_2$ | $[1]_2$ |
| $[1]_2$ | $[1]_2$ | $[0]_2$ |

$\mathbb{Z}_4=\{[0]_4,[1]_4,[2]_4,[3]_4\}$

| +       | $[0]_4$ | $[1]_4$ | $[2]_4$ | $[3]_4$ |
| ------- | ------- | ------- | ------- | ------- |
| $[0]_4$ | $[0]_4$ | $[1]_4$ | $[2]_4$ | $[3]_4$ |
| $[1]_4$ | $[1]_4$ | $[2]_4$ | $[3]_4$ | $[0]_4$ |
| $[2]_4$ | $[2]_4$ | $[3]_4$ | $[0]_4$ | $[1]_4$ |
| $[3]_4$ | $[3]_4$ | $[0]_4$ | $[1]_4$ | $[2]_4$ |

| $\cdot$ | $[0]_4$ | $[1]_4$ | $[2]_4$ | $[3]_4$ |
| ------- | ------- | ------- | ------- | ------- |
| $[0]_4$ | $[0]_4$ | $[0]_4$ | $[0]_4$ | $[0]_4$ |
| $[1]_4$ | $[0]_4$ | $[1]_4$ | $[2]_4$ | $[3]_4$ |
| $[2]_4$ | $[0]_4$ | $[2]_4$ | $[0]_4$ | $[2]_4$ |
| $[3]_4$ | $[0]_4$ | $[3]_4$ | $[2]_4$ | $[1]_4$ |

CONGRUENZE
Definizione: Sia $x\in\mathbb{N},n>0$. Una CONGRUENZA MODULO $n$ è una espressione del tipo$$(*)\quad ax\equiv b\mod n$$dove $a,b\in\mathbb{Z}$.
$x_a\in\mathbb{Z}$ è UNA SOLUZIONE DI $(*)$$$ax_0\equiv b\mod n$$ossia se $\exists k\in\mathbb{Z}$ tale che $ax_0=b+nk$.

**NB.** Non tutte le congruenze hanno soluzioni.
(mentre tutte le equazioni di 1o grado hanno soluzioni)

es1. $2x\equiv 3\mod 4$ NON HA SOLUZIONI se f $x_0\in\mathbb{Z}$ una soluzione, esisterebbe $k\in\mathbb{Z}$ tale che $\begin{align*}2x_0=3+4k\\ \Longrightarrow 3=2x_0-4k\end{align*}$

<u>PROPOSIZIONE</u>: Sia $(*)\ ax\equiv b\mod n$ con $n\in\mathbb{N},\ n>0,\ a,b\in\mathbb{Z}$
Si supponga che $(*)$ abbia soluzioni e sia $x_0$ una sua soluzione. Allora TUTTI I NUMERI INTERI $[x_0]_n=\{x_0+t_n|t\in\mathbb{Z}\}$ SONO SOLUZIONI DI $(*)$.
(IPOT: $x_0$ è soluzione di $(*)$
TESI: $\forall t\in\mathbb{Z}\qquad x_t=x_0+t\cdot n$ é soluzione di $(*)$
$\begin{align*}\text{DIM: }&x_0\text{ è soluzione di }(*)\Longrightarrow\\ &ax_0\equiv b\mod n\Longrightarrow\\ &\exists k\in\mathbb{Z}|ax_0=b+nk\end{align*}$

Non è detto che siano TUTTE le soluzioni.

**NB.** LA CONGRUENZA $(*)\ ax\equiv b\mod n$ CORRISPONDE A UNA EQUAZIONE IN $\mathbb{Z}_n$$$(**)[a]_nx=[b]_n$$NEL SENSO CHE
se $x_0$ è una soluzione di $(*)$, allora $[x_0]_n$ è una soluzione di $(**)$. Viceversa se $[x_0]_n$ è una soluzione di $(**)$, allora $c\in\mathbb{Z}$ è una soluzione di $(*)\quad\forall c\in[x_0]_n$.

“Risolvere la congruenza” $ax\equiv b\mod n$ significa
1. dire se ha soluzioni
2. nel caso abbia soluzioni, trovarle tutte
Come numeri interi, esse sono infinite. Dire in quante classi di congruenza modulo $n$ questi numeri interi si ripartiscono.

**NB1.** Non tutte le equazioni lineari in $\mathbb{Z}$ hanno soluzione.
es. $[2]_4x=[3]_4$ NO

**NB2.** Non tutte le equazioni lineari in $\mathbb{Z}$ che hanno soluzione, ne hanno una sola. 
es. $[2]_6x=[4]_6 (*)$
$[x_0]_6=[2]_6$ è una soluzione di $(*)$

**Teorema 1** _(Esistenza di soluzioni di una congruenza)_
Siano $n\in\mathbb{N},n>0$ e $a,b\in\mathbb{Z}$. Sia $d=MCD(a,n)$. Allora
$[ax\equiv b\mod n\text{ ha soluzioni}]\Longleftrightarrow d|b$

($\begin{align*}^”\Longrightarrow^”&\text{ IPOT: }d=MCD(a,n)|b\\ &\text{ TESI: }ax\equiv b\mod n\text{ ha soluzioni}\\ &\text{ DIM: }\exists\alpha,\beta\in\mathbb{Z}\text{ tali che }d=d\alpha+\beta n\\ &\qquad d|b\Longrightarrow\exists q\in\mathbb{Z}\text{ tali che }b=qd\\ &\qquad\text{Moltiplico “}d=d\alpha+\beta n\text{” per }q\\ &\qquad\text{ottengo: }qd=q\cdot d\cdot\alpha+q\cdot\beta\cdot n\end{align*}$ )

**Teorema 2**
Si supponga che $ax\equiv b\mod n$ abbia soluzioni. Sia $d=MCD(a.n)$.
Le soluzioni della congruenza sono tutti e soli i numeri interi del tipo$$x_k=x_0+k\cdot\frac{n}{d}\quad\text{ al variare di }k\in\mathbb{Z}$$(dove $x_0$ è una particolare soluzione)

CI SONO INFINITI NUMERI INTERI SOLUZIONI DI $ax\equiv b\mod n$ E SI RIPARTISCONO IN ESATTAMENTE $d$ CLASSI DI CONGRUENZA.MODULO $n$.

es. $ax\equiv b\mod n$
1. Trova $d=MCD(a,n)$
2. Se $d|b$ allora congruenza ha soluzione
3. Calcolo $x_0$
	Bezout: cerco $d,\beta\in\mathbb{Z}$

#### Invertibili in $\mathbb{Z}_n$ e il loro calcolo
Dato $n\in\mathbb{N},a\in\mathbb{Z}$ si dice INVERTIBILE MODULO $n$ se la congruenza $ax\equiv 1\mod n$ ha soluzioni.
(quindi $\begin{align*}\Longleftrightarrow &d=MCD(a,n)|1\Longleftrightarrow\\ &d=MCD(a,n)=1\end{align*}$
Se $MCD(a,n)=1$ si dice che $a$ ed $n$ sono COPRIMI)

Analogamente
Dato $n\in\mathbb{N},n>0$.
$[a]_n\in\mathbb{Z}_n$ si dice INVERTIBILE IN $\mathbb{Z}_n$ se $\exists[b]_n\in\mathbb{Z}_n$ tale che $[a]_n\cdot[b]_n=[1]_n$ (cioè se $[a]_n\cdot[b]_n=[1]_n$)

In questo caso $[b]_n$ si dice un inverso di $[a]_n$, 
ESSENDO $d=1,[b]_n$ è <u>UNICO</u>,
quindi $[b]_n$ è l’INVERSO di $[a]_n$ e si indica $[b]_n=[a]_n^{-1}$.

(es. 4 modulo 9 invertibile? $d=MCD(4,9)=1$ quindi sì.
$4x\equiv 1\mod9,\ [x_0]_9=[4]_9^{-1}$  
Bezout: cerco $d,\beta\in\mathbb{Z}\quad d=\alpha a+\beta n$)

$\mathbb{Z}_p$ (con $p$ numero primo)
Fissiamo $p$ numero primo POSITIVO ed $[a]_p\in\mathbb{Z}_p$. Posso supporre $0\leq a<p$. 
SE $a=0$ ALLORA $[a]_p=[0]_p$
SE $a\neq0$ ALLORA $MCD(a,p)=1$
$\Longrightarrow a$ è invertibile modulo $p$, $\exists[a]_p^{-1}$ 

SE $p$ È UN NUMERO PRIMO IN $\mathbb{Z}_p$ TUTTI GLI ELEMENTI $\neq[0]_p$ SONO INVERTIBILI.

FUNZIONE DI EULERO “conta” gli invertibili di $\mathbb{Z}_n$ 
(conta $\forall n\in\mathbb{N}$ quanti sono i numeri $k$ con $\begin{cases}$

### Sistemi di Congruenze
Un sistema di congruenze è $$\begin{cases}a_1x\equiv c_1\mod m_1\\ a_2x\equiv c_2\mod m_2\\ …\\ a_kx\equiv c_k\mod m_k\end{cases}$$$\begin{align*}\text{dove }&a_i,c_i\in\mathbb{Z}\quad i=1,…,k\\ &m_i\in\mathbb{N},m_i>0\quad i=1,…,\end{align*}$

“Risolvere” il sistema significa
- dire se il sistema ha soluzioni
- nel caso ne abbia, trovarle tutte

Un $x_0\in\mathbb{Z}$ è UNA SOLUZIONE del sistema se è contemporaneamente SOLUZIONE di <u>OGNI</u> CONGRUENZA del sistema.

**NB1.** Sa una congruenza del sistema non ha soluzioni, il sistema non ha soluzioni.

**NB2.** Anche se tutte le congruenze hanno soluzione, non è detto che il sistema abbia soluzione.

Il seguente teorema da una condizione SUFFICIENTE affiché particolari sistemi di congruenze abbiano soluzioni.

#### Teorema Cinese dei Resti
Sia $\begin{cases}x\equiv b_1\mod n_1\\ x\equiv b_2\mod n_2\\ …\\ x\equiv b_k\mod n_k\end{cases}$
$b_1,…,b_k\in\mathbb{Z},n_1,…,n_k\in\mathbb{N},n_i>0\ \forall i=1,…,k$
Gli $n_i$ <u>SIANO A DUE A DUE COPRIMI</u>, ovvero tali che $MCD(n_i,n_j)=1\quad\forall i,j\in\mathbb{N}$,
allora il sistema ha INFINITE SOLUZIONI INTERI. Esse

**NB3.** La condizione che gli $n_i$ siano a due a due coprimi non è una condizione necessaria ma sufficiente affinché un sistema di congruenze abbia soluzioni.

Cominciamo a studiare il suo caso $k=2$ (due congruenze)
METODO NEWTON
$$\begin{cases}(A)\ x\equiv b_1\mod n_1\\ (B)\ x\equiv b_2\mod n_2\end{cases}\quad\text{ con ipotesi }MCD(n_1,n_2)=1$$
1. Chiamo $x_1=b_1$ (è una particolare soluzione di (A))
2. Cerco $t_2\in\mathbb{Z}$ tale che $x_1+t_2n_2=x_2$ sia una soluzione di (B)
	cioè $\underbrace{x_1}_{b_1}+t_2n_2\equiv b_2\mod n_2$
3. $x_2$ è UNA SOLUZIONE del sistema
4. Per il teorema cinese dei resti, l’insieme di tutte le soluzioni del sistema è$$[x_2]_n=\{x_2+t_n|t\in\mathbb{Z}\}\quad\text{dove }n=n_1\cdot n_2$$
Studiamo il caso $k=3$ (tre congruenze)
METODO DI NEWTON
$\begin{cases}(A)\ x\equiv b_1\mod n_1\\ (B)\ x\equiv b_2\mod n_2\\ (C)\ x\equiv b_3\mod n_3\end{cases}$
con l’ipotesi $MCD(n_i,n_j)=1\quad\forall i\neq j$

Per trovare $x_3$
1. Chiamo $x_1=b_1$ una soluzione di (A)
2. Cerco $t_2\in\mathbb{Z}$ tale che 
	$x_1+t_2n_2=x_2$ sia soluzione di (B)
3. Allora $x_2$ è soluzione di (A) e (B)
4. Cerco $t_3\in\mathbb{Z}$ tale che
	$x_2+t_3(n_1\cdot n_2)=x_3$ sia soluzione di (C)
5. Allora $x_3$ è soluzione del sistema ((A),(B) e (C))
6. Per il teorema cinese dei resti, l’insieme di tutte le soluzioni del sistema è $$[x_3]_n=\{x_3+t_n|t\in\mathbb{Z}\}$$dove $n=n_1,n_2,…n_k$ 

Un generico sistema di congruenze
AD UN SISTEMA DELLA FORMA 
- “RIDURRE” significa “SOSTITUIRE CON UN SISTEMA EQUIVALENTE”
- “EQUIVALENTE” significa “CON LE STESSE SOLUZIONI” (eventualmente nessuna soluzione)

Motivazione
$\begin{cases}(A)\ 2x\equiv4\mod8\\ (B)\ 3x\equiv6\mod9\end{cases}$
(A)
(B)
L’insieme delle soluzioni di $\begin{cases}(A)\\ (B)\end{cases}$ è l’insieme delle soluzioni di
$\begin{cases}()\\ ()\end{cases}\begin{cases}()\\ ()\end{cases}$

$$(*)\begin{cases}a_1x\equiv c_1\mod m_1\\ a_2x\equiv c_2\mod m_2\\ …\\ a_kx\equiv c_k\mod m_k\end{cases}$$<u>Passaggio 1</u> Calcola $d_i=MCD(a_i,n_i)\quad\forall i=1,…,k$
- se $\exists d_i\not\ | c_i\Longrightarrow$
- se $\forall d_i|c_i\Longrightarrow$

**NB1.** $\displaystyle\frac{a_i}{d_i},\frac{c_i}{d_i},\frac{m_i}{d_i}\in\mathbb{Z}$.

**NB2.** $\displaystyle\frac{a_i}{d_i}x\equiv\frac{c_i}{d_i}\mod\frac{m_i}{d_i}$ è EQUIVALENTE a $a|x\equiv c_i\mod m_i$

$\boxed{}\Longleftrightarrow\boxed{}\xtofrom[\text{}]{\text{}}\boxed{}$

**NB3.** $\displaystyle MCD\Big(\frac{a_i}{d_i},\frac{m_i}{d_i}\Big)=1\Longrightarrow$ ha soluzioni (perché $d_i=MCD(a_i,n_i)$)

Alla fine del <u>Passaggio 1</u>:$$\begin{cases}\frac{a_1}{d_1}x\equiv\frac{c_1}{d_1}\mod m_1\\ \frac{a_2}{d_2}x\equiv\frac{c_2}{d_2}\mod\frac{m_2}{d_2}\\ …\\ \frac{a_k}{d_k}x\equiv\frac{c_k}{d_k}\mod\frac{m_k}{d_k}\end{cases}$$<u>Passaggio 2</u> Risolvo ciascuna congruenza.

Se NON è vero che gli $n_i$ sono a due a due COPRIMI, dipende…
Se gli $n_i$ sono a due a due coprimi, applico il teorema cinese dei resti.

#### Metodo di Lagrange
Per trovare una particolare soluzione di un sistema del tipo:
$\begin{cases}x\equiv b_1\mod n_1\\ x\equiv b_2\mod n_2\end{cases}$

Bezout: $\exists d_1,d_2\in\mathbb{Z}|1=d_1n_1+d_2n_2$
Allora $z=b_2d_1n_1+b_2d_2n_2$ è una soluzione del sistema
Infatti $z\equiv_{n_2}b_1\alpha_2n_2\equiv b_1\Longrightarrow z\equiv b_1\mod n_1$
