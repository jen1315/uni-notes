Es.1 
Per definizione $s^{2}=\frac{1}{n-1}\sum\limits_{i=1}^{n}(x_{i}-\bar{x})$
$\bar{\mu}_{2}=\frac{1}{n}\sum\limits_{i=1}^{n}(x_{i}-\bar{x})^{2}$
In funzione del momento campionario centrato del secondo ordine
$s^{2}=\frac{n}{n-1}\cdot\bar{\mu}_{2}$
$\begin{align*}s^{2}&=\frac{n}{n-1}\cdot\mu_{2}-\frac{2n}{n-1}(\bar{x})^{2}+\frac{n}{n}-1(\bar{x})^{2}\\&=\frac{n}{n-1}(\mu_{2}-(\bar{x})^{2}\end{align*}$
In funzione dei momenti campionari del primo e secondo ordine

Esercizio. 3
a) 9!
b) 8!

Esercizio. 4
200 cassetti numerati da 1 a 200
300 palline indistinguibili
Ogni cassetto deve contenere almeno una pallina. Quanti modi abbiamo per distribuirli?

Idea: 300 palline in fila, distribuire 200-1=199 separatori su 300-1=299 posizioni tra le palline
`**|***|...`
$\left({299\atop199}\right)$

Esercizio. 5
100 cassetti numerati da 1 a 100
5050 palline distinti
i oggetti devono finire nel cassetto i-esimo. Quanti modi abbiamo per distribuirli?
Nota: $\sum\limits_{i=1}^{100}i=5050$

Ponendo M numero di cassetti e n palline da distribuire e $k_{i}$ la numerazione del cassetto
Scelte successive
1. $k_{1}$ oggetti nel primo cassetto: $\left({n\atop k_{1}}\right)$ alternative
2. $k_{2}$ oggetti nel secondo cassetto: $\left({n-k_{1}\atop k_{2}}\right)$ alternative
$\xrightarrow[\text{del calcolo combinatorio}]{\text{principio}}\left({n\atop k_{1}}\right)\cdot\left({n-k_{1}\atop k_{2}}\right)\cdot...\cdot\left({n-\sum\limits_{i=1}^{M}k_{i}\atop k_{m}}\right)$ 

Esercizio. 7
52 carte da gioco poker
seme: picche, fiore, quadro, cuore
tipo: 2,...,10, J, Q, K, A
Se peschiamo 5 carte, quanta probabilità abbiamo che
$({52\atop 5})$
1. almeno 2 carte dello stesso tipo
2. un poker: quattro carte dello stesso tipo e una quinta carta
3. un full: tre carte di un tipo e due carte di un altro tipo
4. un full con una sola carta rossa

Cardinalità di $A^{c}:\quad|A^{c}|=({13\atop5})\cdot 4^{5}$
$({13\atop5})$ scelta dei 5 tipi diversi
$4^{5}$ scelte dei semi (su 4) per le 5 carte
$\squigarrow\quad P(A^{c})=({13\atop5})/$