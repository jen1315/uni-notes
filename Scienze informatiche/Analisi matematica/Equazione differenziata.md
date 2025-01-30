$$g’(y)=x\atop g(y)=\int x=\frac{x^2}{2}+c$$Es. Modello popolazione
$P(t)=$ popolazione Italia nell’anno $t=2000$
La popolazione dipende solo dalle nascite $N(t)$ e morti $M(t)$
$P(t+1)-P(t)=N(t)-M(t)$
Il tasso di nascite e di morti sono costanti $(\frac{\text{nascite}}{\text{morti}})$. 
$\Longrightarrow\alpha P(t)-\beta P(t)=(\alpha-\beta)P(t)=\gamma P(t)$
Sappiamo che la popolazione iniziale in $t=0$ è $P_0\geq0$.
Il nuovo sistema
$\Longrightarrow\begin{cases}P(t+1)-P(t)=\gamma P(t)\\ P(0)=P_0\end{cases}$
ammette una sola soluzione: $P(t)=(1+\gamma)^tP_0$

Questa è una equazione funzionale; trasformiamola in una differenziale generalizzandolo.
$P(t)$ è continua e derivabile. $t$ non è più un anno preciso ma una variabile tempo con variazione di $\epsilon$.
$P(t+\epsilon)-P(t)=gP(t)\epsilon$

$\begin{cases}\dfrac{P(t-\epsilon)-P(t)}{\epsilon}=gP(t)\\ P(0)=P_0\end{cases}$
 
$P(t)=e^{gt}P_0$

Definizione: un’equazione differenziale generica è una equazione dove può comparire una qualsiasi funzione e le sue derivate$$F[x,y(x),y’(x),y^{”}(x),…,y^{n-1}(x)]=0$$L’ordine di una equazione, definisce il numero di parametri

Equazioni di primo ordine 
$y=\frac{x^2}{2}+c$
$$\begin{cases}y’(x)=f[x,y(x)]\\ y(x_0)=y_0\end{cases}$$
È chiamato problema di Cauchy
Può avere
- 1 soluzione
- nessuna soluzione
- più soluzioni

Equazioni a variabile separabili
$y’=xy$
Assumiamo di conoscere la soluzione $y(x)$
$\displaystyle y’(x)=xy(x)\quad\rightarrow\quad\frac{y’(x)}{y(x)}=x$
$\int\frac{y(x)}{y(x)}dx=\int x\ dx=\frac{x^2}{2}+c$

Nelle equazioni a variabile separabili, posso separare tutte le funzioni a $x$ da tutte quelle a $y$.
$\boxed{y’}$
1. Pongo le variabili y al primo membro
2. Integro i termini in x
3. Integro i termini in y
4. Metto insieme

$$y’=f(y)g(y)\quad\Longrightarrow\quad\frac{y’}{g(y)}=f(x)$$
Es. $\begin{cases}y’=\frac{x^2}{y}=\frac{1}{y}\cdot x^2\\ y(0)=1\end{cases}\qquad y(x)=\sqrt{\frac{2}{3}-1}$
$yy’=x^2$
$\int_0^x x^dx=\frac{}{}$

#### Equazioni del primo ordine (lineari)
$$a_0(x)y(x)+a_1(x)y’(x)+…+a_{n-1}(x)y^{(n-1)}(x)+a_n(x)y^{(n)}(x)=b(x)$$dove $a_0,a_1,a_2,…a_n,b$ sono funzioni note.
I coefficienti che dipendono da $x$
$y$ sono di grado 1 e sono moltiplicate per costanti o per funzioni in $x$.

L’equazione si dice **omogenea** se e solo se la funzione x è identicamente nulla, ovvero che $b(x)=0$.

L’equazione generale$$a_1(x)y’+a_0(x)y=b(x)$$
a cui assumiamo che:
- $a_1(x),a_0(x),b(x)$ sono continue
- $a_1(x)$ non si annulla
Può essere riscritta come$$y’=\tilde{a}(x)y+\tilde{b}(x)$$

CASO $\tilde{b}(x)=0$	$$y’=a(x)y$$che è un’equazione differenziale a variabili separabili riscrivibile così$$\frac{y’}{y}=a(x)$$
CASO $\tilde{b}(x)\neq0$ (generica)$$y’=a(x)y+b(x)$$non è separabile ma, ponendo $\displaystyle\tilde{A}(x)=\int\tilde{a}(x)dx$ si riesce a ricavare una soluzione esatta con$$\boxed{y(x)=e^{\tilde{A}(x)}\Big[\int e^{-\tilde{A}(x)}b(x)dx+c\Big]}$$
#### Equazione del secondo ordine
$$a_2y^”(x)+a_1y’(x)+a_0y(x)=0$$
L’ordine si riferisce al numero di parametro che si trovano nell’equazione, in questo caso $c_1,c_2\in\mathbb{R}$.
$$y(x)=c_1e^{\lambda_1x}+c_2e^{\lambda_2x}$$
A cui poniamo $\lambda_1=1,\ \lambda_2=0$$$y(x)=e^{\lambda_1x}\qquad{y’(x)=e^{\lambda_1x}\lambda_1\atop y^”(x)=e^{\lambda_1x}\lambda_1^2}$$$\lambda_1$ soluzione dell’equazione
$(*)\ a_2\lambda^2+a_1\lambda+a_0=0\quad\Longleftarrow\quad a_2y^”a_1y’+a_0y=0$
$$\lambda_1,\lambda_2=\frac{-a_1\pm\sqrt{\Delta}}{2a_2}\qquad\Delta=a_1^2-4a_2a_0$$
CASO $\Delta>0$
Ci sono due soluzioni 

CASO $\Delta=0$
C’è una sola soluzione

CASO $\Delta<0$
Ci sono due soluzioni distinte ma complesse
$\lambda_1,\lambda_2\frac{}{}\begin{cases}\end{cases}$
Formula esponenziale dei numeri complessi: sia $\beta$ è un numero reale$$e^{\beta x}=\cos\beta+i\sin\beta$$
### Funzioni a due o più variabili
$\mathbb{R}^2=\{(a,b)|a,b\in\mathbb{R}\}$
insieme delle coppie di variabili reali
$\mathbb{R}^3=\{(a,b,c)|a,b,c\in\mathbb{R}\}$
insieme delle tuple di variabili reali
etcetera…

$n\in\mathbb{N}\quad\mathbb{R}^n$ $$a_i,b_i(x_1,x_2,x_3,…,x_n)=x\quad x_i\in\mathbb{R}^n$$**vettori di $R^n$**

#### Operazioni
**Somma e differenza di vettori**
$x+y=(x_1+y_1,x_2+y_1,…,x_n+y_n)$
$x-y=(x_1-y_1,x_2-y_2,…,x_n-y_n)$

**Prodotto di un vettore per un numero reale $\alpha\in\mathbb{R}$ (scalare)**
$\alpha\cdot x=(\alpha x_1,\alpha x_2,…,\alpha x_n)$

**Prodotto scalare**
$x\cdot y=x_1y_1+x_2y_2+…+x_ny_n$

Niente divisione, logaritmi, esponenziale, etc

**Modulo (distanza dall’origine)**
In $\mathbb{R}^2$, ovvero in un piano con origine $0=(0,0)$, possiamo usare il teorema di Pitagora $|(a,b)|=\sqrt{a^2+b^2}$

In generale, quindi con origine $0=(0_1,0_2,…,0_n)$
$|x|=\sqrt{x_1^2+x_2^2+…+x_n^2}$

#### Insiemi
Non possiamo definire intervalli, perché non possiamo definire un vettore più grande o piccolo. Possiamo però definire molti insiemi.

**Rettangoli / parallelepipedi**
Rettangolo $=\{x\in\mathbb{R}^2|a_1\leq x_1\leq b_1,a_2\leq x_2\leq y_2\}$
Parallelepipedo $=\{x\in\mathbb{R}^3|a_1\leq x_1\leq b_1,a_2\leq x_2\leq y_2,a_3\leq x_3\leq y_3\}$

In generale$$\{x\in\mathbb{R}^n|a_i\leq x_i\leq b_i;\forall i\in\mathbb{N}\}$$
**Cerchi / sfere**
Cerchio aperto $=\{x\in\mathbb{R}^n||x-x_0|<r\}$
Cerchio chiuso

#### Limiti
Data una funzione $f:\Omega\subseteq\mathbb{R}^n\rightarrow\mathbb{R}$, con $x\in\Omega$ esiste $\ell\in\mathbb{R}$ tale che
$$\lim_{x\rightarrow x_0}f(x)=\ell\Longleftrightarrow\forall\epsilon>0,\exists\delta>0$$

$\{x\in\mathbb{R}^n\}$
#### Derivata parziale
$f’(x_1,x_2)=x_1x_2$
È possibile sceglie una sola variabile e rendere le altre costanti.
$\dfrac{\vartheta f(x_1,x_2)}{\vartheta x_1}=x_2\qquad\dfrac{\vartheta f(x_1,x_2)}{\vartheta x_2}=x_1$

#### Integrali
$$\int\Big[\int f(x_1,x_2)dx_1\Big]dx_2$$
Si calcola prima l’integrale interno, dove $x_1$ è variabile e $x_2$ costante, poi quello esterno dove è viceversa.

Osservazione: $x_2$ essendo costante, può apparire come intervallo dell’integrale interno.

**Massimi e minimi**
$f(x,y)$
1. Trovare $\dfrac{\vartheta f}{\vartheta x},\ \dfrac{\vartheta f}{\vartheta y}$
2. $\nabla f(x,y)=\Big(\dfrac{\vartheta f}{\vartheta x}(x,y),\dfrac{\vartheta f}{\vartheta y}(x,y)\Big)$
3. Trovo tutte le coppie di $(x,y)|\nabla f(x,y)=(0,0)$ tale che sia si annullano, questi punti sono punti critici
4. $Hf(x,y)=\begin{pmatrix}\dfrac{\vartheta^2f}{\vartheta x^2}(x,y)&\dfrac{\vartheta^2f}{\vartheta y\vartheta x}(x,y)\\\dfrac{\vartheta^2f}{\vartheta x\vartheta y}(x,y)&\dfrac{\vartheta^2f}{\vartheta y^2}(x,y)\end{pmatrix}$
5. Faccio il determinante della matrice hessiana
	- se $\det M>0$ è o massimo o minimo
		$\dfrac{\vartheta^2f}{\vartheta x^2}$ è MIN se $>0$ e MAX se $<0$ 
	- se $\det M<0$ non è massimo o minimo
	- se $\det M=0$ non possiamo dire niente

Determinante
$M=\begin{pmatrix}a&b\\ c&d\end{pmatrix}\qquad\det M=a\cdot d-b\cdot c$
