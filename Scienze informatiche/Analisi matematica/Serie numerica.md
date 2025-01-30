”serie numerica = sommare infiniti addendi”
$$\begin{align}\sum_{x=0}^na_k=a_0+a_1+…+a_n\\\sum_{x=0}^{+\infty}a_k=a_0+a_1+a_2+…\end{align}$$
Definizione: data un successione $\{a_n\}$ di numeri reali si dice <u>serie di termine generale</u> le successioni $\{S_n\}_{n\in\mathbb{N}}$ definita da$$S_n=\sum_{x=0}^na_n\qquad\forall x\in\mathbb{N}$$cui $S_n$ è detta somma parziale della serie.

Definizione: la serie di termine generale $a_n\ (\sum_{k=0}^{+\infty}a_k)$ si dice
- <u>convergente</u> se $\displaystyle\lim_{n\rightarrow+\infty}S_n=s\in\mathbb{R}$ e si scrive 
	$\displaystyle\sum_{k=0}^{+\infty}a_k=s\quad$ (oppure $a_0+a_1+a_2+…=s$)
	si dice somma della serie.
- <u>divergente</u> a $+\infty$ (rispettivamente a $-\infty$) se $\displaystyle\lim_{n\rightarrow+\infty}S_n=+\infty$ 
	(rispettivamente a $\displaystyle\lim_{n\rightarrow+\infty}S_n=-\infty$)
- <u>indeterminata</u> se $\{S_n\}_{n\in\mathbb{N}}$ non ha limite $\displaystyle(\not\exists\lim_{n\rightarrow+\infty}S_n)$
Osservazione: spesso si parte da $k_0\in\mathbb{N}$ e non da 0, ossia considero $\sum_{k=k_0}^{+\infty}a_k$

Osservazione: con $q\neq1$$$\sum_{x=0}^n q^x=\frac{1-q^{n+1}}{1-q}$$(se $\displaystyle q=1\quad\sum_{k=0}^nq^k=\sum_{k=0}^n1^k=\sum_{k=0}^n1=n+1$)
Dimostrazione:
$\begin{aligned}(1-q)\sum_{k=0}^nq^k&=\sum_{k=0}^nq^k-q\sum_{k=0}^nq^k=\sum_{k=0}^nq^k-\sum_{k=0}^nq^{k+1}\\&=\sum_{k=0}^nq^k-\sum_{j=1}^{n+1}q^j=q^0-q^{n+1}=1-q^{n+1}\end{aligned}$
$\Longrightarrow (1-q)\sum_{k=0}^nq^k=1-q^{n+1}$
$\Longrightarrow\sum_{k=0}^nq^k=\frac{1-q^{n+1}}{1-q}$

Finita (convergente), infinita (divergente), indeterminata

**Serie geometrica**$$\begin{align}\sum_{k=0}^nr^k&=1+r^1+r^2+r^3+…+r^n+…\qquad r\in\mathbb{R}\\&=\lim_{n\rightarrow+\infty}\sum_{k=0}^nr^k\end{align}$$$\longrightarrow$ serie geometrica di ragione $r(\in\mathbb{R})$

Osservazioni: $\sum_{k=0}^nr^k\begin{cases}n+1&r=1\\ \frac{1-r^{n+1}}{1-r}&r\neq1\end{cases}$
- $r=1: \lim_{n\rightarrow n_0}\sum_{k=0}r^k$
- Cosa succede se $r\neq1$?
	$\lim_{n\rightarrow+\infty}\sum_{k=0}^nr^k=\lim_{n\rightarrow+\infty}\frac{1-r^{k+1}}{1-r}=$?
$\Longrightarrow\sum_{k=0}^nr^k=\begin{cases}\end{cases}$
Proposizione: dato la serie $\sum a_k$ e $\sum b_k$ se convergono entrambe e divergono entrambe a $+\infty$ o entrambe a $-\infty$, allora
$\sum_{k=0}^{+\infty}(ca_k)=c\sum a_k$
Ove si intende
$c(+\infty)=\begin{cases}+\infty&\text{se }c>0\\0&\text{se }c=0\\-\infty&\text{se }x<0\end{cases}\qquad c(-\infty)=\begin{cases}-\infty&\text{se }c>0\\0&\text{se }c=0\\+\infty&\text{se }x<0\end{cases}$

Proposizione:

Proposizione: Se $\sum a_k$ converge allora
1. Il suo resto $n$-esimo è infinitesimo
2. Il suo termine generale $a_n$ è infinitesimo
Dimostrazione:
1. Osservo $\sum_{k=0}^{+\infty}a_n=\underbrace{\sum_{k=0}^{+\infty}a_k}_{s\in\mathbb{R}}-\underbrace{\sum^{n-1}a_k}_{s_{n-1}}$
2. Osservo che $a_n=\sum_{k=0}^na_k-\sum_{k=0}^{n-1}a_k\longrightarrow s-s=0$
	$\Longrightarrow\lim_{n\rightarrow+\infty}a_n=0$ \[ossia $a_n$ è infinitesimo\]
### Criteri di convergenza
Teorema: $\sum a_n$ converge $\Longrightarrow a_n$ è infinitesimo
($a_n\not\rightarrow0\Longrightarrow\sum_{n=0}a_n$ NON più convergente)

Osservazione: non vale il viceversa, ovvero
$a_n\rightarrow0\centernot\Longrightarrow\sum_{n=0}^{+\infty} a_n$ convergente
Esempio: $\sum\frac{1}{\sqrt{k}}=+\infty$ ma $\frac{1}{\sqrt{k}}\rightarrow0$

**Criterio di Cauchy**: la serie $\sum a_k$ converge se e solo se $a_n=\sum a_k$ è successione di Cauchy, ovvero se e solo se
$\forall >0\quad\exists N>0\text{ t.c }|S-S|$

La serie armonica $\sum\frac{1}{k}$ diverge a $\infty$
Osservazione: vedremo che 
$\sum_{k=1}^{+\infty}\frac{1}{k^\alpha}$ converge se e solo se $\alpha>1$

**Convergenza assoluta di una serie**: 
si dice che $\displaystyle\sum_{k=0}^{+\infty}a_k$ converge assolutamente se $\displaystyle\sum_{k=0}^{+\infty}|a_k|$ converge.

Teorema: siano $\{a_k\}$ successioni tali che $\sum_{k=0}^{+\infty}a_k$ converge assolutamente (ossia $\sum_{k=0}^{+\infty}|a_k|$). Allora $\sum_{k=0}^{+\infty}a_k$ converge (semplicemente) e
$$\Big|\sum_{k=0}^{+\infty}a_k\Big|\leq\sum_{k=0}^{+\infty}|a_k|$$
Osservazione: non vale il viceversa. Esistono serie semplicemente convergente che non è assolutamente convergente.
Es: $\sum_{k=1}^{+\infty}\frac{(-1)^k}{k}$
$\sum_{k=1}^{+\infty}|\frac{(-1)^k}{k}|=\sum$

**Serie a termini positivi**
Proposizione: una serie di termine $a_n\geq0\ \forall n$ (o anche solo per $n\geq n_0$) o converge o diverge a $+\infty$.
Dimostrazione: Basta osservare che $S_n=\sum a_k$ è monotona crescente e che quindi $\displaystyle\exists\lim_{n\rightarrow+\infty}S_n$

#### 1. Criterio del confronto
Definizione: siano $\{a_k\}_{k\in\mathbb{N}},\ \{b_k\}_{k\in\mathbb{N}}$ successioni tali che 
$$0\leq a_k\leq b_k\qquad\text{definito per }k\rightarrow+\infty$$allora
1. se $\displaystyle\sum_{k=0}^{+\infty}b_k$ converge $\displaystyle\Longrightarrow\sum_{k=0}^{+\infty}a_k$ converge
2. se $\displaystyle\sum_{k=0}^{+\infty}a_k$ diverge $\displaystyle\Longrightarrow\sum_{k=0}^{+\infty}b_k$ diverge

Osservazione (importante): si confrontano spesso le serie con serie più facili di cui sappiamo la convergenza o divergenza.
Per esempio:$$\boxed{\sum_{k=0}^{+\infty}r^k\text{ che converge se e solo se }|r|<1}$$ovvero $$\boxed{\sum_{k=1}^{+\infty}\frac{1}{k^p}\text{ che converge se e solo se }p\in]0,1[}$$serie armonica generalizzata

Es: studiare il carattere della serie
$\sum_{k=1}^n\frac{2^n(n^2+\sin(e^n))}{3^n}$
Sol: $a\geq0$ 
Se avessi $a_n=(\frac{2}{3})^n\cdot b_n$
con $b_n$ tale che $(\frac{2}{3})^n\cdot b_n\leq c^n$ con $c\in]0,1[$
$\frac{\beta}{3}$

**1.1. Criterio del confronto asintotico**
Teorema: siano $\{a_k\},\ \{b_k\}$ successioni definite $\geq0$ per $x\rightarrow+\infty$ tali che$$\lim_{x\rightarrow+\infty}\frac{a_k}{b_k}=l=\bar{\mathbb{R}}\qquad\Big({{l\geq0\ \text{ o }}\atop{l=+\infty}}\Big)$$allora
1. se $\displaystyle l\in]0,+\infty[\Longrightarrow\sum_{k=0}^{+\infty}a_k\text{ e }\sum_{k=0}^{+\infty}b_k$ hanno lo stesso carattere;
2. se $l=0$ e $\displaystyle\sum_{k=0}^{+\infty}b_k$ converge $\displaystyle\Longrightarrow\sum_{k=0}^{+\infty}a_k$ converge;
3. se $l=+\infty$ e $\displaystyle\sum_{k=0}^{+\infty}b_k$ diverge $\displaystyle\Longrightarrow\sum_{k=0}^{+\infty}a_k$ diverge 
Dimostrazione: non lo facciamo.

$\Big[$Ricordo: $\displaystyle\sum_{k=1}^{+\infty}\frac{1}{k^p}<+\infty\Longleftrightarrow p>1\Big]$

#### 2. Criterio del rapporto
Teorema: sia $\{a_k\}$ una successione di termini positivi (oppure definita $\geq0$). Valgono allora le seguenti affermazioni
1. Se $\exists r\geq1$ tale che
	- a) $\frac{a_{k+1}}{a_k}\leq r$, definito per $x\rightarrow+\infty$
	oppure
	- b) $\displaystyle\lim_{k\rightarrow+\infty}\frac{a_{k+1}}{a_k}=r$
	allora $\displaystyle\sum_{k=0}^{+\infty}a_k$ converge;
2. Se 
	- a) $\frac{a_{k+1}}{a_k}\geq1$, definito per $k\rightarrow+\infty$
	oppure
	- b) $\displaystyle\lim_{k\rightarrow+\infty}\frac{a_{k+1}}{a_k}>1$
	allora $\displaystyle\sum_{k=0}^{+\infty}a_k$ diverge a $+\infty$

Dimostrazione: Consideriamo 1. e dimostriamo solo il suo a)
$\exists r\leq1$ tale che
$\frac{a_{k+1}}{a_k}\leq r\qquad\forall k\geq k_0$
$\Longrightarrow a_{k+1}\leq r\cdot a_k\qquad\forall k\geq k_0$
$\Longrightarrow a_{k_0+1}\leq r\cdot a_{k_0}$
Allora $$\frac{a_{k_0+1}}{a_{k_0}}\leq r\Longrightarrow a_{k_0+2}\leq r\cdot a_{k_0+1}\leq r(r\cdot a_{k_0})$$
In generale
$a_{k_0+1}$
$a_k r^{k-k_0}a_{k_0}$
Di conseguenza
$\sum a_k=\sum a_{k_0}+\sum a_k+\sum a_{k+2}$

Consideriamo 2. e dimostriamo a)
$\frac{a_{k+1}}{a_k}\geq 1$ definito per $x\rightarrow+\infty(a_k\neq0$ definito per $x\rightarrow$ )
$\Longrightarrow\frac{a_{k_0+1}}{a_{k_0}}\geq1$
Di conseguenza
$a_{k_0+k}\not\rightarrow0$
Quindi concludo che la serie diverge

**Serie esponenziale**$$\sum_{n=0}^{+\infty}\frac{x^n}{n!}$$
#### 3. Criterio della radice
Teorema: sia $\{a_k\}_{k\in\mathbb{N}}$ successione con $a_k\geq0\ \forall k$
1. $\exists r<1$ tale che
	1. $\sqrt{a_k}\leq r$ definito per $k\rightarrow+\infty$
	2. $\displaystyle\lim_{k\rightarrow+\infty}\sqrt{a_k}\leq r\leq1$
	Allora $\sum a_k$ converge
1. Se
	1. $\sqrt{a_k}\geq1$ definito per $k\rightarrow+\infty$
	2. $\displaystyle\lim_{k\rightarrow+\infty}\sqrt{a_k}$
	Allora la sua $\sum a_k$ diverge a $+\infty$

Dimostrazione: Considero 1. nel suo caso 1.
$\sqrt{a_k}\leq r\qquad\forall k\geq k_0$
$\Longrightarrow a_k\leq r^k\qquad\forall k\geq k_0$
$\Longrightarrow\sum_{k=0}^{+\infty}a_k\leq\sum_{k=0}^{k=1}a_k+\sum_{k=k_0}^{+\infty}a_k\leq\sum_{k=0}^{+\infty}a_k\leq\sum_{k=0}^{+\infty}a_k+\sum_{k=k_0}^{+\infty}a_k$
Considero 2. nel suo caso 1.

Se ho fattoriali usiamo il criterio del rapporto, nel caso di esponenziali o potenze, vanno bene entrambi.

**Serie logaritmica**$$\sum_{n=1}^{+\infty}(-1)^{n+1}\frac{x^n}{n}\qquad x\in\mathbb{R}$$<u>Convergenza assoluta</u>: $\displaystyle\sum_{n=0}^{+\infty}\Big|\frac{(-1)^{n+1}x^n}{n}\Big|=\sum_{n=0}^{+\infty}\frac{|x|^n}{n}$
Se $|x|>1$ allora $\lim\frac{}{}$
Però $\sum\frac{(-1)^nx^n}{n}$ potrebbe convergere se $|x|\geq1$. Devo considerarlo.
Osservo che se $|x|>1$, allora
$\lim|\frac{(-1)^nx^n}{n}|=+\infty$
Dobbiamo studiarlo quando $|x|=1$ ossia $x=1$ oppure $x=-1$
- se $x=-1$
	$\displaystyle\sum_{n=1}^{+\infty}\frac{(-1)^{n+1}x^n}{n}=\sum_{n=1}^{+\infty}\frac{(-1)^{n+1}(-1)^n}{n}=\sum_{n=1}^{+\infty}\frac{1}{n}$ che diverge a $+\infty$
- se $x=1$
	$\displaystyle\sum_{n=1}^{+\infty}\frac{(-1)^{n+1}x^n}{n}=\sum_{n=1}^{+\infty}\frac{(-1)^{n+1}1^n}{n}=\sum_{n=1}^{+\infty}\frac{(-1)^{n+1}1}{n}$
	Non converge assolutamente ma potrebbe convergere semplicemente. Abbiamo bisogno di un criterio nuovo.

#### 4. Criterio di Leibniz (serie a segno alterno)
Teorema: Sia $\{a_k\}_{k\in\mathbb{N}}$ successioni tale che
1. $a_k>0\qquad\forall k\in\mathbb{N}$
2. $\{a_k\}_{k\in\mathbb{N}}$ decrescente: $a_{x-1}\leq a_k\quad\forall k\in\mathbb{N}$
3. $a_k\rightarrow0$ per $k\rightarrow+\infty$
Allora $\displaystyle\sum_{k=0}^{+\infty}(-1)^ka_k$ converge.
Dimostrazione: non la facciamo.
Osservazione: Il criterio di Leibniz serve per la convergenza semplice, ma non quella assoluta.

Ritorniamo a 
$\displaystyle\sum_{n=1}^{+\infty}\frac{(-1)^{n+1}1}{n}\qquad\sum_{n=1}^{+\infty}(-1)^{n+1}\frac{1}{n}=(-1)\sum_{n=1}^{+\infty}(-1)^n\frac{1}{n}$ è serie a termini di segno alterno. Usiamo il criterio di Leibniz.
Devo verificare che $a_n=\frac{1}{n}$ soddisfi le ipotesi del criterio di Leibniz.
1. $a_n=\frac{1}{n}\geq0\quad\forall n\geq1?\qquad$SÌ 
2. $\{a_n\}_{n\geq1}$ decrescente?$\qquad\frac{1}{n+1}\leq\frac{1}{n}$ VERA $\forall n\geq1$
3. $a_n\rightarrow0$ per $n\rightarrow+\infty?\qquad\frac{1}{n}\rightarrow0$ per $n\rightarrow+\infty$ SÌ
$\Longrightarrow$ per il criterio di Leibniz, $\sum(-1)^n\frac{1}{n}$ converge. 