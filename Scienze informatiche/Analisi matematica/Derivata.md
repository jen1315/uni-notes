
##### Calcolo differenziale
Supponiamo di avere un’automobile che si muove lungo una retta con una legge oraria
$\begin{aligned}s=&S(t)\\&\hookrightarrow\text{nel tempo t la proiezione dell’auto sulla retta è }S(t)\end{aligned}$
Voglio calcolare la velocità istantanea in $t_0$.
Calcolo la velocità media in $[t_0,t_0+h]$ con $h>0$$$\frac{S(t_0+h)-S(t_0)}{t_0+h-t_0}=\frac{S(t_0+h)-S(t_0)}{h}$$e pongo $h\rightarrow0$ se voglio la velocità istantanea$$V(t_0)=\lim_{h\rightarrow 0}\frac{S(t_0+h)-S(t_0)}{h}=\lim_{t\rightarrow t_0}\frac{S(t)-S(t_0)}{t-t_0}$$
Definizione: sia $I\subseteq\mathbb{R}$ intervallo, $x_0\in I,\ f:I\mapsto\mathbb{R}$ finita.
$$\lim\frac{f(x)-f(x_0)}{x-x_0}\Big(=\frac{f(x-x_0)-f()}{h}\Big)$$
Se la funzione esiste finito, $f$ è derivabile in $x_0$.
Se $f$ è derivabile in ogni punto $x_0\in I$, $f$ si dice derivabile in $I$.
Osservazione: Se $f$ è derivabile in $x_0$$$\exists f’(x_0)=\lim\frac{f(x)-f(x_0)}{x-x_0}\in\mathbb{R}$$$\Longrightarrow f(x)-f(x_0)=f’(x_0)(x-x_0)+o(x-x_0)\quad\text{per }x\rightarrow x_0$
$\Longrightarrow f(x)=f(x_0)+f’(x_0)(x-x_0)+o(x-x_0)$

$\begin{aligned}f’(x_0)=\lim\frac{}{}\end{aligned}$
Binomio di Newton $\Big({a\atop k}\Big)=\frac{n!}{k!(n-k)!}$

$\boxed{D\cos x=\sin x\quad\forall x\in\mathbb{R}}$
$\boxed{De^x=e^x\quad x\in\mathbb{R}}$
$\boxed{Da^x=(x)a^{x-1}}$
$\boxed{\ln|x|=\frac{1}{x}}$

Teorema: sia $I\subseteq\mathbb{R}$ intervallo, $x_0\in I,\ f:I\rightarrow\mathbb{R}$ derivabile in $x_0$. Allora $f$ è continua su $x_0$.
Osservazione: non vale il viceversa.

Derivata destra e derivata sinistra
Definizione: sia $I$ intervallo di $\mathbb{R},\ f:I\rightarrow\mathbb{R},\ x_0\in I$. Se esiste
$$\lim_{x\rightarrow x_0^+}\frac{f(x)-f(x_0)}{x-x_0}$$tale limite si dice derivata destra di $f$ in $x_0$ e si indica con$$f’_+(x_0)=D^+f(x_0)$$
Osservazione: se $\begin{aligned}f\text{ è derivabile da destra}\Longrightarrow\lim_{}f(x)\end{aligned}$
Teorema: $I:]a,b[,\ f:I\rightarrow\mathbb{R},\ x_0\in]a,b[$
$$f\text{ derivabile in }x_0\Longleftrightarrow\begin{cases}f\text{ derivabile in }x_0^+\\ f\text{ derivabile in }x_0^-\end{cases}$$
Teorema (algebra delle derivate): $f\cdot g$ derivabile in $x_0\in I,\ I$ 
1. $af$ è derivabile in $x_0$ e $(af)’(x_0)=af’(x_0)$
2. $f+g$ è derivabile in $x_0$ e $(f+g)’(x_0)=f’(x_0)+g’(x_0)$
3. $f\cdot g$ è derivabile in $x_0$ e $(f\cdot g)’(x_0)=f’(x_0)g(x_0)+f(x_0)g’(x_0)$
4. se $g(x_0)\neq0$ allora $f/g$ è derivabile in $x_0$ e $$(\frac{f}{g})’(x_0)=\frac{f’(x_0)g(x_0)-f(x_0)g’(x_0)}{(g(x_0))^2}$$
Osservazione: $(\frac{1}{b})’(x_0)$

Teorema (derivata della $f$ inversa)
$f:I\rightarrow\mathbb{R},\ I$ intorno aperto, $f$ continua, invertibile in $I$ e derivabile su $x_0$, tale che $f’(x_0)\neq0$
$$\boxed{(f^{-1})’(y_0)=\frac{1}{f’(x_0)}}$$
Teorema (della funzione composta o catena): siano $f,g$ $f$ reale di variabile reale tale che $fog$ sia definita in un intervallo $I$. Se $g$ è derivabile su $x_0$ e $f$ è derivabile su $g(x_0)$, allora $f\cdot g$ è derivabile in $x_0$ e su $l_g$.$$D\frac{f\cdot g(x_0)}{f(g(x_0))}=f’(g(x_0))g’(x_0)$$
Osservazione: $\underbrace{f^{-1}(f(x))}_{f^{-1}of(x)}=x\quad\forall x\in domf$
$\Longrightarrow\frac{d}{dx}(f^{-1}of)(x_0)=1$
$(f^{-1})’(f(x))$
$\Longrightarrow(f^{-1})’(y)=\frac{1}{f’(x)}=\frac{1}{f’(f’(f^{-1}(y)))}$
#### Punti di non derivabilità
Definizione: $I\in\mathbb{R}$ intervallo, $f:I\rightarrow\mathbb{R}$ una derivata sinistra $x_0$ e destra $x_0$ tale che $f’_-(x_0)\neq f‘_+(x_0)$ e almeno una delle due sia finita. Allora $x_0$ si dice <u>punto angoloso</u>.
Es: $f(x)=|x|,\ f’_-(0)=-1,\ f’_+(0)=1$

Definizione: sia $f:I\rightarrow\mathbb{R},\ I$ intorno aperto, $x_0\in I$ si abbia $f’(x_0)=+\infty$ o $f’(x_0)=-\infty$, allora $x_0$ si dice <u>punto di flesso a tangente verticale</u>.
Es: $\begin{aligned}f(x)&=sgn(x)\frac{\sqrt{|x|}},\ f’(0)=\lim_{x\rightarrow0}\frac{sgn(x)\sqrt{|x|}}{x}=\\&=\lim_{x\rightarrow0}\frac{\not sgn(x)\sqrt{|x|}}{\not sgn(x)|x|}=\lim_{x\rightarrow0}\frac{\sqrt{|x|}}{|x|}\end{aligned}$
$\Longrightarrow0$ è punto di flesso a $tg$ verticale

Definizione: $f:]a,b[\rightarrow\mathbb{R}$ continua in $x_0$ e $]a,b[$ tale che 
$\text{appare }\begin{aligned}f’_+(x_0)=-\infty\text{ e }f’_-(x_0)=+\infty\\f’_+(x_0)=+\infty\text{ e }f’_-(x_0)=-\infty\end{aligned}$

Teorema del limite della derivata: sia $I\subseteq\mathbb{R}$ intervallo, $f:I\rightarrow\mathbb{R},\ x_0\in I$. Sappiamo
1. $f$ sia continua su $x_0$
2. $f$ sia derivabile su $I\setminus\{0\}$
3. $\exists\lim_{x\rightarrow x_0}f’(x)$
Allora $\exists f’(x_0)$ e $f’(x_0)=\lim_{x\rightarrow x_0} f’(x)$
In particolare se $\lim_{x\rightarrow x_0}f(x)\in\mathbb{R}, f$ è derivabile.

Oss.1 : l’ipotesi di continuità è importante. Se valessero 1. e 2. ma il limite non esistesse, non potrei dire che la derivata non esiste.
Oss.2 : il teorema si può estendere alla derivata destra e sinistra.
$f:I\rightarrow\mathbb{R}$ derivabile su $I\setminus\{x_0\},\ x_0\in I$ tale che

Es: siano $a,b,c\in\mathbb{R}$ e siano
$f(x)=\begin{cases}x&\text{se }x<0\\ax^2+bx+c&\text{se }0\leq x<1\\x+1&\text{se }x>1\end{cases}$
Calcolare se esistono $a,b,c$ tale che $f$ sia continua e derivabile in tutta $\mathbb{R}$.
- Continuità in 0
	$f(0)=c\quad\lim_{x\rightarrow0^-}f(x)=0\quad\lim_{x\rightarrow0^+}f(x)=c$
	$\Longrightarrow$ devo avere $c=0$ in 1
	È continua in $\mathbb{R}$ se e solo se $\begin{cases}c=0\\a+b=2\end{cases}$
- Derivabilità in 0
	Calcolo $f’_-(0)$ e $f’_+(0)$
Mettiamo tutte le condizioni insieme
$\begin{cases}c=0&|\\ a+b=2&|\Longrightarrow\\ b=1&|\\ 2a+b=1\end{cases}\begin{cases}c=0\\a=1\\b=1\end{cases}$
$\Longrightarrow$ non ci sono valori in $a,b,c$ in cui $f$ sia continua e derivabile su tutta $\mathbb{R}$

###### Derivata di ordine superiore
Definizione: $I\subseteq\mathbb{R}$ intervallo, $f:I\rightarrow\mathbb{R}$ derivabile. Se $f’$ è derivabile in $x_0$ (ossia $\exists\lim\frac{}{}\in\mathbb{R}$) allora $f$ è derivabile due volte su $x_0$ e si dice che tale valore è la derivata seconda di $f$ su $x_0$ e si indica$$f’’(x_0),\ D^2f(x_0),\ \frac{d^2}{dx^2}f(x_0)$$più in generale
Definizione: $I\subseteq\mathbb{R}$ intervallo, $n\geq2,\ f:I\rightarrow\mathbb{R}$ derivabile $(n-1)$ volte. Se $f^{(n-1)}$, derivata di ordine $(n-1)$-esimo è derivabile in $x_0\in I$, la sua derivata in $x_0$ si dice derivata $n$-esimo di $f$ in $x_0$. Ossia$$f^{(n)}$$
$D(fg)=(Df)g+f(Dg)$
$D^2(fg)=(D^2f)g+Df\cdot Dg+Df\cdot Dg+f(D^2g)=D^2$

Teorema (formula di Leibniz): $f,g:I\rightarrow\mathbb{R}$ derivabile $n$ volte in $x_0\in I$. Allora $f\cdot g$ è derivabile in $x_0$ e si ha$$(fg)^{(n)}(x_0)=\sum_{k=0}^n\Big({n\atop k}\Big)f^{(n-k)}(x_0)g^{(k)}(x_0)$$Notazione: $I\subseteq\mathbb{R}$ intervallo, $f:I\rightarrow\mathbb{R}$
- $f$ si dice di classe $C^n$ se $f$ è derivatile $n$ volte in $I$ e $f^{(n)}$ e $C^0(I)$(ossia $f^{(n)}$ è continua in $I$)
- $f$ si dice di classe $C^\infty$ se $f$ è derivatile $n$ volte in $I$ per ogni $n\in\mathbb{N}$$$C^\infty(I)=\bigcap_{n\in\mathbb{N}}C^n(I)$$
Teorema di de L’Hôpital: siano $f,g:]a,b[\rightarrow\mathbb{R},\ a,b\in\bar{\mathbb{R}},\ f,g$ derivabile in $]a,b[$. Se
1. $g’(x)\neq0\qquad\forall x\in]a,b[$
2. $f(x),g(x)\rightarrow0\quad$per $x\rightarrow a^+$
	oppure
	$|f(x)|,|g(x)|\rightarrow+\infty\quad$per $x\rightarrow a^+$ 
3. $\exists\lim_{x\rightarrow a^+}\frac{f’(x)}{g’(x)}=l\in\bar{\mathbb{R}}$
Allora$$\begin{aligned}\lim_{x\rightarrow a^+}\frac{f(x)}{g(x)}=l\qquad\Big(\text{ossia }\lim_{x\rightarrow a^+}\frac{f(x)}{g(x)}=_{(H)}\lim_{x\rightarrow a^+}\frac{f’(x)}{g’(x)}\\\text{se quest’ultimo limite esiste}\Big)\end{aligned}$$Analogamente per $x\rightarrow b^-$ oppure per $x\rightarrow x_0\in]a,b[$.
In alcuni casi, “de l’Hôpital” però complica

Proposizione: $I\subseteq\mathbb{R}$ intervallo, $f:I\rightarrow\mathbb{R}$ derivabile in $I$ e tale che $f’(x)=0\quad\forall x\in I$. Allora $f$ è costante in $I$.

Dimostrazione: dobbiamo dimostrare che $\forall x_1,x_2\in I,\ x_1<x_2$ si ha $f(x_1)=f(x_2)$
In $[x_1,x_2]\ f$ soddisfa le ipotesi del teorema di Lagrange e quindi $\exists c\in]x_1,x_2[$ tale che$$\frac{f(x_2)-f(x_1)}{x_2-x_1}\quad f’(c)$$D’altra parte $f’(c)=0$ perché $f’(0)\ \forall x\in I$. Quindi$$\frac{f(x_2)-f(x_1)}{x_2-x_1}=0$$ho che $f(x_2)-f(x_1)$, ossia $f(x_1)=f(x_2)$.
Osservazione: è importante che $I$ sia un intervallo.

Teorema (test di monotonia): $f:]a,b[\rightarrow\mathbb{R}$ derivabile
1. $f$ è crescente $\Longleftrightarrow f’(x)\geq0\quad\forall x\in]a,b[$
2. $f$ è decrescente $\Longleftrightarrow f’(x)\leq0\quad\forall x\in]a,b[$
3. se $f’(x)>0\quad\forall x\in]a,b[\ \Longrightarrow f$ è strettamente crescente
4. se $f’(x)<0\quad\forall x\in]a,b[\ \Longrightarrow f$ è strettamente decrescente

Dimostrazione: dimostriamo solo 1). Osserviamo che 2) discende da 1. Prendendo $-f$. 3)  e 4) si dimostrano in maniera simile.

Siano $x,y\in]a,b[,\ y>x$. Allora $f(y)\geq f(x)$ ossia $f(y)-f(x)\geq0$
Se $y>x$$$\frac{f(y)-f(x)}{y-x}\geq0$$che$$\underbrace{\lim_{y\rightarrow x^+}\frac{f(y)-f(x)}{y-x}}_{f’(x)=f’_+(x)}\geq0$$e quindi $f’(x)\geq0$.
Posso ripetere il ragionamento $\forall x\in]a,b[$ $$f’(x)\geq0\qquad\forall x\in]a,b[$$Voglio dimostrare che se $x_1,x_2\in]a,b[$ e $x_1>x_2$, allora $f(x_2)\geq f(x_1)$

ossia $f(x_2)\geq f(x_1)$
che è ciò che volevo dimostrare.

Osservazione: 3) e 4) valgono solo in un verso:
$\exists f$ strett. crescenti tale che $f’(x)\not>0\quad\forall x\in X$
Non è vero che $f’(x)=3x^2>0\quad\forall x\in\mathbb{R}$, anche se $f$ è strettamente crescente (si annulla in $x=0$).

Osservazione: è importante avere un intervallo.
Osservazione: il test di monotonia si utilizza per studiare i punti critici. Supponiamo, , $f’(x_0)=0$. Se vedo che
$x<x_0\Longrightarrow f’(x)>0:f$ è strett. crescente se $x<x_0$
$x>x_0\Longrightarrow f’(x)<0:f$ è strett. decrescente se $x>x_0$

$x_0$ è punto di massimo locale
$x_0$ è punto di minimo locale
$x_0$
Analogamente

Es: $f(x)=x\log x,\ D=]0,+\infty[$
$$\lim_{x\rightarrow0^+}f(x)=0\qquad\lim_{x\rightarrow+\infty}f(x)=+\infty$$Segno di $f$
$f(x)=0\Longleftrightarrow\log x=0\Longleftrightarrow x=1$
$f(x)>0\Longleftrightarrow x log x>0\Longleftrightarrow\log >0\Longleftrightarrow1$

Derivabilità di $f$
$f(x)$ è il prodotto di $x$ (che è derivabile in $]0,+\infty[$) e $\log x$ (che è derivabile in $]a,b[$) $\Longrightarrow f(x)$ è derivabile in $]0,+\infty[$
$f’(x)>1\cdot\log x+x\cdot\frac{1}{x}=\log x+1\quad\forall x\in]0,+\infty[$

Segno di $f’$
$f’(x)=0\Longleftrightarrow\log x+1=0\Longleftrightarrow\log x=-1\Longleftrightarrow x=e^{-1}$
$f’(x)>0\Longleftrightarrow\log x+1>0\Longleftrightarrow\log x>-1\Longleftrightarrow x=e^{-1}$
$f’(1/e)=0\Longrightarrow\frac{1}{e}$ è punto stazionario 
$f’>0$ in $]\frac{1}{e},+\infty[\Longrightarrow f$ è strettamente crescente in $]\frac{1}{e},+\infty[$

##### Funzioni concave e convesse
Definizione: $I\subseteq\mathbb{R},\ f:I\rightarrow\mathbb{R}, \ I$ intervallo, $f$ è <u>convessa</u> in $I$ se $\forall x_1,x_2\in I,\ x_1\neq x_2$, il segmento che congiunge $(x_1,f(x_1))$ e $(x_2,f(x_2))$ non ha punti sotto il grafico di $f$ (“sta tutto sopra o sotto il grafico di $f$”).
Se gli unici punti che appartengono al grafico di $f$ sono gli estremi del segmento, allora $f$ si dice <u>strettamente convessa</u>.

Definizione $f:\mathbb{R}\supseteq I\rightarrow\mathbb{R},\ I$ intervallo è <u>concava</u> se $-f$ è convessa. $f$ è <u>strettamente concava</u> se $-f$ è strett. convessa.
Osservazione: si può 

Teorema: sia $f$ derivabile due volte in $I$ intervallo
- $f$ convessa in $I\Longleftrightarrow f^”(x)\geq0\quad\forall x\in I$
- $f$ concava in $I\Longleftrightarrow f^”(x)\leq0\quad\forall x\in I$
- $f^”(x)>0\quad\forall x\in I\Longrightarrow f$ strett. convessa in $I$
- $f^”(x)<0\quad\forall x\in I\Longrightarrow f$ strett. concava in $I$

La funzione cambia concavità nel punto di flesso.
Definizione: sia $x_0\in I,\ f:I\rightarrow\mathbb{R}$, dico che $x_0$ sia punto di flesso di $f$ se esiste un intorno $U$ di $x_0$ per cui $f$ cambia concavità e $\exists f’(x_0)$.

Teorema: $f:\mathbb{R}\supseteq I\rightarrow\mathbb{R},\ x_0$ punto di flesso per $f$ se $f$ è derivabile due volte in $x_0\Longrightarrow f^”(x_0)=0$.
Osservazione: 

##### Asindoti
Definizione: sia $f$ funzione reale di variabile reale
se $\lim_{x\rightarrow+\infty} f(x)=c\in\mathbb{R}\Longrightarrow$ la retta $y=c$ è asindoto orizzontale a $+\infty$
se $\lim_{x\rightarrow-\infty} f(x)=c\in\mathbb{R}\Longrightarrow$ la retta $y=c$ è asindoto orizzontale a $-\infty$

se $\lim_{x\rightarrow c}={+\infty\atop-\infty}$ la retta $y$ è asindoto verticale
Definizione: sia $f$ funzione reale di variabile reale, se $\exists m,q\in\mathbb{R}, m\neq0$ tale che
$\lim_{}\frac{f(x)}{x}=m$
$\lim f(x)-mx=q$
##### Formula di Taylor
$$f’(x)=\lim_{x\rightarrow X_0}\frac{f(x)-f(x_0)}{x-x_0}$$
$\Longrightarrow f(x)-f(x_0)=f’(x_0)(x-x_0)+o(x-x_0)$ per $x\rightarrow x_0$
$\Longrightarrow f(x)=f(x_0)+f’(x_0)(x-x_0)+o(x-x_0)$ per $x\rightarrow x_0$
$f=$ polinomio di grado 1 + errore di $o(x-x_0)$ 

**Polinomio di Taylor**
Definizione: Prendo $f:I\rightarrow\mathbb{R},\ I\subseteq\mathbb{R}$ intervallo, $x_0$ punto interno ad $I,\ f$ derivabile $n$ volte in $x_0$. Chiamo <u>polinomio di Taylor di grado n centrato in x0</u> il polinomio
$\begin{align}P_{x_0}^n(x)&=f(x_0)+f’(x_0)(x-x_0)+\frac{f^”(x_0)}{2!}(x-x_0)^2\\ &+\frac{f’^”(x_0)}{3!}(x-x_0)^3+…+\frac{f^{(n)}(x_0)}{n!}(x-x_0)^n\\ &\sum_{k=0}^n\frac{f^{(n)}(x_0)}{k!}(x-x_0)^k\end{align}$
ove $k!=k(k-1)(k-2)…1,\qquad 0!=1$
      $f^{(0)}=f$

**Formula di Taylor con il resto della forma di Peano**
Definizione: Se $f:I\rightarrow\mathbb{R},\ I\subseteq\mathbb{R}$ intervallo, $x_0$ punto interno di $I,\ f$ derivabile $n$ volte in $x_0$, allora
$$\begin{align}f(x)=&\underbrace{\sum_{k=0}^n\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k}+&&\underbrace{o((x-x_0)^n)}\quad \text{per }x\rightarrow x_0\\&\text{Polinomio di Taylor}&&\text{resto/errore che tende}\\&\text{ di ordine }n&&\text{a zero per }x\rightarrow x_0\\& &&\text{più velocemente di }(x-x_0)^n\end{align}$$
Notazione: se $x_0=0$, si chiamano polinomio e formula di McLaurin

Polinomio e formula di McLaurin
(nelle $n$ piccole nella formula di MCLaurin compaiono funzioni di esponenti dispari)

ERRORE GRAVE DA NON FARE
$\log(x)=\log(1+(x-1))=_{\text{Taylor di }\log(x-1)}$
Taylor funziona per $x$ che si avvicinano a 0 non -1

Osservazioni: $I\subseteq\mathbb{R}\setminus\{0\},\ o(x)$
#### Studio di funzioni
$f(x)=|\arctan(\log x)|$
1. Dominio: $]0,+\infty[$
2. $f$ è pari o dispari? Periodica?
	Il dominio non è simmetrico rispetto $0\Longrightarrow f$ non può essere nè pari nè dispari.
3. Limiti di $f$ agli estremi del dominio
	$\begin{aligned}&\lim_{x\rightarrow0^+}|\arctan(\log x)|=\frac{\pi}{2},\qquad&\lim_{x\rightarrow+\infty}|\arctan(\log x)|=\frac{\pi}{2}\\&\Longrightarrow\text{si può estendere per}&\Longrightarrow y=\pi/2\text{ è asin. orizzontale}\\ &\qquad\text{continuità in }0&\not\exists\text{ asin. obliqui a }+\infty\end{aligned}$
4. Segno di $f$
	
5. $f$ è continua? È continua lungo tutto il dominio
6. Derivabilità di $f$
	$f(x)=\begin{cases}-\arctan(\log x)&0<x<1\\\arctan(\log x)&x\leq1\end{cases}$
	$f^‘(x)=\begin{cases}-\frac{1}{1+(\log x)}&0<x<1\\\frac{1}{1+(\log x)}&x\leq1\end{cases}$
7. Punti critici e monotonia
	$|\frac{1}{1+(\log x)}|\neq0$
8. Derivata seconda
	$f^”(x)=-[((-1)(1+(\log x)^{-2}2\log x\frac{1}{x})\frac{1}{x}+\frac{1}{1+(log x)^2}\frac{(-1)}{x^2}]$
	$(-1)\frac{1}{(1+(\log x)^2)^2}2\log x\frac{1}{x^2}$
	- $\forall x\in]0,1[$
		$f^”(x)=-[((-1)(1+(\log x)^{-2}2\log x\frac{1}{x})\frac{1}{x}+\frac{1}{1+(log x)^2}\frac{(-1)}{x^2}]\geq0$
		$f^”(x)>0\quad\forall x\in]0,1[\setminus\{1/2\},\ f^”(1/2)=0$
		$\Longrightarrow f$ è strett convessa in $]0,1[$
	- $\forall x\in]1,+\infty[$
		$f^”(x)=-[((-1)(1+(\log x)^{-2}2\log x\frac{1}{x})\frac{1}{x}+\frac{1}{1+(log x)^2}\frac{(-1)}{x^2}]\leq0$
		$\Longrightarrow f$ è strett concava in $]1,+\infty[$ 
		Estremi locali`
		$f$ non ha massimo locale. $f$ ha minimo locale in $x=1$.
		$x=1$ è punto di minimo assoluto e il min ass è $f(1)=0$