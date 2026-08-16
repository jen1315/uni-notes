---
layout: page
title: Appunti analisi
share: true
---
Una carrellata di informazioni utili per l'appello di Analisi 1 @unipd

## Teoria
### > Definizioni

*Limite* = 

*Derivata* = Sia $$f:(a,b)\rightarrow\mathbb{R}$$ e $$x_{0}\in(a,b)$$, la derivata è il limite finito di 
$$\lim_{h\rightarrow0}\frac{f(x_{0}+h)-f(x_{0})}{h}=f'(x_{0})=c\in\mathbb{R}$$

*Integrale* = Sia $$f:[a,b]\rightarrow\mathbb{R}$$ limitata, consideriamo la suddivisione di \[a,b\] individuata dai punti x0,...,xn con $$x_{j}=a+jh$$ dove $$h=\frac{b-a}{n}$$ e $j=0,...,n$$ e scegliamo in ciascun intervallo $$[x_{j-1},x_{j}]$$, un punto albitrario $$\xi_{j}$. Costruiamo la somma di Cauchy-Riemann
$$S_{n}=\sum\limits_{j=1}^{n}f(\xi)\cdot(x_{j}-x_{j-1})=\frac{b-a}{n}\sum\limits_{j=1}^{n}f(\xi)$$
Il limite $$n\rightarrow+\infty$$ di questa somma è l'integrale di f in \[a,b\].
$$\lim_{n\rightarrow+\infty}S_{n}=\int_{a}^{b}f(x)dx$$

**Derivabilità di una funzione in x**
Una funzione è derivabile in $$x_{0}$$ se il limite sinistro e il limite destro del rapporto incrementale nel punto esistono finiti e uguali.
$$\lim_{h\rightarrow0^{-}}\frac{f(x_{0}+h)-f(x_{0})}{h}=\lim_{h\rightarrow0^{+}}\frac{f(x_{0}+h)-f(x_{0})}{h}=c\in\mathbb{R}$$

### > Teoremi
**Teorema di Rolle**
Sia $$f:[a,b]\rightarrow\mathbb{R}$$ continua e derivabile in $$]a,b[$$ tale che $$f(a)=f(b)$$ allora $$]X_{0} \in[a,b]:f'(x_0)=0$$.

**Teorema di Fermat**
Sia $$y=f(x)$$ una funzione con $$Dom(f)$$. Se $$x_{0}\in Dom(f)$$ è un punto di massimo o minimo relativo per f, e la funzione è derivabile in $$x_{0}$$ allora $$f'(x_{0})=0$$.

**Teorema di Lagrange**
Sia $$f:[a,b]\rightarrow\mathbb{R}$$ continua, derivabile in $$]a,b[$$ allora $$\exists c\in]a,b[$$ tale che 
$$f'(c)=\frac{f(b)-f(a)}{b-a}$$

**Teorema de l'Hopital**
Siano $$f,g:[a,b]\rightarrow\mathbb{R}$$ continue e derivabili in $$]a,b[-\{0\}$$. Supponiamo $$f'(x_{0})=g'(x_{0})$$ e $$g'(x)\neq0\quad\forall\ x\neq x_{0}$$. Allora esiste
$$L=\lim_{x\rightarrow x_{0}}\frac{f'(x)}{g'(x)}=\lim_{x\rightarrow x_{0}}\frac{f(x)}{g(x)}$$

**Teorema fondamentale del calcolo integrale**
Se $$f:[a,b]\rightarrow\mathbb{R}$$ è continua e $$x\in[a,b]$$ definita $$F(x)=\int^{x}_{c}f(t)dt$$, allora F è derivabile e vale $$F'(x)=f(x)$$. 
$$\begin{align}F'(x)&=\lim_{h\rightarrow0}\frac{F(x+h)-F(x)}{h}=\lim_{h\rightarrow0}\frac{\int_{0}^{x+h}f(t)dt-\int_{0}^{x}(t)dt}{h}\\&=\lim_{h\rightarrow0}\frac{\int_{0}^{x}f(t)dt+\int_{x}^{x+h}f(t)dt-\int_{0}^{x}(t)dt}{h}=\lim_{h\rightarrow0}\frac{1}{h}\int_{x}^{x+h}f(t)dt\\ x+h\rightarrow x\end{align}$$

**Teorema della media integrale**
Sia $$f$$ continua in $$[a,b]$$. Allora esiste $$c\in[a,b]$$ tale che 
$$f(c)=\frac{1}{b-a}\int_{a}^{b}f(t)dt$$
### > Criteri di convergenza
**Criterio del confronto**
Siano $$\sum\limits a_{n}$$ e $$\sum\limits b_{n}$$ due serie dai termini positivi, se $$a_{n}\leq b_{n}$$ definitivamente, allora se $$\sum\limits b_{n}$$ converge $$\sum\limits a_{n}$$ converge e se $$\sum\limits a_{n}$$ diverge $$\sum\limits b_{n}$$ diverge.

**Criterio del confronto asintotico**
Siano $$\sum\limits a_{n}$$ e $$\sum\limits b_{n}$$ due serie dai termini positivi, con $$b_{n}\neq0$$ per ogni $$n\in\mathbb{N}$$ e supponiamo che esiste 
$$\lim_{n\rightarrow+\infty}\frac{a_{n}}{b_{n}}=L$$
allora
- se $$L\in(0,+\infty)$$, le due serie hanno lo stesso carattere
- se $$L=0$$ e $$\sum\limits b_{n}$$ converge, $$\sum\limits a_{n}$$ converge
- se $$L=+\infty$$ e $$\sum\limits b_{n}$$ diverge, $$\sum\limits a_{n}$$ diverge

**Criterio del rapporto**
Siano $$\sum\limits a_{n}$$ una serie dai termini positivi e $$\lim_{n\rightarrow+\infty}\frac{a_{n}+1}{a_{n}}=L$$ allora
- se L>1, la serie converge
- se L>1, la serie diverge
- se L=1, non possiamo concludere niente.

**Criterio della radice**
Siano $$\sum\limits a_{n}$$ una serie dai termini positivi, se esiste $$\lim_{n\rightarrow+\infty}\sqrt[n]{a_{n}}=L$$
allora
- se L>1, la serie converge
- se L>1, la serie diverge
- se L=1, non possiamo concludere niente.

**Criterio di Leibniz**
Si consideri $$\sum\limits_{n\geq0}(-1)^{n}a_{n}$$ se
1. $$a_{n}\geq0$$ per ogni $$n\geq0$$
2. $$a_{n}\geq a_{n+1}$$ 
3. $$\lim_{n\rightarrow+\infty}a_{n}=0$$
allora la serie converge.

## Pratica

 $\sqrt{x(...)}\rightarrow|x|\sqrt{(...)}$$

Simmetrie
pari: $$f(-x)=f(x)\qquad$$ dispari: $$f(-x)=-f(x)$$

### > Limiti

$$\dfrac{\pm1}{0^{\pm}}=\pm\infty$$

**Equivalenze asintotiche**
(per $$x\rightarrow0$$)
$$\sin x\sim x\qquad 1-\cos x\sim\frac{1}{2}x^{2}\qquad \tan x\sim x$$
$$e^{1}\sim x\qquad (1+x)^{a}-1\sim ax$$
funzionano per rapporti, esponenziali e prodotti

### > Derivate
di polinomi composti
- somma/differenza
  $$\frac{d}{dx}[f(x)\pm g(x)]=f'(x)\pm g'(x)$$
- prodotto con costante
  $$\frac{d}{dx}[f(x)\cdot c]=f'(x)\cdot c$$
- prodotto
  $$\frac{d}{dx}[f(x)\cdot g(x)]=f'(x)g(x)+f(x)g'(x)$$
- rapporto
  $$\frac{d}{dx}[\frac{f(x)}{g(x)}]=\frac{f'(x)g(x)-f(x)g'(x)}{[g(x)]^{2}}$$
- funzione di funzione
  $$\frac{d}{dx}[f(g(x))]=f'(g(x))\cdot g'(x)$$

Candidati punti di massimo o minimo $$f'(x)=0$$
Studio della monotonia con disequazione: > crescente, < decrescente

Limiti ai estremi della derivata
se $$\sup/\inf f=\pm\infty$$ allora non c'è punto di massimo/minimo

### > Integrali
**Operazioni tra polinomi**
- somma/differenza
  $$\int f(x)\pm g(x)dx=\int f(x)\pm\int g(x)dx$$
- prodotto con constante
  $$\int cf(x)dx=c\int f(x)dx$$
- valore assoluto
  $$|\int f(x)dx|\leq\int|f(x)|dx$$


 $$\int f(g(x))g'(x)dx=F(g(x))+c$$
 $$\int f(x)g'(x)dx=f(x)g(x)-\int f'(x)g(x)dx$

**Frazione di polinomi**
1. DIVISIONE tra polinomi
   (saltare questo passo se gr N(x) < gr D(x))
2. FATTORIZZARE il denominatore
3. DECOMPORRE in frazioni$$\frac{1}{(x-c_{1})(x+c_{2})}=\frac{A}{x-c_{1}}+\frac{B}{x+c_{2}}=\frac{Ax+c_{2}A+Bx-c_{1}B}{(x-c_{1})(x+c_{2})}=\frac{(A+B)x+c_{1}A-c_{2}B}{(x-c_{1})(x+c_{2})}$$   $$\begin{cases}A+B=0\\ c_{1}A-c_{2}B=1\end{cases}\rightarrow\begin{cases}A=-B\\ B=\frac{-1+c_{1}A}{c_{2}}\end{cases}$$
4. INTEGRARE

Equazioni differenziali
**Problema di Cauchy**
$$\begin{cases}y'(t)+a_{0}(t)\cdot y(t)=g(t)\\ y(t_{0})=t_{0}\end{cases}$$

$$y(t)=e^{-A(t)}\left[y_{0}+\int_{t_{0}}^{t}(g(s)\cdot e^{A(s)})ds\right]$$
con $$A(t):=\int_{t_{0}}^{t}(a_{0}(s))ds$$

