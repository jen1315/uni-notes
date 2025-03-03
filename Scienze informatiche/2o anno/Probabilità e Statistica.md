Statistica
- descrittiva, descrivere e sintetizzare dati
- inferenziale, trarre conclusioni dai dati

Sia $(X_{i})_{i\in\{1,...,n\}}$ un campione univariato
Ricorda:
media empirica (campionaria) $\bar{x}\doteq\frac{1}{n}\sum\limits_{i=1}^{n}x_{i}=\sum\limits_{j=1}^{k}v_{j}\cdot\frac{f_{j}}{n}$
dove $v_{j,...,n}$ sono valori distinti e $f_{j}$ la frequenza assoluta
varianza empirica $s^{2}\doteq\frac{1}{n-1}\left(\sum\limits_{i=1}^{n}(x_{i}-\bar{x})^{2}\right)$
$s=\sqrt{s^{2}}$ è deviazione standard empirica

Nota: Siano $a,b\in\mathbb{R}$. Poniamo $y_{i}=a\cdot x_{i}+b$
Allora
- $\bar{y}=a\cdot\bar{x}+b$
- $\begin{align*}s^{2}_{y}&=\frac{1}{n-1}\sum\limits_{i=1}^{n}(y_{i}-\bar{y})^{2}\\&=\frac{1}{n-1}\sum\limits_{i=1}^{n}(a\cdot x_{i}\cancel{+b}-(a\cdot\bar{x}\cancel{+b}))^2\end{align*}$

Nota: $s_{y}=\sqrt{s^{2}_{y}}=\sqrt{a^{2}\cdot s^{2}_{x}}=a\cdot s_{x}$
Trasformazione "lineare" della deviazione standard.
La deviazione standard ha la stessa unità di misura dei dati.

Varianza e deviazione standard campionaria permettono di stimare la proporzione dei dati che sono "lontani" o "vicini" alla media campionaria.

#### Disuguaglianza di Chebyshev (variazione campionaria)
Sia $(x_{i})_{i\in\{1,...,n\}}$ un campione univariato e siano $\bar{x}$ la media campionaria e s la deviazione standard.
Se $s>0$, allora per ogni $\alpha>0$
1. $\displaystyle\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|<\alpha\cdot s\}}{n}\geq1-\frac{n-1}{n\cdot\alpha^{2}}>1-\frac{1}{\alpha^{2}}$
2. $\displaystyle\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}\leq\alpha\cdot s_{x}|}{n}>1-\frac{n-1}{n\cdot\alpha^{2}}>1-\frac{1}{\alpha^{2}}$
3. $\displaystyle\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|\geq\alpha\cdot s\}}{n}\leq\frac{n-1}{n\cdot\alpha^{2}}<\frac{1}{\alpha^{2}}$
4. $\displaystyle\frac{\#\{i\in\{1,...,n\}:x_{i}-\bar{x}<\alpha\cdot s\}}{n}\leq1-\frac{n-1}{n+\alpha^{2}}$ (unilaterale)
Nota: stime 1. 2. 3. interessanti per $\alpha\geq1$
Nota: 3. implica 1.

Dimostrazione della 3.
$\displaystyle\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|\geq\alpha\cdot s\}}{n}=\frac{1}{n}\sum\limits_{i=1}^{n}\perp_{[\alpha\cdot s_{x})}()$
Notazione: funzione indicatrice
Sia $\Omega$ un insieme non-vuoto. La funzione indicatrice di un sotto-insieme $A\subseteq\Omega$ è data da $\perp_{A}\doteq\begin{cases}1&\text{se }x\in A\\0&\text{altrimenti}\end{cases}\qquad x\in\Omega$

$\displaystyle\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|\geq\alpha\cdot s\}}{n}=\frac{1}{n}\sum\limits_{i=1}^{n}\underbrace{\perp_{[\alpha^2\cdot s^2_{x})}(|x_i-\bar{x}|^2)}_{\leq\frac{|x_i-\bar{x}|^2}{\alpha^2\cdot s^2_x}}$
$\begin{align*}\rightsquigarrow\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|\geq\alpha\cdot s\}}{n}&\leq\frac{1}{n}\sum\limits_{i=1}^{n}\frac{(x_{i}-\bar{x})^2}{\alpha_{2}\cdot s^{2}_x}\\&=\frac{1}{\alpha^{2}\cdot s^{2}_{x}}\cdot\frac{1}{n}\underbrace{\sum\limits_{i=1}^{n}(x_{i}-\bar{x})^{2}}_{(n-1)\cdot s^{2}_{x}}=\frac{n-1}{n\cdot\alpha^{2}}\end{align*}$
Applicazione: $\alpha\in\{2,3,5\}$
dalla 1.
- $\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|<2\cdot s\}}{n}>\frac{3}{4}=75\%$
- $\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|<3\cdot s\}}{n}>\frac{8}{9}\approx89\%$
- $\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|<5\cdot s\}}{n}>\frac{24}{25}=96\%$

Analogamente dalla parte 3.
- $\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|\geq2\cdot s\}}{n}<\frac{1}{4}=25\%$
- $\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|\geq3\cdot s\}}{n}<\frac{1}{9}\approx11\%$
- $\frac{\#\{i\in\{1,...,n\}:|x_{i}-\bar{x}|\geq5\cdot s\}}{n}<\frac{1}{25}=4\%$
