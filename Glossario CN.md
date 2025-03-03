##### 1. Sistema binario e sistema floating-point IEEE754 dei numeri macchina

##### 2. Errori assoluto e relativo, errore di rappresentazione
Dato un $x\in\mathbb{R}^{n}$ e una norma fissata $\|\cdot\|$ per $\mathbb{R}^{n}$, l'errore assoluto è$$err_{ass}(\tilde{x}):=\|x-\tilde{x}\|$$mentre l'errore relativo è$$err_{rel}(\tilde{x}):=\frac{\|x-\tilde{x}\|}{\|x\|}\qquad\text{se }\|x\|\neq0$$Gli errori di rappresentazione sono gli errori causati dalla rappresentazione dei numeri in un sistema limitato. In particolare, prendiamo in considerazione i floating point durante troncamento e arrotondamento.
L'errore assoluto di rappresentazione è$$err_{ass}(fl^{Tr/Ar}(x))=|x-fl^{Tr/Ar}(x)|$$mentre l'errore relativo di rappresentazione è$$err_{rel}(fl^{Tr/Ar}(x)):=\frac{|x-fl^{Tr/Ar}(x)|}{|x|}\qquad\forall|x|\neq0$$Stimiamo l'errore di rappresentazione
- Troncamento
- Arrotondamento
##### 3. Operazioni macchina, loro (non) proprietà, precisione macchina
Per ogni operazione reale $\ast$, viene associata una operazione macchina $\circledast$ definita come$$x\circledast y=fl(fl(x)\ast fl(y))$$Alle operazioni macchina, non valgono le normali proprietà delle operazioni
- non è commutativa
- non è associativa
- non distribuisce rispetto a $\oplus$
- gli elementi neutri $\oplus,\odot$ non sono unici
- non vale la proprietà di cancellazione

Def. La **precisione macchina** è il più piccolo numero floating pont positivo $\varepsilon_{MACH}$ per cui$$fl(1+\varepsilon_{MACH})\neq1$$
##### 4. Stabilità di un algoritmo, stabilità delle operazioni macchina e cancellazione numerica
Un algoritmo si dice **stabile** se "non amplifica in modo incontrollato gli errori presenti sui dati". Vogliamo una stima di stabilità $$err_{rel}(output)\leq C_{STAB}\cdot err_{rel}(input)$$
##### 5. Problema matematico, buona posizione
Gli problemi matematici che affronteremo sono nella forma
"Trovare $\underset{\text{dominio}}{x\in X}:F(x,d)=0,\  \underset{\text{dati ammissibili}}{d\in D}$"

Un problema matematico è detto *ben posto* quando
- ha la definizione del suo dominio e dei dati ammissibili
- $\forall d\in D,\quad\exists! x\in X:F(x,d)=0$
- $d\longmapsto x(d)$ soluzione del problema è continua
##### 6. Condizionamento numerico assoluto e relativo di un problema ben posto
Un problema si dice ben condizionato se "una piccola variazione dei dati corrisponde a piccole variazioni della soluzione".
NUMERO DI CONDIZIONAMENTO
*locale* (di ordine $\alpha$) in $d\in D$$$\lim_{\tilde{d}\rightarrow d}\sup\frac{|x(\tilde{d})-x(d)|}{|\tilde{d}-d|^{\alpha}}\leq k_{\alpha}(d)\qquad0<\alpha\leq1$$*globale* (di ordine $\alpha$) in D$$\sup_{d\in D}k_{\alpha}(d)\leq k_{\alpha}<+\infty$$Osservazione: Il buon condizionamento è una proprietà del problema, non del metodo di soluzione.
##### 7. Numero di condizionamento di una matrice e stima dell'errore relativo della soluzione di un sistema lineare con termine noto affetto da errore (con dimostrazione). Cosa succede se perturbiamo anche la matrice (no dimostrazione).
In un sistema lineare $Ax=b$ con termine noto $b$ affetto da errore.
$\tilde{b}\approx b\qquad A\tilde{x}=\tilde{b}$
$\tilde{b}=b+\delta_{b}\qquad\tilde{x}=x+\delta_{x}\qquad$ voglio stimare l'errore relativo $\dfrac{\|\delta_{x}\|}{\|x\|}$
$\begin{rcases}A(x+\delta_{x})=b+\delta_{b}\\ Ax=b\end{rcases}\Rightarrow A\delta x=\delta b$
A è invertibile quindi $\delta_{x}=A^{-1}\delta_{b}$
e in particolare $\|\delta_{x}\|=\|A^{-1}\delta_{b}\|$ 

In un sistema lineare $Ax=b$ dove sia A che b sono affetti da errore.
$(A+\delta_{A})(x+\delta_{x})=b+\delta_{b}$
$(A+\delta_{A})\delta_{x}=\cancel{b}+\delta_{b}-\cancel{Ax}-\delta_{A}x$

##### 8. Algoritmi di sostituzione avanti e sostituzione indietro, condizioni per l'applicabilità.
Usabile solo se A è triangolare superiore o inferiore.
$x(n)=b(n)/A(n,n)$

##### 9. Fattorizzazione LU senza pivoting: algoritmo, limitazioni alla sua applicabilità e problematiche numeriche


##### 10. Algoritmo LU con pivoting parziale per righe "idea" del pivoting e sua motivazione, output dell'algoritmo (no dettagli dell'algoritmo)
##### 11. Punti fissi, lemma delle contrazioni con dimostrazione.
##### 12. Metodi iterativi lineari stazionari per soluzione di Ax=b: idea generale, condizioni per la consistenza, possibili vantaggi, risultato di convergenza generale che si deduce dal lemma delle contrazioni
##### 13. Metodo di Richardson: definizione, analisi della convergenza tramite norma e tramite proprietà spettrali (serie di Neumann).
##### 14. Precondizionamento del metodo di Richardson e metodi di Jacobi e di Gauss Seidel
##### 15. Lemma dei cerchi di Gerschgorin e matrici strettamente diagonalmente dominanti, applicazione alla convergenza di Jacobi.
##### 16. Criteri di arresto per metodi iterativi per la soluzione di sistemi lineari: residuo relarivo e step
##### 17. Sistemi sovradeterminati esistenza e unicità della soluzione, minimi quadrati come generalizzazione del concetto di soluzione
##### 18. Teorema delle proiezioni ortogonali ed equazioni normali con dimostrazione
##### 19. Metodo QR per la soluzione delle eq normali
##### 20. Radici di un eq non lineare: condizioni per l'unicità, condizioni per l'esistenza e metodo di bisezione (con dimostrazione)
##### 21. Radici semplici e radici di molteplicità maggiore di 1, condizionamento del calcolo di radici
Def "Molteplicità di una radice"


##### 22. Metodo di Newton: euristica e definizione. Teorema di convergenza locale per radici semplici con dimostrazione
Teorema: "convergenza locale per radici semplici"
Dato un $f\in\mathcal{C}^{2}([a,b])$ e un $x^{*}$ radice semplice di $f\in[a,b]$, esiste un intorno I di $x^{*}$ tale che il metodo di Newton inizializzato con $x_{0}\in I$ converge a $x^{*}$. Inoltre si ha$$\lim_{k\rightarrow+\infty}\frac{|e_{k+1}|}{|e_{k+1}|^{2}}=\left|\frac{f''(x^{*})}{2f'(x^{*})}\right|$$