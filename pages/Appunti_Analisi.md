---
layout: page
title: Appunti analisi
share: true
---
Una carrellata di informazioni utili per l'appello di Analisi 1 @unipd
## Teoria
### Definizioni
Limite = 

Derivata = 

Integrale = 

Derivabilità di una funzione in x
### Teoremi
**Teorema di Rolle**
Sia $$f:[a,b]\rightarrow\mathbb{R}$$ continua e derivabile in $$]a,b[$$ tale che $$f(a)=f(b)$$ allora $$]X_{0} \in[a,b]:f'(x_0)=0$$.

**Teorema di Fermat**
Sia $$y=f(x)$$ una funzione con $$Dom(f)$$. Se $$x_{0}\in Dom(f)$$ è un punto di massimo o minimo relativo per f, e la funzione è derivabile in $$x_{0}$$ allora $$f'(x_{0})=0$$.

**Teorema di Lagrange**
Sia $$f:[a,b]\rightarrow\mathbb{R}$$ continua, derivabile in $$]a,b[$$ allora $$\exists c\in]a,b[$$ tale che $$f'(c)=\frac{f(b)-f(a)}{b-a}$$

**Teorema de l'Hopital**
Siano $$f,g:[a,b]\rightarrow\mathbb{R}$$ continue e derivabili in $$]a,b[-\{0\}$$. Supponiamo $$f'(x_{0})=g'(x_{0})$$ e $$g'(x)\neq0\quad\forall\ x\neq x_{0}$$. Allora esiste $$L=\lim_{x\rightarrow x_{0}}\frac{f'(x)}{g'(x)}=\lim_{x\rightarrow x_{0}}\frac{f(x)}{g(x)}$$

**Teorema fondamentale del calcolo integrale**
Se $$f:[a,b]\rightarrow\mathbb{R}$$ è continua e $$c\in[a,b]$$ definita $$F_{c}(x)=\int^{x}_{c}f(t)dt$$, allora Fc è derivabile e vale $$F'_{c}(x)=f(x)$$ per $$x\in[a,b]$$. 

**Teorema della media integrale**
### Criteri di convergenza
**Criterio del confronto**
Siano $$\sum\limits a_{n}$$ e $$\sum\limits b_{n}$$ due serie dai termini positivi, se $$a_{n}\leq b_{n}$$ definitivamente, allora se $$\sum\limits b_{n}$$ converge $$\sum\limits a_{n}$$ converge e se $$\sum\limits a_{n}$$ diverge $$\sum\limits b_{n}$$ diverge.

**Criterio del confronto asintotico**
Siano $$\sum\limits a_{n}$$ e $$\sum\limits b_{n}$$ due serie dai termini positivi, 

**Criterio del rapporto**
**Criterio della radice**
**Criterio di Leibniz**

## Pratica

$\sqrt{x(...)}\rightarrow|x|\sqrt{(...)}$$
### Limiti
**Equivalenze asintotiche**
(per $$x\rightarrow0$$)
$$\sin x\sim x\qquad 1-\cos x\sim\frac{1}{2}x^{2}\qquad \tan x\sim x$$
$$e^{1}\sim x\qquad (1+x)^{a}-1\sim ax$$
funzionano per rapporti, esponenziali e prodotti

### Integrali
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