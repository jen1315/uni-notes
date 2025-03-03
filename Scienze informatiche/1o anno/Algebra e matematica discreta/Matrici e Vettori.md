(Algebra)
- [[#Matrice e sistema lineare|Matrice e sistema lineare]]
	- [[#Matrice e sistema lineare#Sistemi lineari|Sistemi lineari]]
		- [[#Sistemi lineari#Algoritmo di Gauss|Algoritmo di Gauss]]
		- [[#Sistemi lineari#Risolubilità di un sistema lineare|Risolubilità di un sistema lineare]]
- [[#Matrici invertibili|Matrici invertibili]]
	- [[#Matrici invertibili#Calcolo della matrice invertibile|Calcolo della matrice invertibile]]
- [[#Sottospazi di spazi vettoriali|Sottospazi di spazi vettoriali]]
	- [[#Sottospazi di spazi vettoriali#Base|Base]]
	- [[#Sottospazi di spazi vettoriali#4 sottospazi fondamentali di una matrice|4 sottospazi fondamentali di una matrice]]
	- [[#Sottospazi di spazi vettoriali#Applicazioni lineari|Applicazioni lineari]]
	- [[#Sottospazi di spazi vettoriali#Matrice associata ad un’applicazione lineare rispetto a fissate basi ordinate su dominio e codominio|Matrice associata ad un’applicazione lineare rispetto a fissate basi ordinate su dominio e codominio]]
	- [[#Sottospazi di spazi vettoriali#Interpretazione geometrica di $R^2$|Interpretazione geometrica di $R^2$]]
	- [[#Sottospazi di spazi vettoriali#Esempi di norme|Esempi di norme]]
		- [[#Esempi di norme#Il _PRODOTTO INTERNO STANDARD_ di $K^n$|Il _PRODOTTO INTERNO STANDARD_ di $K^n$]]
		- [[#Esempi di norme#Algoritmo di Gran Schmidt (G.S.)|Algoritmo di Gran Schmidt (G.S.)]]
		- [[#Esempi di norme#Il complemento ortogonale di un sottospazio di $K^m$|Il complemento ortogonale di un sottospazio di $K^m$]]
		- [[#Esempi di norme#Il complemento ortogonale dei 4 sottospazi fondamentali di una matrice|Il complemento ortogonale dei 4 sottospazi fondamentali di una matrice]]
	- [[#Sottospazi di spazi vettoriali#Calcolo di Determinanti|Calcolo di Determinanti]]
		- [[#Calcolo di Determinanti#Il determinante di matrici triangolari|Il determinante di matrici triangolari]]
	- [[#Sottospazi di spazi vettoriali#Autovalori, Autovettori, Autospazi di una matrice|Autovalori, Autovettori, Autospazi di una matrice]]
		- [[#Autovalori, Autovettori, Autospazi di una matrice#Calcolo dei Autovalori|Calcolo dei Autovalori]]
		- [[#Autovalori, Autovettori, Autospazi di una matrice#Matrici simili ad Autovalori|Matrici simili ad Autovalori]]
	- [[#Sottospazi di spazi vettoriali#Matrici diagonalizzabili|Matrici diagonalizzabili]]
		- [[#Matrici diagonalizzabili#Matrice unitariamente diagonalizzabili|Matrice unitariamente diagonalizzabili]]

### Matrice e sistema lineare
Siano $m,n\in\mathbb{N}$, una matrice $m\times n$ è una tabella di $m,n$ oggetti(numeri o elementi di uno stesso insieme) disposti ordinatamente in $m$ righe e $n$ colonne. 
Tali oggetti sono detti COEFFICIENTI della matrice.

<u>Notazione</u> Una matrice $m\times n$ sarà indicata con uno dei seguenti modi
$$\begin{pmatrix}a_{11} &a_{12} &… &a_{1n}\\ a_{21} &a_{22} &… &a_{2n}\\ &&…\\ a_{n1} &a_{n2} &… &a_{nn}\end{pmatrix}\qquad (a_{ij})_{\begin{align}1\leq i\leq m\\ 1\leq j\leq n\end{align}}\quad\text{ o }\quad(a_{ij})$$

Osservazione: ogni numero reale può essere visto come una matrice $1\times1$ con coefficiente 

SOMMA
Siano $A=(a_{ij})$ e $B=(b_{ij})$ due matrici $m\times n$ in una matrice $A+B$ definita$$A+B=(a_{ij}+b_{ij})$$
**Proprietà**
Siano $A,B,C$ tre matrici $m\times n$ e siano $\alpha,\beta\in\mathbb{N}$
1. $A+(B+C)=(A+B)+C$  associativa
2. $A+B=B+A$ commutativa
3. $A+0=A\quad(=0+A)$ esistenza identità additiva
4. $A+(-A)=0\quad -A=(-1)A$
5. $\alpha(A+B)=\alpha A+\alpha B$
6. $(\alpha+\beta)A=\alpha A+\beta B$

Una matrice $1\times n$ è detta **vettore riga**.
Una matrice $n\times 1$ è detta **vettore colonna**.
<u>Notazione</u> Se $u=\begin{pmatrix}u_1\\ u_2\\ …\\ u_n\end{pmatrix}$ è scritto $u^T=(u_1\quad u_2\quad …\quad u_n)$. $u^T$ è detto **vettore trasposto** di $u$.


PRODOTTO SCALARE
Siano $n\in\mathbb{N},\ u^T=(u_1\quad u_2\quad …\quad u_n)$ e $w=\begin{pmatrix}w_1\\ w_2\\ …\\ w_n\end{pmatrix}$, 
si definisce prodotto (riga per colonna) il seguente numero complesso$$\begin{align*}u^T\cdot w&=u_1w_1+u_2w_2+…+u_nw_n\\ &=(u_1\quad u_2\quad …\quad u_n)\begin{pmatrix}w_1\\ w_2\\ …\\ w_n\end{pmatrix}\end{align*}$$Proprietà $w^T\cdot u=u^T\cdot w$
Per il prodotto appena definito, NON vale la legge della cancellazione.
$(i\quad0)\Big({0\atop i}\Big)=0\qquad(i)$

Siano $A$ una matrice $m\times n$ e $B$ una matrice $n\times m$. Il prodotto (riga per colonna) di A e B è la matrice $m\times n$, e il suo coefficiente $c_{ij}$ di$$\begin{align*}c_{ij}&=\text{(i-esima di A)(j-esima di B)}\\ &=\sum_{K=1}^ra_{iK}b_{Kj}\end{align*}$$
Proprietà (del prodotto matriciale)
Siano $A,B,C$ matrici per cui e $m\times n$ sono definiti e $\alpha\in\mathbb{C}$
1. $A(BC)=(AB)C\quad$(prop. associativa)
2. $0A=A0=0$
3. 	$A\begin{pmatrix}1&&&0\\ &1&&\\ &&…&\\ 0&&&1\end{pmatrix}=\begin{pmatrix}1&&&0\\ &1&&\\ &&…&\\ 0&&&1\end{pmatrix}A=A$
4. $A(B+C)=AB+AC$
5. $(A+B)C=AC+BC$
6. $\alpha(AB)=(\alpha A)B=A(\alpha B)$

**Attenzione:** Il prodotto matriciale NON gode della proprietà commutativa né della legge di cancellazione.

Osservazione: $v^Tu\quad(1\times n)\cdot(n\times1)=1$
$uv^T=\begin{pmatrix}\end{pmatrix}$

Sia $A=(a_{ij})$ una matrice $m\times n$
$A=\begin{pmatrix}0&1\\1+i&3\\2i&2-2i\end{pmatrix}$
- la trasposta di $A$ è la matrice $n\times m,\ B=(b_{ji})$ definita ponendo $b_{ji}=a_{ij}\quad\begin{align*}\forall1\leq i\leq m\\ \forall1\leq j\leq n\end{align*}$
	Si indica $A^T$.
	$A^T=\begin{pmatrix}0&1+i&2i\\1&3&2-2i\end{pmatrix}$
- la coniugata di $A$ è la matrice $m\times n,\ C=(c_{ij})$ definita ponendo $c_{ij}=\overline{a_{ij}}$
	Si indica $C=\overline{A}$.
	$\overline{A}=\begin{pmatrix}0&1\\1-i&3\\-2i&2+2i\end{pmatrix}$
- la h-trasposta di $A$ è la matrice $n\times m,\ B=(b_{ji})$ tale che $B=\overline{A}^T=\overline{(A^T)}$, ovvero ponendo $b_{ji}=\overline{a_{ij}}$.
	Si indica $A^H$.
	$A^H=\begin{pmatrix}0&1-i&-2i\\1&3&2+2i\end{pmatrix}$

In ciò che segue, date $A,B$ si supponga che $A\neq B$ o $AB$ esistano.

Proprietà (della trasposizione)
Siano $A,B$ delle matrici e $\alpha\in\mathbb{C}$
- $(\alpha A)^T=\alpha A^T$
- $(A+B)^T=A^T+B^T$
- $(A^T)^T=A$
- $(AB)^T=B^TA^T$

Proprietà (della coniugata)
Siano $A,B$ delle matrici e $\alpha\in\mathbb{C}$
- $\overline{(\alpha A)}=\overline{\alpha}\overline{A}$
- $\overline{(A+B)}=\overline{A}+\overline{B}$
- $\overline{\overline{A}}=A$
- $\overline{(AB)}=\overline{A}\overline{B}$

Proprietà (della h-trasposta)
- $(\alpha A)^H=\alpha A^H$
- $(A+B)^H=A^H+B^H$
- $(A^H)^H=A$
- $(AB)^H=B^HA^H$

L’insieme di tutte le matrici $m\times n$ (a coefficienti in $\mathbb{C}$) si indica con $M_{m,n}(\mathbb{C})\text{ o }M_{m\times n}(\mathbb{C})$.
Con $m=n$, si scriverà semplicemente $M_m(\mathbb{C})$.

Solo in $M_m(\mathbb{C})$ sono definite entrambe le operazioni $+$ e $\cdot$ introdotte ieri.

Sia $A=(a_{ij})_{1\leq i,j\leq n}$ e $M_m(\mathbb{C})$ la diagonale principale di $A$ di cui <u>n-upla ordinata</u> 

$A=(a_{ij})\subseteq M_m(\mathbb{C})$ si dice DIAGONALE se $a_{ij}=0$ se $i\neq j$.
$A=(a_{ij})\subseteq M_m(\mathbb{C})$ si dice SCALARE se $a$ 

**Osservazione:** Le matrici scalari si comportano come gli scalari.
$\begin{align*}(d\mathbb{1}_n)A=d(\mathbb{1}_nA)&=dA\quad\forall A\in M_m(\mathbb{C})\\ &=Ad=(Ad)\mathbb{1}_n=A(d\mathbb{1}_n)\end{align*}$
le matrici scalari sono le matrici che 

<u>Notazione</u> 
$M_{n\times1}(\mathbb{C})=\mathbb{C}^n$
$M_{1\times n}(\mathbb{C})=\mathbb{C}_n$

Una matrice $A$ è detta
- **simmetrica** se $A=A^T$
- **anti-simmetrica** se $A=-A^T\quad(\text{cioè se }-A=A^T)$
- **hermitiana** se $A=A^H$
- **anti-hermitiana** se $A=-A^H\quad(\text{cioè se }-A=A^H)$
(da notare che $A$ deve essere quadrata)

es.
$\displaystyle{\begin{pmatrix}1&j\\ j&1\end{pmatrix}\atop\text{simmetrica}}\quad{\begin{pmatrix}0&-i\\ i&0\end{pmatrix}\atop\text{anti-simmetrica}}{\begin{pmatrix}1&1-i\\ 1+i&1\end{pmatrix}\atop\text{hermitiana}}{\begin{pmatrix}1i&1-i\\—1-i&-i\end{pmatrix}\atop\text{anti-hermitiana}}$

#### Sistemi lineari
Un sistema lineare (a coefficienti complessi) è un insieme infinito di equazioni di primo grado nelle stesse incognite.

In generale un sistema lineare di $m$ equazioni a $n$ incognite è$$\begin{cases}a_{11}x_1+a_{12}x_2+…+a_{1n}=b_1\\ a_{21}x_1+a_{22}x_2+…+a_{2n}=b_2\\ …\\ a_{n1}x_1+a_{n2}x_2+…+a_{nn}=b_n\end{cases}\quad(*)$$Dato il sistema lineare $(*)$,
- la matrice $A=(a_{ij})\in M_{m,n}(\mathbb{C})$ è detta **matrice (incompleta) dei coefficienti**
- Il vettore colonna $b=(b_1\ b_2\ …\ b_m)^T\in\mathbb{C}^m$ è detto **vettore dei termini noti**
- il vettore colonna $x=(x_1\ x_2\ …\ x_n)^T$ è detto **vettore delle incognite**.

<u>Osservazione</u>: $\boxed{x\not\in\mathbb{C}^n}$ : $x$ è un vettore di incognite. 
Tuttavia $(*)$ riscrive come $\boxed{Ax=b}$
Infatti, da $(*)$ abbiamo che $$\boxed{b_i=\sum_{j=1}^na_{ij}x_j}\quad\text{ per ogni }1\leq i\leq m$$e in effetti l’i-esimo coefficiente del vettore colonna $Ax$ è$$(Ax)_i=\sum_{j=1}^na_{ij}x_j=b_i$$
##### Algoritmo di Gauss
(lezione 14/03)
Risolvere il sistema lineare $Ax=b$ significa determinare l’insieme$$\{c=(c_1\ …\ c_n)^T\in\mathbb{C}^n|Ac=b\}$$(differenza tra $Ax=b$ e $Ac=b$)

La strategia per risolvere $Ax=b$ è quella di “trasformare” $A$ e $b$ in modo da ottenere matrice
Dobbiamo definire le operazioni nel metodo di eliminazione di Gauss.

Non sono ammesse scale con altezza diversa da 1.

Data una matrice a gradini $u$, il primo coefficiente unitario $(\neq0)$ di ogni riga non nulla è detto PIVOT.
Ogni colonna contenente un pivot è detta colonna DOMINANTE.
Una colonna non dominante è detta LIBERA.

Occorre risolvere i seguenti punti:
1. Bisogna provare che ogni matrice $A\in M_{m,n}(\mathbb{C})$ si può trasformare in una matrice a gradini (forma ridotta)
2. Risolto 1., bisogna dimostrare che detta $u$ una forma di $A$, allora i sistemi lineari associati ad $A$ ed $u$ sono equivalenti

Per risolvere Il punto 1., introduciamo le seguenti operazioni

OPERAZIONI ELEMENTARI SULLE RIGHE
di una matrice $A\in M_{m,n}(\mathbb{C})$
- **scambio di righe**, $\boxed{E_{ij}}$ è l’operazione che scambia la riga i-esima di $A$ con la riga j-esima
- **moltiplicazione di riga per scalare non nullo**, $\boxed{E_i(\alpha)}$ con $\alpha\in\mathbb{C}\setminus\{0\}$
- **somma di riga con multiplo di un’altra riga**, $\boxed{E_{ij}(\alpha)}$ somma di riga i-esima con riga j-esima moltiplicato con $\alpha$

In $\mathbb{C}^n$ i vettori direttori sono $(1\leq i\leq n)$ tali che hanno un 1 in una posizione  $$c_i=(0\ …\ 0\ 1\ 0\ …\ 0)^T$$Definizione
Siano $A=(a_{ij})\in M_{m,n}\text{ e }b=(b_1\ …\ b_n)^T\in\mathbb{C}^m$ in matrice$$(A|b)=\left(\begin{array}{ccc|c}a_{11}&…&a_{1n}&b_1\\ \vdots&\ddots&\vdots&\vdots\\ a_{n1}&…&a_{m,n}&b_n\end{array}\right)\in M_{m,n}$$È detta matrice completa o aumentata del sistema $Ax=b$.

Il metodo di eliminazione di Gauss consiste nel portare in forma ridotta la matrice aumentata $(A|b)$. 
Detta $(u|d)$ una tale forma ridotta, allora il sistema lineare $ux=d$ si può risolvere per sostituzione “all’indietro”.

Es. 
$\left(\begin{array}{cccc|c}1&3&-2&1&-1\\0&0&1&2&1\\0&0&0&0&0\end{array}\right)$
Otteniamo 
$\begin{cases}x_1+3x_2-2x_3+x_4=-1\\ x_3+2x_4=1\end{cases}$
Le soluzioni del sistema è
$\left\{\begin{pmatrix}\alpha-8/(-4+i)\\\alpha\\ k/(-k+i)\end{pmatrix}\in\mathbb{C}^3\Big|\alpha\in\mathbb{C}\right\}$

##### Risolubilità di un sistema lineare
Vediamo quando un sistema è risolubile e in caso affermativo, studiamo le sue 
Sia $Ax=b$ un sistema lineare e $(u|d)$ una matrice ridotta di $(A|b)$.
Se $(u|d)$ ha la seguente forma$$\left(\begin{array}{ccc|c}1&&*&d_1\\0&0&1&d_2\\0&0&0&1\end{array}\right)$$cioè se $d$ è colonna dominante, allora $ux=d$ impossibile $Ax=b$ è impossibile: infatti il sistema
Pertanto se $d$ è dominante, allora $Ax=b$ è impossibile.
Supponiamo che $d$ sia libero.

<u>1o caso</u>: $(u|d)$ ha la seguente forma:$$\left(\begin{array}{ccc|c}1&&*&d_1\\0&1&&\vdots\\0&0&1&d_K\\0&0&0&0\end{array}\right)$$quindi con tutte le colonne dominanti (tranne l’ultima).
Il sistema lineare associato diventa$$\begin{cases}x_n=d_n\\ x_{n-1}+*x_n=*\\ x_{n-2}+*x_{n-1}+*x_n=*\\…\\x_1+\sum_{j=2}^nx_j=*\end{cases}$$Conclusione: se $(u|d)$ ha tutte le colonne dominanti (tranne l’ultima) allora $Ax=b$ è risolubile ed ammette una sola soluzione.

<u>2o caso</u>: $(u|d)$ ha almeno una colonna libera
allora $Ax=b$ ammette infinite soluzioni. Più precisamente se $(u|d)$ ha $K<n$ colonne libere, allora $Ax=b$ ha infinite soluzioni dipendenti da $K$ parametri.

19 aprile, 1o compitino
### Matrici invertibili
(Lezione 18/03)
Una matrice $A$ è INVERTIBILE o NON SINGOLARE se esiste una matrice $A$ tale che$$\boxed{AB=BA=I_a}\qquad I_a=\mathbb{1}_n=\begin{pmatrix}1&&&0\\&1&&\\&&\ddots&\\0&&&1\end{pmatrix}$$**NB1:** se $A\in M_n(\mathbb{C})$ è invertibile allora la matrice $B$ della definizione è unica e si indicherà con $B=A^{-1}$.

**NB2:** è possibile dimostrare che
- $(AB=I_a\text{ e }A\in M_n(\mathbb{C}))\Longrightarrow BA=I_a$
- $(BA=I_a\text{ e }A\in M_n(\mathbb{C}))\Longrightarrow AB=I_a$

**NB3:** se $A$ non è quadrata, in generale inversa destra di $A\neq$ inversa sinistra di $A$.

Es. $A=(1\quad0)$. Allora $B=(1\quad1)^T$ è inversa destra $AB=(1\quad0)\begin{pmatrix}1\\1\end{pmatrix}=1$ ma non è inversa sinistra $BA=\begin{pmatrix}1\\1\end{pmatrix}(1\quad0)=\begin{pmatrix}1&0\\1&0\end{pmatrix}\neq I_2=\begin{pmatrix}1&0\\0&1\end{pmatrix}$

Inoltre:esistenza di inversa destra di $A\centernot\Longrightarrow$
       esistenza di inversa sinistra di $A\centernot\Longrightarrow$
	   unicità dell’ inversa sinistra di $A$

**NB4:** se di $A\in M_n(\mathbb{C})$ conosco l’invertibilità (in particolare, conosco $A^{-1}$) allora tutti i sistemi lineari $Ax=b$ ammettono una ed una sola soluzione.$$\begin{align*}Ax&=b\\ A^{-1}Ax&=A^{-1}b\\x&=A^{-1}b\in\mathbb{C}^n\qquad I_nX=X\end{align*}$$**NB5:** le matrici invertibili di $M_1(\mathbb{C})$ sono i numeri complessi invertibili, cioè $\mathbb{C}\setminus\{0\}=\mathbb{C}^x$. Ma non è vero che ogni matrice $2\times2$ non nulla è invertibile.

Es. $\begin{pmatrix}1&0\\1&0\end{pmatrix}$ non è invertibile. Altrimenti deve esistere $B=\begin{pmatrix}a&b\\ c&d\end{pmatrix}$ e $M_2(\mathbb{C})$ tale che
$\begin{pmatrix}1&0\\1&0\end{pmatrix}\begin{pmatrix}a&b\\ c&d\end{pmatrix}=\begin{pmatrix}1&0\\0&1\end{pmatrix}\Longleftrightarrow\begin{cases}a=1\\ b=0\\ a=0\\ b=1\end{cases}$

(Lezione 19/03)
Data $A\in M_n(\mathbb{C})$,
$A$ è invertibile $\Longrightarrow Ax=b$ ha un’unica soluzione $\forall b\in\mathbb{C}^n$
						$\uparrow$
ha una forma ridotta di $A$ ha tutte le colonne dominanti

Le implicazioni precedenti si possono invertire.

TEOREMA
Per ogni $A\in M_n(\mathbb{C})$, le seguenti affermazioni sono equivalenti
(a) $A$ è invertibile
(b) $Ax=b$ ha un’unica soluzione, $\forall b\in\mathbb{C}^n$
(c) una (ciascuna) forma ridotta di $A$ ha tutte le colonne dominanti

Ricordiamo che fissato $n\in\mathbb{N}$, i vettori coordinati di $\mathbb{C}^n$ sono i vettori $c_1,c_2,…,c_n$ dove$$c_i=(0\quad…\quad0\quad1_i\quad0\quad…\quad0)^T$$
Data $A\in M_{m,n}(\mathbb{C})$, una sua ridotta di Gauss-Jordan è una ridotta di $A$ in cui le colonne dominanti sono vettori coordinati di $\mathbb{C}^n$, quindi una matrice della forma$$\begin{pmatrix}…&1&&0&&0&\\&&&1&…&0&\\&&&&&1&…\\&e_1&&e_2&&e_3\end{pmatrix}$$
Analogamente al metodo di eliminazione di Gauss,
<u>PROPOSIZIONE</u>: ogni $A\in M_{m,n}(\mathbb{C})$ ammette una forma ridotta di Gauss-Jordan, ottenibile con le operazioni elementari delle righe di $A$.

Notazione $A\begin{align*}&\xrightarrow{\text{EG\ }}u\\ &\xrightarrow{\text{EGJ}}u’\end{align*}$

 Data $A\in M_{m,n}(\mathbb{C})$, una forma ridotta di Gauss-Jordan $u$
  $n\degree$ di colonne dominanti di $u$
$=n\degree$ di gradini di $u$
$=n\degree$ di righe $\neq0$ di $u$
$=rK(A)$ rango di $A$

<u>COROLLARIO</u>: $A\in M_n(\mathbb{C})$ è invertibile solo se $rK(A)=n$.

#### Calcolo della matrice invertibile
Sia $A\in M_n(\mathbb{C})$, sappiamo quando è invertibile. Ma come calcoliamo $A^{-1}$?
Possiamo sfruttare il metodo di eliminazione di Gauss(-Jordan).
1. Consideriamo la matrice $(A|I_n)\in M_{n,2n}$
2. All’interno di $(A|I_n)$ ottengo una forma ridotta di Gauss-Jordan di $A$, cioè lo porto nella forma $(u’|b)$
3. Portiamo $(u’|b)$ nella forma $(I_n|c)$ (con operazioni elementari nelle righe). A questo punto, $\boxed{c=A^{-1}}$
L’ inversa è unica.

Le matrici invertibili $A\in M_2(\mathbb{C})$ sono caratterizzate dalla condizione è $ad-bc\neq0$, e in tal caso$$A^{-1}=\frac{1}{ad-bc}\begin{pmatrix}d&-b\\-c&a\end{pmatrix}$$
PROPRIETÀ 
Siano $A,B\in M_n(\mathbb{C})$ matrici invertibili. Allora
1. $AB$ e $BA$ sono invertibili e 
	$(AB)^{-1}=B^{-1}A^{-1}$ e $(BA)^{-1}=A^{-1}B^{-1}$
2. $A^T$ è invertibile, e $(A^T)^{-1}=(A^{-1})^T$
3. $A^{-1}$ è invertibile, e $(A^{-1})^{-1}=A$

# Spazi vettoriali complessi e reali

Sia $K\in\{\mathbb{R,C}\}$,
> Uno spazio vettoriale su $K$
> - se $K=\mathbb{C}$ si dice spazio vettoriale (complesso)
> - se $K=\mathbb{R}$ si dice uno spazio vettoriale reale
> è un insieme NON VUOTO $V$ su cui vengono definite 2 operazioni $$\begin{align*}+:V\times V&\longrightarrow V\qquad\text{e}\qquad &\cdot:K\times V&\longrightarrow KV\\(\underline{v},\underline{w})&\longmapsto\underline{v}+\underline{w}&(\alpha,\underline{v})&\longmapsto\alpha\underline{v}\end{align*}$$

che soddisfano le seguenti condizioni
$\forall\underline{u},\underline{v},\underline{w}\in V$ (detti vettori e usano il simbolo di vettore colonna)
$\forall\alpha,\beta\in K$ (detti scalari)
si ha
 1. $\underline{u}+(\underline{v}+\underline{w})=(\underline{u}+\underline{v})+\underline{w}$  ASSOCIATIVA
 2. $\underline{u}+\underline{v}=\underline{v}+\underline{u}$  COMMUTATIVA
 3. $\alpha(\beta\underline{v})=(\alpha\beta)\underline{v}$
 4. $1\cdot\underline{v}=\underline{v}$ 
 5. $(\alpha+\beta)\underline{v}=\alpha\underline{v}+\beta\underline{v}$  DISTRIBUTIVA
 6. $\alpha(\underline{u}+\underline{v})=\alpha\underline{u}+\alpha\underline{v}$  DISTRIBUTIVA
 7. $\forall\underline{v}\in V\ \exists\underline{w}\ |\ \underline{v}+\underline{w}=0$
	$\underline{w}$ si indica con $-\underline{v}$ e si chiama opposto di $\underline{v}$

Esempi di spazi
1. Vettori colonna: $\mathbb{R}_n,\mathbb{C}_n$
   Vettori riga:         $\mathbb{R}_n,\mathbb{C}_n$
   Matrici:                $M_{m\times n}(\mathbb{R}),M_{m\times n}(\mathbb{C})$

2. $a,b\in\mathbb{R}\quad a<b\qquad f:[a,b]\rightarrow\mathbb{R}$
	Sia $F([a,b])$ l’insieme di tutte le funzioni $f:[a,b]\rightarrow\mathbb{R}$
	$\begin{align*}f,g\in F([a,b])\qquad\qquad f+&g:(a,b)\rightarrow\mathbb{R}\\(f+&g)(x)=f(x)+g(x)\quad\forall x\in[a,b]\end{align*}$
    $\begin{align*}f\in F[a,b]\quad\alpha\in\mathbb{R}\qquad\alpha &f:[a,b]\rightarrow\mathbb{R}\\(\alpha&f)(x)=\alpha\cdot f(x)\quad\forall x\in[a,b]\end{align*}$
    $F([a,b])$ è uno _SPAZIO VETTORIALE REALE_.

3. Polinomi $f(x)=a_0+a_1x+a_2x^2+…+a_nx^n$
    $\mathbb{R}[x]=$ insieme dei polinomi a coefficienti reali
    $\mathbb{C}[x]=$ insieme dei polinomi a coefficienti complessi
	**NB1.** $\deg(f(x)+g(x))\leq\max\{\deg f(x)+\deg g(x)\}\quad\forall f(x)g(x)\in K[x]$
	**NB2.** Siano $x\in\{\mathbb{R,C}\}$ e $x\in K$, quindi $c\in K[x]$ e 
     se $c\neq0$ allora $\deg c=0$
     se $c=0$ allora si pone per convenzione $\deg c=-a$
	**NB3.** $\deg(\alpha f(x))\leq\deg f(x),\ \forall\alpha\in K,\ \forall f(x)\in K[x]$

4. $\mathbb{R}_n[x]=$ insieme di polinomi a coefficienti reali di grado $\leq n$
   quindi $\mathbb{R}_n[x]=\{f(x)\in\mathbb{R}[x]|\deg f(x)\leq n\}$
   $\mathbb{C}_n[x]=$ insieme di polinomi a coefficienti complessi di grado $\leq n$
   quindi $\mathbb{C}_n[x]=\{f(x)\in\mathbb{C}[x]|\deg f(x)\leq n\}$

5. $V=\{0\}\qquad\underline{0}+\underline{0}=\underline{0}$
	$K\in\{\mathbb{R,C}\}\quad\alpha\in K\qquad\alpha\cdot\underline{0}=\underline{0}$
	si chiama _SPAZIO NULLO_.

### Sottospazi di spazi vettoriali

Sia $V$ uno spazio vettoriale e $K\in\{\mathbb{R,C}\}$,
> Un sottoinsieme $U$ di $V$ si dice un SOTTOSPAZIO VETTORIALE (o semplicemente sottospazio) se sono soddisfatte le seguenti condizioni
> 1. $\underline{0}\in U$
> 2. $\underline{u}_1+\underline{u}_2\in U\qquad\forall\underline{u}_1,\underline{u}_2\in U$
>    (si dice che $U$ è chiuso rispetto alla somma)
> 3. $\alpha\underline{u}\in U\qquad\forall\underline{u}\in U\quad\forall\alpha\in K$
>    (si dice che $U$ è chiuso rispetto al prodotto scalare)

Un sistema lineare del tipo $A\underline{x}=\underline{0}$ (cioé col vettore dei termini noti uguale a 0) si chiama SISTEMA LINEARE OMOGENEO.
**NB.** $A\underline{x}=\underline{0}$ ha sempre soluzioni!
     $A\underline{v}=\underline{0}\qquad\underline{v}=\underline{0}$
     Il vettore $\underline\ n\times2$ è una soluzione di $A\underline{x}=\underline{0}$
Sia $A\in M_{m\times n}(\mathbb{C})$, l’insieme delle soluzioni del sistema lineare omogeneo $A\underline{x}=\underline{0}$ viene indicato con il simbolo $N(A)$.$$N(A)=\{\underline{v}\in\mathbb{C}^n|A\underline{v}=\underline{0}\}\in\mathbb{C}^n$$VERIFICHIAMO CHE $N(A)$ È UN SOTTOSPAZIO DI $\mathbb{C}^n$
Dobbiamo fare 3 verifiche
1. $\underline{0}\in N(A)$
2. $\forall\underline{u},\underline{v}\in N(A)\Longrightarrow\underline{u}+\underline{v}\in N(A)$
	$\begin{rcases}\underline{u}\in N(A)\Longrightarrow A\underline{u}=\underline{0}\\\underline{v}\in N(A)\Longrightarrow A\underline{v}=\underline{0}\end{rcases}\qquad\underline{0}=A(\underline{u}+\underline{v})=A\underline{u}+A\underline{v}=\underline{0}+\underline{0}=\underline{0}$
3. $\forall\underline{u}\in N(A)\quad\forall\alpha\in\mathbb{C}\Longrightarrow\alpha\underline{v}\in N(A)$
	$\underline{0}=A(\alpha\underline{u})=\alpha (A\underline{u})=\alpha\cdot\underline{0}=\underline{0}$

**NB1.** Se $W$ è un sottospazio di $V$, allora $U$ è uno spazio vettoriale (con il )
**NB2.** $\displaystyle\Big({U\text{ soddisfa}\atop[1]+[2]+[3]}\Big)\Longleftrightarrow\Big({U\text{ soddisfa: }[1]_{BIS}: U\neq\emptyset\atop+[2]+[3]}\Big)$ 

PROPOSIZIONE
Siano $V$ uno spazio vettoriale su $K\in\{\mathbb{R,C}\}$
Si prende:
1. $U\leq W\leq V\Longrightarrow U\leq V$
2. $\{\underline{0}\}\leq V$
NB1. $\alpha\in K,\ \underline{v}\text{ e }\alpha\underline{v}=\underline{0}$
Vale la legge della cancellazione dei prodotti
NB2. $\forall\alpha\in K,\ \forall\underline{}\in V$
NB3. $\forall\alpha\in K,\ \alpha\cdot\underline{0}=\underline{0}$
##### Insieme di multipli di un vettore
Siano $V$ uno spazio vettoriale su $K\in\{\mathbb{R,C}\}$ e $\underline{v}\in V$$$\{\alpha\underline{v}|\alpha\in K\}\ =\text{insieme dei multipli di }V=\ <\underline{V}>$$
1. $<\underline{v}>$ è un sottospazio di $V$
2. se $\underline{v}=\underline{0}$ allora $<v>=\{\alpha\underline{v}|\alpha\in K\}=\{\alpha\cdot\underline{0}|\alpha\in K\}=\{\underline{0}\}=\{\underline{v}\}$
   $<v>$ ha un unico elemento

Di conseguenza
segue che anche $U$ ha infiniti elementi.

Sia $V$ uno spazio vettoriale su $K\in\{\mathbb{R,C}\}$
> Una _COMBINAZIONE LINEARE_ degli $n$ vettori $v_1,v_2,…,v_n$(lista di vettori, possibili ripetizioni) con _COEFFICIENTI_ (o PESI) $\alpha_1,\alpha_2,…,\alpha_n\in K$ è il vettore $\alpha_1\underline{v}_1+\alpha_2\underline{v}_2+…+\alpha_n\underline{v}_n$

Dati $A=\{v_1,v_2,…,v_n\}\in V$,
l’insieme di tutte le loro combinazioni lineari è $$\{\alpha_1\underline{v}_1+\alpha_2\underline{v}_2+…+\alpha_n\underline{v}_n|\alpha_1,\alpha_2,…,\alpha_n\in K\}$$ e si indica con $<\underline{v}_1,\underline{v}_2,…,\underline{v}_n>$ 
e si chiama il _SOTTOSPAZIO GENERATO_ da $\underline{v}_1,\underline{v}_2,…,\underline{v}_n$ o dalla lista $A$.

(29/04)
> Sia $S$ una lista finita di vettori $V$,$$S=\{\underline{v}_1,\underline{v}_2,…,\underline{v}_n\}$$si chiama _SISTEMA DI GENERATORI DI $V$_ se $<S>=V$

**NB.** $S$ è un sistema di generatori di $V\Longleftrightarrow V\subseteq <S>$
$\Longleftrightarrow\forall\underline{v}\in V\quad\underline{v}\in<S>=\{\sum_{i=1}^n d_i|\}$
$\Longleftrightarrow\forall\underline{v}\in V\quad\exists d_1,d_2,…,d_n\in K|\underline{v}=\alpha_1\underline{v}_1+\alpha_2\underline{v}_2+…+\alpha_n\underline{v}_n$

NB. $<\emptyset>=\{S\}$

Sia $V$ uno spazio vettoriale su $K\in\{\mathbb{R,C}\}$,
Il problema di stabilire se $S$ è un insieme di generatori di $V$ si traduce nel problema di se una famiglia di sistemi lineari $A\underline{x}=\underline{b}$ dove $A$ è fissata e $\underline{b}$ è un vettore di termini noti _VARIABILE_ abbia o meno soluzioni$$\underset{m\times n}{A}\underline{x}_{n\times1}=\underline{b}_{m\times1}\text{ cui soluzioni }\forall\underline{b}\in\mathbb{C}^m$$
##### Insiemi Linearmente Indipendenti e Dipendenti
Sia $V$ 
> $A$ si dice **L.I. (linearmente indipendente)** se l’unica combinazione lineare <u>nulla</u> dei suoi elementi è quella con tutti i coefficienti uguali a 0.

> $A$ si dice **L.D. (linearmente dipendente)** se non è L.I. 

**NB1.** Per convenzione $\emptyset$ è L.I.
**NB2.** Sia $\underline{v}\in V$ allora $\{\underline{v}\}$ è L.D. $\Longleftrightarrow\underline{v}=\underline{0}$
**NB3.** Sia $\underline{v}\in V$ allora $\{\underline{v}\}$ è L.I. $\Longleftrightarrow\underline{v}\neq\underline{0}$

Quando i vettori colonna di $A$ risultano tutti dominanti, allora è L.I.

#### Base
Sia $V$ uno spazio vettoriale,
> Una _BASE_ di $V$ è un’insieme di generatori che sono L.I.

Si dice _BASE CANONICA_ se è base composta di colonne dominanti.

Però dobbiamo tenere conto di un insieme di generatori più generale (che comprende anche un insieme infinito di elementi)

> Uno spazio vettoriale $V$ si dice FUNZIONE GENERATORE ($f\cdot g$) se ammette un insieme di generatori finito.

NON TUTTI I SPAZI VETTORIALI SONO $f\cdot g$

**TEOREMA (Esistenza ed Equipotenza delle Basi)**
Sia $V$ uno spazio vettoriale si $K\in\{\mathbb{R,C}\}$
- ogni insieme di generatori di $V$ contiene (almeno) una base di $V$
- siano $B_1$ e $B_2$ due basi di $V$, allora
	(Il numero di elementi di $B_1)=|B_1|=|B_2|=($il numero di elementi di $B_2)$
	Tale numero è quindi un invariante di $V_1$ e si chiama la _DIMENSIONE DI $V$_ e si indica $\dim V$.

**NB.** Se $B$ è una base di $V$ allora $B$ è L.I.
Se $B$ è L.I. allora in $B$ NON ci sono RIPETIZIONI.
Equivalentemente:
Sia $A=\{\underline{v}_1,\underline{v}_2,…,\underline{v}_n\}$ 
$$\begin{align*}L.I.\Longrightarrow\text{NON CI SONO RIPETIZIONI}\\\text{equivale a}\\L.D.\Longrightarrow\text{CI SONO RIPETIZIONI}\end{align*}$$
<u>PROPOSIZIONE</u>
Un’insieme di generatori che abbia tanti elementi quanti la dimensione dello spazio è una base dello spazio vettoriale.

##### Somma e Somma diretta di sottospazi
Siano $V$ uno spazio vettoriale e $U_1, U_2$ due sottospazi di $V$
$U_1+U_2=\{\underline{u}_1+\underline{u}_2|\underline{u}\in U_1,\underline{u}_2\in U_2\}$ È UN SOTTOSPAZIO di $V$
anche $U_1\cap U_2$ è SOTTOSPAZIO di $V$
SE $U_1\cap U_2=\{\underline{0}\}$ ALLORA $U_1+U_2=U_1\oplus U_2$ e si chiama _SOMMA DIRETTA_.

<u>PROPRIETÀ DELLA DIMENSIONE</u>
Sia $V$ uno spazio vettoriale su $K\in\{\mathbb{R,C}\}$
1. $U\underset{sottospazio}{\leq} V\Longrightarrow\dim U\leq\dim V$
2. $\begin{rcases}U\leq V\\\dim U=\dim V\end{rcases}\Longrightarrow U=V$
2. $\begin{rcases}U\leq V\\\dim U=0\qquad\end{rcases}\Longrightarrow\{\underline{0}\}$
3. $U_1,U_2\leq V\Longrightarrow$
	$\dim(U_1+U_2)=\dim U_1+\dim U_2-\dim(U_1\cap U_2)$
4. (conseguenza di 3.) 

**NB.** $U_1\oplus U_2\oplus U_3$ occorre $\begin{cases}U_1\cap U_2=0\\ U_2\cap U_3=0\\ U_1\cap U_3=0\end{cases}$

##### Rango
Sia $A_{m\times n}$
1.  $A\xrightarrow[EG]{} U_1$ forma ridotta di Gauss di $A$
	$A\xrightarrow[EG]{} U_2$ forma ridotta di Gauss di $A$                  
$$\Big({\text{il numero di righe}\atop\text{non nulle di }U_1}\Big)=\Big({\text{il numero di righe}\atop\text{non nulle di }U_2}\Big)$$
	chiamiamolo _RANGO DI $A$_ $=rkA$
2. $A_{m\times n},\quad rkA=k$
	$A\xrightarrow[EG]{}U$
	Poiché ogni “scalino” è “alto” 1 allora
	$k=$ numero delle colonne dominanti di $U$
3. $k\leq m\text{ e }k\leq n$ 
2. Si può provare che $rkA=rkA^T=rk^H$
3. Si può provare che se $B$ è una matrice tale che $\exists AB$ allora
	$rk(AB)\leq rkA$ ed anche $rk(AB)\leq rkB$

#### 4 sottospazi fondamentali di una matrice
$A\in M_{m\times n}(\mathbb{C})$
$\displaystyle\underset{m\times n}{A}=\left[\begin{array}{c|c|c|c}&&&\\&&&\\&&…&\\&&&\end{array}\right]={[\underline{a}_1\ \underline{a}_2\ …\ \underline{a}_n]\atop A\text{ è una riga di vettori colonna}}$

**NB.** Per convenzione, i vettori riga vengono indicati come trasposte di vettori colonna.
$\underset{m\times n}{A}=\left[\begin{array}{cccc}&&&\\\hline&&&\\\hline&&\vdots&\\\hline&&&\end{array}\right]=\left[\begin{matrix}\underline{r}_1^T\\\underline{r}_2^T\\\vdots\\\underline{r}_n^T\end{matrix}\right]A\text{ è una riga di vettori riga}$

1. Lo _**SPAZIO DELLE COLONNE**_ di $A$
	$\begin{align*}C(A)&=<\underline{a}_1,\underline{a}_2,…,\underline{a}_n>\leq\mathbb{C}^m\\&=\{\alpha_1\underline{a}_1+\alpha_2\underline{a}_2+…\alpha_n\underline{a}_n|\alpha_1,…,\alpha_n\mathbb{C}\}\end{align*}$
2. Lo _**SPAZIO DELLE RIGHE**_ di $A$
	$R(A)=<\overline{\underline{r}}_1,\overline{\underline{r}}_2,…,\overline{\underline{r}}_n>\qquad\overline{(\underline{r}_i^T)}=\overline{\underline{r}}_1$
3. Lo **_SPAZIO NULLO_** di $A$
	$N(A)=\{\underline{x}|A\underline{x}=\underline{0}\}\leq\mathbb{C}^n$
4. Lo _**SPAZIO NULLO SINISTRO**_ di $A$
	$N(A^H)=\{\underline{x}|A^H\underline{x}=\underline{0}\}\leq\mathbb{C}^m$

$\boxed{\text{Come trovare delle basi di }C(A),\ R(A)}$
$A\leq M_{m\times n}(\mathbb{C})\qquad A\xrightarrow[EG]{}U$
1. $A=[\underline{a}_1\quad\underline{a}_2\quad…\quad\underline{a}_n]\qquad U=[\underline{u}_1\quad\underline{u}_2\quad…\quad\underline{u}_n]$
	$rkA=k\Longrightarrow U$ ha $k$ colonne dominanti
	Siano $\underline{u}_1,\underline{u}_2,…,\underline{u}_n$ le colonne 
	 
	**NB1.** $\dim C(A)=|B|=k=rkA$
	**NB2.** $\begin{rcases}\dim C(A)=k\\\dim C(U)=k\end{rcases}$
		MA $C(A)\neq C(U)$
	
1. $A=\begin{pmatrix}\underline{a}_1\\\underline{a}_2\\…\\\underline{a}_n\end{pmatrix}\qquad U=\begin{pmatrix}\underline{u}_1\\\underline{u}_2\\…\\\underline{u}_k\\\overline{\underline{0}}\end{pmatrix}$
	$R(A)=<\overline{\underline{r}}_1,\overline{\underline{r}}_2,…\overline{\underline{r}}_n>$
	$R(U)=<\overline{\underline{r}}_1,…,\overline{\underline{r}}_k|\not\overline{\underline{0}},…,\not\overline{\underline{0}}>$

	**NB1.** $\dim R(A)=|D|=k=rkA=\dim R(U)$
	**NB2.** $R(A)=R(U)kA$ non è detto che le h-trasposte delle righe di $A$ corrispondenti alle righe non nulle di $U$, siano una base di $R(A)$. 
	OCCORRE PRENDERE LE H-TRASPOSTE DELLE RIGHE NON. NULLE DI $U$ (dipende dal fatto che quando È.G. possano esserci stati scambi di righe di $A$)

**Calcolare la base di uno spazio nullo $N(A)$**
$A\in M_{m\times n}(\mathbb{C}),\ k=rkA$
$$\begin{align*}N(A)=\{\underline{x}|A\underline{x}=\underline{0}\}=N(U)\\A\underline{x}=\underline{0}\qquad[A|\underline{0}]\xrightarrow[EG]{}[U|\underline{0}]\end{align*}$$
Quanti elementi avrà una base di $N(A)$?
**Teorema (Nullità di Rango)** $A_{m\times n},\ rkA=\underline{x}$$$\dim N(A)=\Big({\text{numero delle}\atop\text{colonne di }A}\Big)-rkA=n-k$$Qual è una $\dim$ di $N(A)$?
- se $k=n$, allora tutte le colonne di $U$ sono dominanti
	$N(A)=N(U)=\{\underline{0}\}$
	L’unica base di $N(A)$ è $\emptyset$
- se $k\neq n$ allora $k<n$ e $n-k>0$,
	$U$ ha $n-k$ colonne libere, per cui $A\underline{x}=\underline{0}$ ha $\infty^{n-k}$ soluzioni, e gli elementi di $N(A)$ sono “descritti” da $n-k$ parametri.
	Se $h_1,h_2,…,h_n$ sono questi parametri, una base $\mathcal{C}$ di $N(A)=N(U)$ è $\mathcal{C}=\{\underline{v}_1;\underline{v}_2;…;\underline{v}_{n-k}\}$

##### Basi dello spazio delle colonne: applicazioni
(7/05)
\[1\] Siano $\mathcal{S}=\{\underline{a}_1,\underline{a}_2,...,\underline{a}_n\}$ un insieme di vettori di $K^m\text{ e }W=<\mathcal{S}>\leq K^m$
Per definizione di $W,\ \mathcal{S}$ è un insieme di generatori di $W$.

Per trovare una base di $W$ contenuta in $S$…
1. Costruisco $A=[\underline{a}_1\ \underline{a}_2\ …\ \underline{a}_n]_{m\times n}$ allora $C(A)=<\underline{a}_1,\underline{a}_2,…,\underline{a}_n>=<\mathcal{S}>=W$
2. $A\xrightarrow[EG]{}U=[\underline{u}_1\ \underline{u}_2\ …\ \underline{u}_n]$ forma ridotta di Gauss. Sia $k=rkA$, se $\underline{u}_{i_1},\underline{u}_{i_2},…,\underline{u}_{i_k}$ sono le colonne dominanti di $U$ allora $\mathcal{B}=\{\underline{a}_{i_1};\underline{a}_{i_2};…;\underline{a}_{i_k}\}$ è una base di $C(A)=W$ contenuta in $\mathcal{S}$

\[2\] Sia $\mathcal{B}=\{\underline{a}_1,\underline{a}_2,…,\underline{a}_n\}$ un insieme di vettori di $K^n$
Per sapere se $B$ è una base di $K^n$, invece di verificare che $B$ è insieme di generatori di $K^n$ e che $\mathcal{B}$ è L.I. conviene:
1. Costruisco $A=[\underline{a}_1\ \underline{a}_2\ …\ \underline{a}_n]_{m\times n}$, allora $<\mathcal{B}>=C(A)\leq K^n$
2. $C(A)=K^n\Longleftrightarrow\dim C(A)=\dim K^n$
$B$ è una base di $K^n\Longleftrightarrow B$ è un insieme di generatori $K^n$
$\boxed{B\text{ è una base di }K^n\Longleftrightarrow rkA=n}$

\[c\] Sia $a=\{\underline{a}_1,…,\underline{a}_n\}$ un insieme di vettori di $K^m$, $a$ è LI o LD?
Costruiamo $A=[\underline{a}_1\ \underline{a}_2\ …\ \underline{a}_n]_{m\times n}$ 

$\mathcal{A}$ un insieme di vettori di $K^m$ e $|a_n|=m$

**NB.** Sottoinsiemi di insiemi di vettori LI sono LI

Sia $\mathcal{A}=\{\underline{a}_1,\underline{a}_2,…,\underline{a}_n\}$ un insieme di vettori di $K^m$
Si supponga che $\mathcal{A}$ sia L.I.
Problema: Posso estendere $\mathcal{A}$ con una base $\mathcal{B}$ di $K^m$?
(cioè definire una base $\mathcal{B}$ di $K^m$ che contenga $\mathcal{A}$)
Siano $A_1=[\underline{a}_1\ \underline{a}_2\ …\ \underline{a}_n]_{m\times n}$
$A=[A_1|I_m]\quad A\text{ è }m\times(n+m)$
$I=\left[\begin{matrix}1&0\\0&1\end{matrix}\right]\qquad A\xrightarrow[EG]{}U=[U_1|U_2]$
- Vediamo che $C(A)=K^m$
- Trova una base di $C(A)$ prendendo le colonne di $A$ corrispondenti alle colonne di $U$
- Siccome $\mathcal{A}=\{\underline{a}_1,\underline{a}_2,…,\underline{a}_n\}$ è L.I. 
	$\Longrightarrow RkU_1=n\Longrightarrow$ tutte le colonne $U_1$

##### BASI ORDINATE
Sia $V$ uno spazio vettoriale su $K\in\{\mathbb{R,C}\}$
> Una _BASE ORDINATA_ di $V$ è una base di $V$ in cui sia fissato l’ordine degli elementi.

(l’ordine dei vettori è tenuta conto)

Sia $\mathcal{B}=\{\underline{v}_1,\underline{v}_1,…,\underline{a}_n\}$ una base ordinata di $V$ e sia $\underline{v}\in V$
- $\mathcal{B}$ è un insieme di generatori di $V\Longrightarrow\exists\underline{v}_1,\underline{v}_2,…,\underline{v}_n\in K$ tale che $\underline{v}=\alpha_1\underline{v}_1+\alpha_2\underline{v}_2+…+\alpha_n\underline{v}_n$
- $\mathcal{B}$ è L.I.$\Longrightarrow\alpha_1,\alpha_2,…,\alpha_n$ sono univocamente individuate da $\underline{v}$
Quindi
$ $
> Sia $\mathcal{B}=\{\underline{v}_1,…,\underline{v}_n\}$ una base ordinata di $V$ tale che . Si chiama _BASE DELLE COORDINATE_ del vettore $\underline{v}\in V$
> Si scrive $C_{\mathcal{B}}(v)=\left[\begin{matrix}\alpha_1\\\vdots\\\alpha_n\end{matrix}\right]$

In generale in $\displaystyle{V=\mathbb{R}^n,\mathbb{R}\atop V=\mathbb{C}^n,\mathbb{C}}$
$\mathcal{E}=\{\underline{e}_1,\underline{e}_2,…,\underline{e}_n\}$ base ordinata 

(9/05)
Sia $V$ uno spazio vettoriale con $K\in\{\mathbb{R,C}\}$
Fissata una base ordinata $\mathcal{B}=\{\underline{v}_1,\underline{v}_2,…,\underline{v}_n\}$ di $V$ si dice che$$\forall\underline{v}\in V\ \exists!\left[\begin{matrix}\alpha_1\\\alpha_2\\\vdots\\\alpha_n\end{matrix}\right]\in K^n\quad|\quad\underline{v}=\sum_{i=1}^n\alpha_i\underline{v}_i$$$C_\mathcal{B}(\underline{v})=\left[\begin{matrix}\alpha_1\\\vdots\\\alpha_n\end{matrix}\right]\begin{align*}\text{ è il vettore delle coordinate di }\underline{v}\\\text{rispetto alla base ordinata }\mathcal{B}\end{align*}$
Quindi, fissata una base ordinata $\mathcal{B}=\{\underline{v}_1;…;\underline{v}_n\}$ di $V$ si può definire la funzione:$$\begin{align*}C_\mathcal{B}:V&\longrightarrow K^n\\\underline{v}&\longmapsto C_\mathcal{B}(x)\end{align*}$$Essa si chiama _MAPPA DELLE COORDINATE_ rispetto alla base ordinata $\mathcal{B}$.

**NB.** Se $\mathcal{B}=\{\underline{v}_1,…,\underline{v}_n\}$ è una base ordinata di $V$
$C_\mathcal{B}(\underline{v}_i)=?$

è un isomorfismo

Godono delle seguenti proprietà
1. $C_\mathcal{B}(\underline{v}+\alpha)=C_\mathcal{B}(\underline{v})+C_\mathcal{B}(\alpha)$
2. $C_\mathcal{B}(\alpha\underline{v})=\alpha C_\mathcal{B}(\underline{v})$
3. $C_\mathcal{B}$ è iniettiva: $\quad C_\mathcal{B}(\underline{v})=C_\mathcal{B}(\underline{w})\Rightarrow\underline{v}=\underline{w}$
4. $C_\mathcal{B}$ è suriettiva:
	$\forall\left[\begin{matrix}\alpha_1\\\vdots\\\alpha_n\end{matrix}\right]\in K^n\quad\exists\underline{v}\in V$ tale che $C_\mathcal{B}(\underline{v})=\left[\begin{matrix}\alpha_1\\\vdots\\\alpha_n\end{matrix}\right]$

#### Applicazioni lineari
Un’APPLICAZIONE (o TRASFORMAZIONE) LINEARE è una funzione$$f:V\rightarrow W$$Tale che
0. $V\text{ e }W$ sono spazi vettoriali di stesso $K$ (entrambi reali o entrambi complessi)
1. $f(\underline{v}_1+\underline{v}_2)=f(\underline{v}_1)+f(\underline{v}_2)\quad\underline{v}_1,\underline{v}_1\in V$
2. $f(\alpha\underline{v})=\alpha f(\underline{v})\quad\forall\underline{v}\in V,\ \forall\alpha\in K$
##### Esempi importanti di applicazioni lineari
1. 
3. $A\in M_{m\times n}$
	$\begin{align*}f_A:\mathbb{C}^n&\rightarrow\mathbb{C}^m\\&\rightarrow A\underline{v}\end{align*}$
	Si chiama _APPLICAZIONE LINEARE INDOTTA_ della matrice $A$

**NB.** $V\xrightarrow[]{f}W\xrightarrow[]{g}Z\qquad V\xrightarrow[]{f\cdot g}Z$
$f,g$ sono applicazioni lineari$\Longrightarrow g\cdot f$ è applicazione lineare

$N(f)=\{\underline{v}\in V|f(\underline{v})=\underline{0}\}$ si chiama _SPAZIO NULLO_ o $Ker$ _NUCLEO_ di $f$.
**NB.** Si può verificare (usando il fatto che $f$ è un’applicazione lineare) che $N(f)$ È UN SOTTOSPAZIO DI $V$.

$Im f=\{f(\underline{v})|\underline{v}\in V\}$ si chiama _SPAZIO IMMAGINE_ di $V$.
**NB.** Si può verificare (usando il fatto che $f$ è un’applicazione lineare) che $Im f$ è un _SOTTOSPAZIO_ di $W$

In particolare $A\in M_{m\times n}(\mathbb{C})$ e $f_A:\begin{align*}\mathbb{C}^n&\rightarrow\mathbb{C}^m\\\underline{v}&\mapsto A\underline{v}\end{align*}$ applicazione lineare indotta da $A$
Chi sono $N(f_A)$ e $Im f$?
$\begin{align*}N(f_A)&=\{\underline{v}\in\mathbb{C}^n|f_A(\underline{v})=\underline{0}\}\\&=\{\underline{v}\in\mathbb{C}^n|A\underline{v}=\underline{0}\}\end{align*}\qquad Im f_A=\{f_A(\underline{v})|\underline{v}\in\mathbb{C}^n\}=\{A\underline{v}|\underline{v}\in\mathbb{C}^n\}$
**NB.** $A\in M_{m\times n}\quad A=[\underline{a}_1\ \underline{a}_2\ …\ \underline{a}_n]$
$A\left[\begin{matrix}\underline{a}_1\\\underline{a}_2\\\vdots\\\underline{a}_n\end{matrix}\right]=\alpha_1\underline{a}_1+\alpha_2\underline{a}_2+…+\alpha_n\underline{a}_n$

$\underline{e}_i$ la i-esima colonna di $\mathbb{C}$
$A\underline{e}_i=\underline{a}_i=$ i-esima colonna di $A$

#### Matrice associata ad un’applicazione lineare rispetto a fissate basi ordinate su dominio e codominio

Siano $V,W$ spazi vettoriali su $K\in\{\mathbb{R,C}\}$
$f:V\rightarrow W$ una applicazione lineare
$\mathcal{B}=\{\underline{v}_1,\underline{v}_2,…,\underline{v}_n\}$ una base ordinata di $V$
$\mathcal{D}=\{\underline{w}_1,\underline{w}_2,…,\underline{w}_n\}$ una base ordinata di $W$

$\exists!A_{m\times n}$ tale che sia commutativo il seguente diagramma
$$\begin{array}{ccc}V&\xrightarrow[]{f }&W\\\downarrow C_\mathcal{B}&&\downarrow C_\mathcal{D}\\ K^n&\xrightarrow[f_A]{}&K^m\end{array}$$
cioè tale che $C_\mathcal{D}\circ f=f_{A}\circ C_{\mathcal{B}}$
cioè tale che $\forall\underline{v}\in V:\qquad\begin{array}{ccc}\underline{v}\in V&\xrightarrow[]{f }&f(\underline{v})\\\downarrow C_\mathcal{B}&&\downarrow C_\mathcal{D}\\ C_\mathcal{B}(\underline{v})&\xrightarrow[f_A]{}&A\cdot C_\mathcal{B}(\underline{v})\end{array}$
$\exists!A_{m\times n}$ tale che $C_\mathcal{D}(f(\underline{v}))=A\cdot C_\mathcal{B}(\underline{v})\quad\forall\underline{v}\in V$

**Matrice di passaggio da una matrice ordinata all’altra**
Siano $V$ uno spazio vettoriale su $K\in\{\mathbb{R,C}\}$
$\mathcal{B}=\{\underline{v}_1,\underline{v}_2,…,\underline{v}_n\}$
$\mathcal{B}’=\{\underline{v’}_1,\underline{v’}_2,…,\underline{v’}_n\}$ due basi ordinate di $V$
La funzione identità $\underset{\hspace{1cm}\underline{v}\rightarrow\underline{v’}}{id_V:V\rightarrow V’}$  è un’applicazione lineare
La matrice associata a $id_v$ rispetto alle basi ordinate
$\mathcal{B}’$ sul dominio, $\mathcal{B}$ sul dominio
si chiama _MATRICE DI PASSAGGIO_ da $\mathcal{B}‘$ a $\mathcal{B}$ e si indica $M_{\mathcal{B}\leftarrow\mathcal{B}’}$
$$\begin{array}{ccc}\mathcal{B}’&\underrightarrow{id_i }&\mathcal{B}\\\downarrow C_\mathcal{B’}&&\downarrow C_\mathcal{B}\\ K^n&\overrightarrow{f_{M_{\mathcal{B}\leftarrow\mathcal{B}}}}&K^n\end{array}$$
**NB.** $M_{\mathcal{B}’\leftarrow\mathcal{B}}=M_{\mathcal{B}\leftarrow\mathcal{B}‘}^{-1}$

#### Interpretazione geometrica di $R^2$
$\displaystyle R^2=\{\left[{a\atop b}\right]|a,b\in\mathbb{R}\}$
$\left[{a\atop b}\right]$ è raggiungibile in $0_{xy}$ da una funzione $\overrightarrow{0P}$

Mentre $Q$ è nel 
1. Il vettore $\underline{v}=\left[{a\atop b}\right]\in\mathbb{R}^2$ corrisponde al punto $P(a,b)$
2. A cosa corrisponde $0_{xy}$ i sottospazi di dimensione 1 

**Regola del parallelogramma**
$\displaystyle\underline{v}=\left[{a\atop b}\right],\underline{w}=\left[{c\atop d}\right]\in\mathbb{R}^2\quad\Rightarrow\quad\underline{v}+\underline{w}=\left[{a\atop b}\right]+\left[{c\atop d}\right]=\left[{a+c\atop b+d}\right]$ “somma algebrica”

$\begin{align*}\text{Se P rappresenta }\underline{v}\text{ in }0_{xy}&\Rightarrow&\text{La “SOMMA GEOMETRICA” (la somma delle facce}\\\text{Q rappresenta }\underline{w}\text{ in }0_{xy}&&\vec{OP}\text{ ed }\vec{OQ}\text{) è (regola del parallelogramma) la faccia }\vec{OR}\end{align*}$

Provo che $\begin{cases}x_R=x_P+x_Q=a+c\\ y_R=y_P+y_Q=b+d\end{cases}$  ossia che R rappresenta il vettore $\underbrace{\underline{v}+\underline{w}}_{\text{somma algebrica}}$

**NB1.** $\mathop{\vphantom{\triangle}}_{O}\hspace{-0.10em}{\stackrel{Q}{\triangle}}_{H}=\mathop{\vphantom{\triangle}}_{P}\hspace{-0.10em}{\stackrel{R}{\triangle}}_{L}$ perché hanno lati paralleli e $\underbrace{|OQ|=|PR|}_{\text{stessa ipotenusa}}$
**NB2.** $\mathop{\vphantom{\rectangle}}_{O}\hspace{-0.17em}{\stackrel{Q}{\rectangle}}_{H}$ è un rettangolo 
- $f(x)\leq0$ e $[f()]$ 

> Sia $V$ è uno spazio vettoriale 

#### Esempi di norme
$V=\mathbb{R}^{2},\ K=\mathbb{R}$
$V\ni\underline{v}=\left[{a\atop b}\right]$
1. Norma _**EUCLIDEA**_
	In generale, se $V=\mathbb{R}^n$ con $K=\mathbb{R}$ o se $V=\mathbb{C}^n$ con $K=\mathbb{C}$
	$\begin{array}{c|c}||\cdot||_2:\mathbb{R}^n\rightarrow\mathbb{R}_{\geq0}&||\cdot||_2:\mathbb{C}^n\rightarrow\mathbb{R}_{\geq0}\\||\underline{v}||_2=\sqrt{\underline{v}^T\underline{v}}&||\underline{v}||_2=\sqrt{\underline{v}^H\underline{v}}\\\text{NORMA EUCLIDEA DI }\mathbb{R}^n&\text{NORMA EUCLIDEA DI }\mathbb{C}^n\end{array}$
	Se $\underline{v}\in\mathbb{R}^n$ allora $\underline{v}^H=\underline{v}^T$ per cui $\sqrt{\underline{v}^T\underline{v}}=\sqrt{\underline{v}^H\underline{v}}$ se b
1. Norma _TAXI DRIVER_ o _MANHATTAN_
	$\|\underline{v}\|_1=|a|+|b|$
	In generale, se $V=\mathbb{R}^n\text{ e }K=\mathbb{R}\text{ o se }V=\mathbb{C}^n\text{ e }K=\mathbb{C}$
	$\|\cdot\|_1:V\rightarrow\mathbb{R}_{\geq0}\qquad\left\|\left[\begin{matrix}v_{1}\\ v_{2}\\\vdots\\ v_{n}\end{matrix}\right]\right\|_1=\max\{|\underline{v}_1|,|\underline{v}_2|,…,|\underline{v}_n|\}$
1. Norma _INFINITESIMA_

##### Il _PRODOTTO INTERNO STANDARD_ di $K^n$ 
La funzione al numeratore in (\*) è $\quad\begin{align*}\mathbb{R}^2\times\mathbb{R}^2\rightarrow\mathbb{R}\\(\underline{v},\underline{w})\rightarrow\underline{v}^T\underline{w}\end{align*}$

La generalizziamo (da $\mathbb{R}^2\text{ a }\mathbb{R}^n): \quad\begin{align*}\mathbb{R}^n\times\mathbb{R}^n\rightarrow\mathbb{R}\\(\underline{v},\underline{w})\rightarrow\underline{v}^T\underline{w}\end{align*}$

(passando da $\mathbb{R}^n\text{ a }\mathbb{C}^n)\quad\begin{align*}\mathbb{C}^n\times\mathbb{C}^n\rightarrow\mathbb{C}\\(\underline{v},\underline{w})\rightarrow\underline{v}^H\underline{w}\end{align*}$

La funzione si indica con il simbolo $(\cdot|\cdot)$

$\begin{align*}(\cdot|\cdot):K^{n}\times K^{n}\rightarrow K\\(\underline{v}|\underline{w})=\underline{v}^H\underline{w}\end{align*}\qquad$ si chiama “_PRODOTTO INTERNO (o SCALARE) STANDARD_” di $K^n$

**Il coseno dell’angolo tra due vettori di $\mathbb{R}^2$**
Siano $\underline{v},\underline{w}\in\mathbb{R}^2$ tali che $\underline{v}\neq0\neq\underline{w}$

Vettori ortogonali
Se $\underline{v},\underline{w}\in\mathbb{R}^2$ con $\underline{v}\neq\underline{0}\neq\underline{w}$, allora $\underline{v}$ è ortogonale a $\underline{w}(\underline{v}\perp\underline{w})\Longleftrightarrow[\widehat{\underline{v}\underline{w}}=90\degree\text{ oppure }\widehat{\underline{v}\underline{w}}=270\degree]$


ORTOGONALE
ORTONORMALE

**NB.** Un insieme ORTONORMALE si ottiene da un insieme da un insieme ORTOGONALE privo di vettori nulli e normalizzando tutti i suoi vettori.

Un insieme di generatori ortogonale è $\begin{cases}\text{insieme di generatori}\\\text{insieme ortogonale}\end{cases}$
Una base ortogonale è $\begin{cases}\text{base}\\\text{insieme ortonormale}\end{cases}$
Stesso vale per l’insieme ortonormale. 

$V=K^{m}, K\in\{\mathbb{R,C}\}$
$(\cdot|\cdot)$ è il prodotto standard di $V$ ($()$)

**NB1.** $\underline{0}\perp\underline{v}\quad\forall\underline{v}\in V$
**NB2.** Si può dimostrare che se $\mathcal{S}_v$ è un insieme di generatori ortogonale di $W$ e $V$ allora l’insieme $\mathcal{B}$ che si ottiene da $\mathcal{S}$ togliendo gli eventuali vettori

<u>OBIETTIVO</u> Sia $W\subseteq V=K^m$
Dato $\mathcal{S}=\{\underline{v}_1,\underline{v}_2,…,\underline{v}_n\}$ un insieme di generatori di $W$ costruire $\mathcal{S}_o=\{\underline{u}_1,…,\underline{u}_n\}$ un insieme di generatori ORTOGONALE di $W$.

<u>TECNICA</u> Algoritmo di _GRAN SCHMIDT_ (G.S.)

**NB3.** Se $\mathcal{S}$ è una base di $W$, allora applicando as $\mathcal{S}$ G.S. Si ottiene una base ortogonale di $W$.

**NB4.** Per costruire una base ORTONORMALE di $W$, si normalizzano i vettori di una base ortogonale. 

##### Algoritmo di Gran Schmidt (G.S.)
Ho $\underline{v}_1,\underline{v}_2,…,\underline{v}_n$ costruisco $\underline{u}_1,\underline{u}_2,…,\underline{u}_n$
$\underline{u}_1=\underline{v}_1$
$\underline{u}_2=\underline{v}_2-\alpha_{12}\underline{u}_1\qquad\alpha_{12}=\begin{cases}0&\text{se }\underline{u}_1=0\\\frac{(\underline{u}_1|\underline{v}_2)}{(\underline{u}_1|\underline{u}_1)}&\text{se }\underline{u}_1\neq0\end{cases}$
$\underline{u}_3=\underline{v}_3-\alpha_{13}\underline{u}_1-\alpha_{23}\underline{u}_2\qquad\alpha_{13}\begin{cases}0&\text{se }\underline{u}_1=0\\\frac{(\underline{u}_1|\underline{v}_3)}{(\underline{u}_1|\underline{u}_1)}&\text{se }\underline{u}_1\neq0\end{cases}\qquad\alpha_{23}=\begin{cases}0&\text{se }\underline{u}_2=0\\\frac{(\underline{u}_2|\underline{v}_3)}{(\underline{u}_2|\underline{u}_2)}&\text{se }\underline{u}_2\neq0\end{cases}$
e così avanti…
Ovvero $\displaystyle\boxed{\underline{u}_j=\underline{v}_j-\sum_{i=1}^{j-1}\alpha_{ij}\underline{u}_i\qquad\alpha_{ij}=\begin{cases}0&\text{se }\underline{u}_i=0\\\frac{(\underline{u}_i|\underline{v}_j)}{(\underline{u}_i|\underline{u}_i)}&\text{se }\underline{u}_i\neq0\end{cases}}$

Per renderli ortonormali, $\underline{u}^*=\frac{\underline{u}}{\|\underline{u}\|_{2}}\qquad\|\underline{u}\|_2=\sqrt{(\underline{u}|\underline{u})}$ 

Schema di 

##### Il complemento ortogonale di un sottospazio di $K^m$
Sia $V\in K^{m},\ K\in\{\mathbb{R,C}\}$ e sia $U$ sottospazio di $V=K^m$
Il _COMPLEMENTO ORTOGONALE_ $U^{\perp}\text{ di }U\text{ in }K^m$ è$$\begin{align*}U^{\perp}&=\{\underline{v}\in K^{m}|\underline{v}\perp\underline{u}\quad\forall\underline{u}\in U\}\\&=\{\underline{v}\in K^{m}|(\underline{v}|\underline{u})=0\quad\forall\underline{u}\in U\}\end{align*}$$Da $(\underline{v}|\underline{u})=\underline{v}^H\underline{u}$ segue che 
$U^{\perp}$ è un SOTTOSPAZIO DI $K^m$
\[a\] $U\cap U^{\perp}=\{\underline{0}\}$
	Infatti:$\quad\underline{z}\in U\cap U^{perp}\Longrightarrow\begin{cases}\underline{z}\in U\\\underline{z}\in U^{\perp}=\{\underline{v}\in K^m|\underline{u}^{H}\underline{v}=0\quad\forall\underline{u}\in U\}\end{cases}$
	$\Longrightarrow\underline{z}^H\underline{z}=0$
	ma $\underline{z}^{H}\underline{z}=\|\underline{z}\|_2$
\[b\] Si può provare che $K^m=U+U^{\perp}$
	allora da \[a\] segue che $K^{m}=U\oplus U^{perp}$
	ne segue
	$\forall\underline{v}\in K^{m}\exists!\underline{u}\in U\exists!\underline{w}\in U^{\perp}$
	Infatti l’esistenza di $\underline{u}$ e di $\underline{w}$ segue che $K^m=U+U^{perp}$ per quanto riguarda l’unicità:
	se $\exists\underline{u}_1+\underline{u}_{2}\in U\quad\exists\underline{w}_1,\underline{w}_{2\in}U^{perp}$
	$\underline{v}=\underline{u}_{1}+\underline{u}_{2}=\underline{w}_1+\underline{w}_2$
	$\Longrightarrow\underline{u}_{1}+\underline{u}_{2}$
- - -
$U\in K^{m}\quad U^{\perp}\leq K^{m\qquad}K^{m}=U\oplus U^{\perp}$
$\dim K^{m}=\dim(U\oplus U^{\perp})=\dim U$
$\forall\underline{v}\in V\ \exists!\underline{u}\in U\ \exists!\underline{w}\in U^{\perp}\text{ t.c. }$
$\underline{u}:=P_{U}$ è _proiezione ortogonale_

**CALCOLO DELLA PROIEZIONE ORTOGONALE $P_U(\underline{v})$**
$U\in K^{m}\qquad\underline{v}\in K^m$
- si trova una base ORTONORMALE si $U:\{\underline{v}_1^*,\underline{v}_2^*,…,\underline{v}_k^*\}$
- $Q=[\underline{u}_{1}^{*}\ \underline{u}_{2}^{*}\ …\ \underline{u}_{k}^{*}]$
- 
- $P_\underline{v}=P_{U}(\underline{v})$
	$\underline{v}=P_{U}(\underline{v})+\underline{w}$
##### Il complemento ortogonale dei 4 sottospazi fondamentali di una matrice
$\begin{align*}A_{m\times n}\qquad N(A)\leq\mathbb{C}^n\quad R(A)\leq\mathbb{C}^n\\ N(A^{H})\leq\mathbb{C}^m\quad C(A)\leq\mathbb{C}^m\end{align*}$
Si prova che $N(A)^{\perp}=C(A^{H})$
1. $N(A)^{\perp}=R(A)$ (ecco perché abbiamo definito $R(A)\text{ come }C(A^H)$)
2. $R(A)^{\perp}=N(A)$
	In particolare $\qquad\mathbb{C}^{n}=N(A)\oplus R(A)$
3. Mettendo $A^{H}$ al posto di $A$ ottengo:
	$N(A^H)^{\perp}=C(A)$
4. $C(A)^{\perp}=N(A^H)$
	In particolare $\qquad\mathbb{C}^{m}=C(A^{H})\oplus N(A^{H})$

#### Calcolo di Determinanti
Sia $A$ una matrice <u>QUADRATA</u> di ordine $n$,
Il determinante di $A$ è un numero che dipende da $A$. Lo indichiamo $\det A$.
Caso $n=1\quad$ Se $A=[a_{11}]$ è $\det A=a_{11}$
Caso $n=2$
$\text{Se }\begin{align*}A=\left[\begin{matrix}a_{11}&a_{12}\\ a_{21}&a_{22}\end{matrix}\right],\ \det A=a_{11}a_{22}-a_{12}a_{21}\\&=(a_{11}a_{22})+(-a_{12}a_{21})\end{align*}$

$C_{ij}=$ la matrice che si ottiene da $A$ togliendo la riga $i$ e la colonna $j$
     la _MATRICE COMPLEMENTARE_ di riga i e colonna j
$A_{ij}=(-1)^{i+j}\det C_{ij}\qquad$ _COMPATTORE DI POSTO $[i,j]$_ per A
$\det\left[\begin{matrix}a_{11}&a_{12}\\ a_{21}&a_{22}\end{matrix}\right]=[a_{11}\ a_{12}]\left[{A_{11}\atop A_{12}}\right]$

Caso $3\times3$
$\begin{align*}\det\left[\begin{matrix}a_{11}&a_{12}&a_{13}\\ a_{21}&a_{22}&a_{23}\\ a_{31}&a_{32}&a_{33}\end{matrix}\right]&=a_{11}(-1)^{1+1}\det C_{11}+a_{12}(-1)^{1+2}\det C_{12}+a_{13}(-1)^{1+3}\det C_{13}\\&=a_{11}\det\left[\begin{matrix}a_{22}&a_{23}\\ a_{32}&a_{33}\end{matrix}\right]-a_{12}\det\left[\begin{matrix}a_{21}&a_{23}\\ a_{31}&a_{33}\end{matrix}\right]+a_{13}\det\left[\begin{matrix}a_{21}&a_{22}\\ a_{31}&a_{32}\end{matrix}\right]\end{align*}$

**Formula di Laplace del determinante rispetto alla $1^a$ riga**
Se $A=(a_{ij})\quad n\times n$
$\det A=[a_{11}\ a_{12}\ …\ a_{1n}]\left[\begin{matrix}A_{11}\\ A_{12}\\\vdots\\ A_{1n}\end{matrix}\right]$
Sviluppo del determinante rispetto all’i-esima riga,
Laplace si può applicare a qualsiasi riga e conviene applicarla a quella con più zeri

**Sviluppo del determinante rispetto all’j-esima colonna**
$A=(a_{ij})\quad n\times n$
$\det A=[a_{1j}\ a_{2j}\ …\ a_{nj}]\left[\begin{matrix}A_{1j}\\ A_{2j}\\\vdots\\ A_{nj}\end{matrix}\right]$
##### Il determinante di matrici triangolari
Il determinante di una matrice triangolare è il prodotto degli elementi della diagonale
$\det\left[\begin{matrix}t_{11}&&\mathbb{O}\\ &\ddots& \\ *&&t_{nn}\end{matrix}\right]$

Proprietà
Siano $A,B\quad n\times n$
1. $\det\overline{A}=\overline{\det A}$
2. $\det(A^{T})=\det A$
3. $\det(A^H)=\overline{\det A}$
4. $\det(AB)=(\det A)(\det B)$
5. $A$ è non singolare $\Longleftrightarrow\det A\neq0$
	In tal caso: $\displaystyle\det(A^{-1})=\frac{1}{\det A}$
#### Autovalori, Autovettori, Autospazi di una matrice
Sia $A$ una matrice $n\times n$ e coefficienti in $K\in\{\mathbb{R,C}\}$
$A\underline{v}=?\qquad\forall\underline{v}\in K^n$
Nel caso in cui $A=\lambda I_n=\left[\begin{matrix}\lambda&&\mathbb{O}\\&\ddots&\\\mathbb{O}&&\lambda\end{matrix}\right]\qquad A\underline{v}=(\lambda I_n)\underline{v}=\lambda(I_n\underline{v})=\lambda\underline{v}$

<u>PROBLEMA</u> Se $A$ è QUALUNQUE matrice $n\times n$
$\exists\underline{v}\neq0$ per cui $A\underline{v}=\lambda\underline{v}$ per una opportuna $\lambda$?

> Uno scalare $\lambda\in K$ tale che esiste $\underline{v}\in K^{n}$
> $\underline{v}\neq\underline{0}$ per cui $A\underline{v}=\lambda\underline{v}$ si dice _AUTOVALORE_ di $A$.
> L’indice di tutti gli autovalori di $A$ si dice lo _SPETTRO_ di $A$ e si indica con $Spec(A)$.
 
<u>NOTAZIONI</u> $K\in\{\mathbb{R,C}\}\quad \mu\in K$
$A_{n\times n}$ a coefficienti in $K$$$E_{A}(\mu)=\{\underline{v}\in K^n|A\underline{v}=\mu\underline{v}\}$$$\mu$ qualsiasi numero anche quando $E_{A}(\mu)=\{\underline{0}\}$. Usiamo $\lambda$ per precisare l’uso di autovalori.

$\begin{align*}E_A(\lambda)&=\{\underline{v}\in K^n|A\underline{v}=\lambda\underline{v}\}\\&=\{\underline{v}\in K^n|A\underline{v}-\underbrace{\lambda\underline{v}}_{\lambda I_n\underline{v}}=0\}\\&=\{\underline{v}\in K^n|(A-\lambda I_n)\underline{v}=0\}\\E_{A}(\lambda)&=N(A-\lambda I_n)\end{align*}$
1. $E_{A}(\lambda)$  è uno sottospazio di $K^n$ e si chiama _AUTOSPAZIO DI $A$ RELATIVO ALL’AUTOVALORE $\lambda$_
2. $E_{A}(\lambda)\neq\{\underline{0}\}$
	Ogni elemento di $E_{A}(\lambda)$ <u>NON NULLO</u> si chiama _AUTOVETTORE DI $A$ RELATIVO ALL’AUTOVALORE $\lambda$_
3. $\dim E_{A}(\lambda)=d(A)=$ la _MOLTIPLICITÀ GEOMETRICA DELL’ AUTOVALORE $\lambda$_
$\begin{align*}\dim E_{A}(\lambda)&=\dim N(A-\lambda I_n)=\\&=(\text{})-rk(A-\lambda I_n)\end{align*}$

##### Calcolo dei Autovalori
Sia $A\ n\times n$
$\lambda$ è un autovalore di $A\Longleftrightarrow E_{A}(\lambda)\neq\{\underline{0}\}$
$\Longleftrightarrow N(A-\lambda I_n)\neq\{\underline{0}\}$
$\Longleftrightarrow\dim$
$\Longleftrightarrow rk(A-\lambda I_n)<n$
$\Longleftrightarrow A-\lambda I-n\quad$NON HA INVERSA (è singolare)
$\Longleftrightarrow\det(A-\lambda I_n)=0$$$\lambda\in Spec(A)\Longleftrightarrow\det(A-\lambda I_n)=0$$$A_{n\times n}\qquad\det(A-xI_{n})=0$ è _EQUAZIONE CARATTERISTICA_ di $A$
$P_{A}(x)=$ _POLINOMIO CARATTERISTICO_ di $A$

Quindi $\lambda$ è zero di $P_{A}(x)$
**Proprietà**
$A\ n\times n,\quad n\geq2\qquad P_{A}(x)=\det(A-\lambda I_n)$
1. $\deg P_{A}(x)=n$
2. Il coefficiente di $x^n\text{ in }P_{A}(x)\text{ è }(-1)^n$
	$P_{A}(x)$ è un polinomio di grado $n$	

**NB.** Per il Teorema Fondamentale dell’Algebra, ogni polinomio a coefficienti complessi si fattorizza in fattori lineari.

Sia $A_{n\times n}$. Fattorizzo $P_{A}(x)$ in fattori lineari ($n$ fattori)
gli autovalori DISTINTI di $A$ sono $\lambda_1,\lambda_2,…,\lambda_{k},\ Spec(A)=\{\lambda_1,\lambda_2,…,\lambda_{k}\}$
$P_A(x)=c(x-\lambda_{1})$

3. $n$
4. $m_i=$ la _MOLTIPLICITÀ ALGEBRICA DELL’ AUTOVALORE $\lambda$ _

<u>TEOREMA</u>
Siano $A\ n\times n$ e $\lambda$ un autovalore di $A$,
se $d(\lambda)=$ moltiplicità geometrica di $A$
 e $m(\lambda)=$ moltiplicità algebrica di $A$ si ha $$1\leq d(A)\leq m(\lambda)$$
 Nelle matrici triangolari, gli autovalori sono i coefficienti nella sua diagonale.
$T=\left[\begin{matrix}t_{11}&t_{12}&…&&t_{1n}\\0&t_{22}&&*&\\0&0&t_{33}&&\vdots\\&&&\ddots&\\\mathbb{O}&&&&t_{nn}\end{matrix}\right]$

In particolare gli autovalori di una matrice DIAGONALE sono i numeri sulla diagonale.

##### Matrici simili ad Autovalori
> Due matrici $A\text{ e }B\ n\times n$ si dicono _SIMILI_ se $\exists S$ <u>non singolare</u> tale che $A=SBS^{-1}$

**NB.** $A$ è simile a $B\Longleftrightarrow B$ è simile ad $A$
$A=SBS^{-1}\Longleftrightarrow\quad S^{-1}AS=S^{-1}SBS^{-1}S$
$\Longleftrightarrow\exists S_{1}$ non singolare $B=S_{1}AS_{1}^{-1}$ prendo $S_{1}=S^{-1}$

<u>TEOREMA</u> Siano $A\text{ e }B\ (n\times n)$ simili. Allora
1. $P_{A}(x)=P_{B}(x)$ Quindi
	$Spec A= Spec B$
	$\forall\lambda\in SpecA\qquad({\text{la molteplicità algebrica}\atop\text{di }\lambda\text{ corrispondente in A}})=({\text{la molteplicità algebrica}\atop\text{di }\lambda\text{ corrispondente in B}})$
2. $\forall\lambda\in SpecA$
	$\dim E_{A}(\lambda)=\dim E_{B}(\lambda)$

#### Matrici diagonalizzabili
> $A_{n\times n}$ si dice _DIAGONALIZZABILE_ se è simile ad una matrice diagonale, cioè
> $\exists S$ non singolare e
> $\exists D$ diagonale tale che $A=SDS^{-1}$

Utilità:
Sia $A$ diagonalizzabile,
$\begin{align}A^{2}&=A\cdot A=(SDS^{-1})(SDS^{-1})\\&=SDS^{-1}SDS^{-1}\\&=SD^{2}S^{-1}\end{align}$

<u>TEOREMA (caratterizzazione delle matrici diagonali)</u>
Sia $A\ n\times n$ complessa
$\lambda_1,\lambda_2,…,\lambda_k$ gli autovalori distinti di $A$
$m_{1},m_{2},…,m_{k}$ le loro moltiplicità algebriche
$d_{1},d_{2},…,d_{k}$     le loro moltiplicità geometriche
$$A\text{ è DIAGONALIZZABILE}\Longleftrightarrow d_{i}=m_{i}$$
**NB.** $A$ ha autovalori distinti $\Longrightarrow A$ diagonalizzabile
Ma $A$ diagonalizzabile $\centernot\Longrightarrow A$ ha autovalori distinti

Questo quindi non basta per definire se $A_{n\times n}$ sia diagonalizzabile,
1. Costruzione di $D=\left[\begin{matrix}d_{1}&&&\mathbb{O}\\&d_{2}&&\\&&\ddots&\\\mathbb{O}&&&d_{n}\end{matrix}\right]$
	$\begin{rcases}d_{1},d_{2},…,d_{n}\text{ sono gli autovalori di D (perché D è diagonale)}\\\text{Gli autovalori di }D\text{ sono quelli di A (perché A e D sono simili)}\end{rcases}\Longrightarrow$
	$\Longrightarrow D=\left[\begin{smallmatrix}\lambda_1&&&&&&\\&\ddots&\leftarrow m_1&&&\mathbb{O}&\\&&\lambda_1&&&&\\&&&\lambda_2&&&\\&&&&\ddots&&\\&\mathbb{O}&&&&\lambda_2&\leftarrow m_k&&\\&&&&&&\vdots&\\&&&&&&&\lambda_k\end{smallmatrix}\right]$
	
2. Costruzione di $S$
	$\forall i=1,…,k$, sia $\mathcal{B}_i$ una base di $E_{A}(\lambda_i)$
	**NB.** $\mathcal{B}_i$ ha $d_i$ elementi
	Sia $\mathcal{B}_{i\quad}n=d_i$ 
	**NB1.** Si può dimostrare che, essendo $A$ diagonalizzabile
	**NB2.** $A=SDS^{-1}$

##### Matrice unitariamente diagonalizzabili
> $U$ Si dice _UNITARIA_ se $U^{-1}=U^{H}$

**NB.** $\begin{rcases}U\text{ unitaria}\\ U\text{ reale}\end{rcases}\Longrightarrow U$ ortogonale

> $A$ si dice _NORMALE_ se $AA^{H}=A^{H}A$

es. Matrici hermitiane, anti-hermitiane, unitarie

> $A$ si dice _UNITARIAMENTE DIAGONALIZZABILE_ se
> $\exists D$ diagonale
> $\exists U$ unitaria tale che $A=UDU^{-1}$

**NB.** $A$ unitariamente diagonalizzabile $\Longrightarrow A$ diagonalizzabile
							$\centernot\Longleftarrow$
<u>TEOREMA</u> (Caratterizzazione delle Matrici Unitariamente Diagonalizzabili)
$A$ è unitariamente diagonalizzabile $\Longleftrightarrow A$ è normale

**Teorema Spettrale: Versione MOLTIPLICATIVA**
Sia $A$ unitariamente diagonalizzabile (quindi sia $A$ normale, ossia $AA^{H}=A^{H}A$)$$\underset{n\times n}{A}=UDU^H\qquad(U^{-1}=U^{H})$$$\lambda_1,\lambda_2,…,\lambda_k$ gli autovalori distinti di $A$
$m_{1},m_{2},…,m_{k}$ le loro moltiplicità algebriche
$d_{1},d_{2},…,d_{k}$     le loro moltiplicità geometriche

1. Costruzione di $D$
	$D=\left[\begin{array}{|ccc|c|ccc|}\lambda_1&&&&&&\\&\ddots&\leftarrow m_1&&&\mathbb{O}&\\&&\lambda_1&&&&\\&&&\vdots&&&\\&&&&\lambda_k&&\\&\mathbb{O}&&&&\ddots&\leftarrow m_k\\&&&&&&\lambda_k\end{array}\right]$
2. Costruzione di $U$
	$\mathcal{B}_{i}^{H}$ base <u>ortonormale</u> di $E_{A}(\lambda_{i}),\ i=1,…,k$
	$Q_{i}\ n\times d_i$ matrice che ha come colonne i vettori di $\mathcal{B}_{i}^{H}$$$\underset{n\times n}{U}=[Q_{1}|Q_{2}|…|Q_{k}]$$
**Teorema Spettrale: Versione ADDITTIVA**

Osservazione: Sia $A\ 2\times2$. È diagonalizzabile? $\deg P_{A}(x)=2_{i}$
<u>1o caso</u> $P_{A}(x)=(x-\lambda_{1})(x-\lambda_{2}),\ $


