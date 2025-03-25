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

**Disuguaglianza di Chebyshev (variazione campionaria)**
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


Statistiche per la distribuzione dei dati
Sia $(x_{i})_{i\in\{1,...,n\}}$ un campione univariato e sia $\sigma$ una permutazione che riordina i dati in ordine crescente dei valori:
> Def. Il *percentile campionario k-esimo*, con $k\in\{0,...,100\}$ del campione è dato da $$\overline{p}_{k}=\begin{cases}x_{\sigma(\lceil\frac{n\cdot k}{100}\rceil)}&\text{se }n\cdot\frac{k}{100}\not\in\mathbb{N}\\\frac{1}{2}(x_{\sigma(\frac{n\cdot k}{100})}+x_{\sigma(\frac{n\cdot k}{100}+1)})&\text{altrimenti}\end{cases}$$

Nota: $\overline{p}_{50}$ è la mediana campionaria.


Sia $(x_{i})_{i\in\{1,...,n\}}$ un campione d-variato di molteplicità n, cioè$$x_{i}=(x_{i1},...,x_{id})\in\mathbb{R}^{4}\text{ per ogni }i\in\{1,...,d\}$$Nota: per $\in\{1,...,d\},\quad(x_{i})_{i\in\{1,...,n\}}$ è campione univariato

Obiettivo: misura per la dipendenza tra le componenti
Caso più semplice $d=2\quad\Longrightarrow$ dati bivariati 
Sia $(x_{i}y_{i})_{i\in\{1,...,n\}}$ un campione bivariato, la quantità che misura la dipendenza "lineare-affine" tra le due componenti oppure tra due campioni bivariati con la stessa numerosità:
>Def. La *Covarianza Campionaria* tra $(x_{i})_{i=\{1,...,n\}}\text{ e }(y_{i})_{i=\{1,...,n\}}$ è data da$$Cov_{xy}=\frac{1}{n-1}\sum\limits_{i=1}^{n}(x_{i}-\bar{x})\cdot(y_{i}-\bar{y})$$dove $\bar{x}$ è la media campionaria di $(x_{i})$ e
>dove $\bar{y}$ è la media campionaria di $(y_{i})$

Nota: Se $x=y$ cioè $x_{i}=y_{i}\ \forall i\in\{1,...,n\}$ allora$$COV_{xy}=s^{2}_{x}=s^{2}_{y}$$-> "varianza = covarianza del campione con se stesso"

Attenzione: la varianza di un campione è sempre non negativa, mentre la varianza tra due campioni non identici, può essere anche negativa

Per avere una misura della dipendenza tra due campioni (o componenti) che non dipende dalle unità di misura, si normalizza la covarianza usando le deviazioni standard.

> Def. La *Correlazione Campionaria* tra $(x_{i})_{i=\{1,...,n\}}\text{ e }(y_{i})_{i=\{1,...,n\}}$ è data da$$Corr_{xy}=\frac{Cov_{xy}}{s_{x}\cdot s_{y}}$$dove $s_{x}$ è la deviazione standard campionaria di $x_{i}$ e
> dove $s_{y}$ è la deviazione standard campionaria di $y_{i}$

Osservazione:
1. $Corr_{xy}=\dfrac{\sum\limits_{i=1}^{n}(x_{i}-\bar{x})\cdot y_{i}-\bar{y}}{\sqrt{\sum\limits_{i=1}^{n}(x_{i}-\bar{x})^{2}}\cdot\sqrt{\sum\limits_{i=1}^{n}(y_{i}-\bar{y})^{2}}}$
   Nota: la parte $\frac{1}{n-1}$ si cancella
2. la correlazione campionaria assume valori tra -1 e 1. $Corr_{xy}\in[-1,...,1]$
   In particolare:
   - $Corr_{xy}=1$ se e solo se $\exists ab\in\mathbb{R},\ a>0$ e per ogni $i\in\{1,...,n\},\ y_{i}=a\cdot x_{i}+b$
   - $Corr_{xy}=-1$ se e solo se $\exists ab\in\mathbb{R},\ a<0$ e per ogni $i\in\{1,...,n\},\ y_{i}=a\cdot x_{i}+b$

La correlazione campionaria misura/quantifica la dipendenza lineare-affine tra due campioni (o componenti).
Dipendenza lineare-affine è massima se $|Corr_{xy}|=1$
Dipendenza lineare-affine è minima se $|Corr_{xy}|=0$

Correlazione positiva (vicino a 1) significa che i valori dei campioni vanno "alla stessa direzione".
Correlazione negativa (vicino a -1) significa che i valori dei campioni vanno "in direzioni opposte".

Per un campione d-variato $(x_{i})_{i\in\{1,...,d\}}$ con $x_{i}=(x_{id},...,x_{in})\in\mathbb{R}^{2}$ possiamo definire la matrice di covarianza $$C=(c_{k\ell})_{k,\ell\in\{1,...,d\}}\text{ con }c_{k\ell}=Cov_{x^{(k)}x^{(\ell)}}$$dove $x^{(k)}=(x_{ik})_{i\in\{1,...,d\}}\text{ e }x^{(\ell)}=(x_{i\ell})_{i\in\{1,...,d\}}$
Analogamente si definisce la matrice di correlazioni.

La matrice di covarianze da una misura delle dipendenze lineare-affini tra le d componenti di un campione d-variato.
Nota: C è una matrice dxd simmetrica. La diagonale di C è formata dalle varianze delle componenti $c_{\ell\ell}=s^{2}_{x}\text{ per }\ell\in\{1,...,d\}$
$v^{T}C\geq0$ per ogni $v\in\mathbb{R}^{d}$ -> C matrice 
-> esistono valori $\lambda_{1},...,\lambda_{d}\in\mathbb{R}$ e vettori $v^{(i)},...,v^{(d)}$ tali che $\lambda_{1}\geq...\geq\lambda_{d}\geq0,\ <v^{()},v^{()}>=\delta$
delta di kronecker$$C=(v^{(1)}...v^{(d)})\ \text{diag}(\lambda_{1}...\lambda_{d})(v^{(1)}...v^{(d)})$$
#### Spazi di probabilità
Modello statistico per descrivere esperimenti aleatori
Tre componenti:
1. Insieme di tutti gli esiti possibili dell'esperimento
   $\rightsquigarrow$ *spazio campionario*: insieme non vuoto $\Omega$
2. Insieme di tutte le affermazioni ammissibili sull'esito dell'esperimento
   $\rightsquigarrow$ *sistema degli eventi*: sottoinsieme $\mathcal{F}$ del sistema delle parti di $\Omega$, quindi $\mathcal{F}\in\mathcal{P}(\Omega)$
   Scelta stardard: se $\Omega$ è un insieme finito e numerabile ($\Omega$ al più numerabile), allora $\mathcal{F}\doteq\mathcal{P}(\Omega)$
3. Assegnazione di un "grado di fiducia" ad ogni affermazione ammissibile
   $\rightsquigarrow$ *misura di probabilità*: mappa $P:\mathcal{F}\rightarrow[0,1]$ dove 1 indica il massimo grado di fiducia e 0 il minimo grado di fiducia
   La valutazione degli eventi tramite la misura di probabilità deve essere coerente:
   (a) $P(\Omega)=1$
   (b) se $A,B\in\mathcal{F}$ con $A\cap B=\emptyset$ allora $P(A\cup B)=P(A)+P(B)$

Interpretazione logica delle operazioni insiemistiche
Siano $A,B\in\Omega,\ \Omega$ non-vuoto. Allora
- $A\cup B\qquad$"A o B"
- $A\cap B\qquad$"A e B"
- $A^{c}\doteq\{w\in\Omega:w\not\in A\}\qquad$"non A"
- $A\setminus B\doteq A\cap B^{c}\qquad$"A e non B"
- $A\triangle B\doteq(A\setminus B)\cup(B\setminus A)\qquad$"o A o B"
- $(A\setminus B)^{c}\qquad$"non A o B" <-> "se A allora B"

Modello matematico per un esperimento aleatorio
> Def. Una terna $(\Omega,\mathcal{F},P)$ si dice *spazio di probabilità* se
> 1. $\Omega$ è un insieme non-vuoto, lo spazio campionario
> 2. $\mathcal{F}$ è una $\sigma$-algebra in $\Omega$, il sistema degli eventi
> 3. P è una misura di probabilità in $\mathcal{F}$

>Def. $\mathcal{F}$ si dice $\sigma$-algebra in $\Omega$ se $\mathcal{F}\in\mathcal{P}(\Omega)$ e
>a. $\emptyset\in\mathcal{F}$
>b. se $A\in\mathcal{F}$ allora $A^{c}\in\mathcal{F}$
>c. se $(A_{i})_{i\in\mathbb{N}}\subset\mathcal{F}$ allora $\bigcup_{i\in\mathbb{N}}A_{i}\in\mathcal{F}$

Scelte estreme per una $\sigma$-algebra in $\Omega$
- $\mathcal{P}(\Omega)$ la $\sigma$-algebra totale
- $\{\emptyset,\Omega\}$ la $\sigma$-algebra triviale

Nota: Se $\mathcal{F}$ è una $\sigma$-algebra in $\Omega$
- $\emptyset,\Omega\in\mathcal{F}$
- $\mathcal{F}$ è chiusa risptto a unioni e intersezioni al più numerabili; in particolare se 

Osservazione: Se $\Omega$ è al più numerabile e $\mathcal{F}$ è una $\sigma$-algebra che contiene tutti i singoletti (quindi $\{u\}\in\mathcal{F}$ per ogni ) allora $\mathcal{F}=\mathcal{P}(\Omega)$

Terzo componente
Def. Sua $\mathcal{F}$ una $\sigma$-algebra in $\Omega$. Una mappa $P:\mathcal{F}\rightarrow[0,1]$ si dice misura di probabilità su $\mathcal{F}$ se
1. $P(\Omega)=1$
2. Se $(A_{i})_{i\in\mathbb{N}}\in\mathcal{F}$ è una successione di eventi *disgiunti a due a due*, cioè $A_{i}\cap A_{j}=\emptyset\text{ se }i\neq j$, allora
   $P(\bigcup A)$

Osservazione:
1. $(A_{i})$ implica l'additività finita
   $P(A\cup B)=P(A)+p(B)\text{ se }A\cap B=\emptyset$

Esempio: Sia $\Omega$ un insieme non-vuoto finito e sia $\mathcal{F}\doteq\mathcal(\Omega)$.
Definiamo $P:\mathcal{P}(\Omega)\rightarrow[0,1]$ tramite$$P(A)=\frac{A}{\Omega},\quad A\subseteq\Omega$$P è una misura di probabilità:
$(A|):\qquad P(\Omega)=\frac{A}{\Omega}=1$
$(A\delta):\qquad$ Siano $A_{1},A_{2},...,A_{n}\subseteq\Omega$ tali che $A_{i}\cap A_{j}=\emptyset\text{ se }i\neq j$.
	Allora $\displaystyle P(\bigcup_{i\in\mathbb{N}}A_{i})=\frac{|\bigcup_{i\in\mathbb{N}}A_{i}|}{|\Omega|}$
	Ma allora $|\bigcup_{i\in\mathbb{N}}A_{i}|=\sum\limits_{i=1}^{\infty}|A_{i}|$ poiché $A_{i}\cap A_{j}=\emptyset\text{ se }i\neq j$
	$\displaystyle\rightsquigarrow P(\bigcup_{i\in\mathbb{N}}A_{i})=\sum\limits_{i=1}^{\infty}\underbrace{\frac{|A_{i}|}{|\Omega|}}_{=P(A_{i})}=\sum\limits_{i=1}^{\infty}P(A_{i})$
Nota: Se P è la distribuzione uniforme discreta su $\Omega$, allora $$P(\{w\})=\frac{1}{|\Omega|}\text{ per ogni }w\in\Omega$$P è la misura di probabilità nel caso del lancio di un dado regolare ed equilibrato

##### Costruzione di misure di probabilità discrete
Sia $\Omega\neq\emptyset$ al più numerabile.
Se $\mathcal{F}=\mathcal{P}(\Omega)$ e P è una misura di probabilità su $\mathcal{F}=\mathcal{P}(\Omega)$, allora per ogni $A\subseteq\Omega$
$(*_{i})\qquad P(A)=\sum\limits_{w\in A}P(\{w\})$
Nota: $A=\bigcup_{w\in A}\{w\}$ unione al più numerabile di insiemi disgiunti a due a due
$(*_{i})$ vale grazie a $(A\delta)$

Quindi basta conoscere le probabilità dei singoletti
$\rightsquigarrow\Omega\rightarrow w\mapsto P(\{w\})$ definisce una funzione $p:\Omega\rightarrow[0,1]$
	con $\sum\limits_{w\in\Omega}p(w)=1$ grazie ad $(A|)$

> Def. Sia $\Omega\neq\emptyset$ arbitrario. Una funzione $p:\Omega\rightarrow[0,1]$ tale che $\sum\limits_{w\in\Omega}p(w)=1$ si dice *densità discreta* su $\Omega$.

Nota: Se p è una densità discreta su $\Omega$ allora $\{w\in\Omega:p(w)>0\}$ è al più numerabile.

Proposizione: densità discrete e misure di probabilità
Sia $\Omega\neq\emptyset$ insieme albitrario e sia $\mathcal{F}$ una $\sigma$-algebra in $\Omega$.
1. Se p è una densità discreta su $\Omega$ allora $P(A)\doteq\sum\limits_{w\in A}p(w)$
   definisce una misura di probabilità su $\mathcal{F}$. E' la misura di probabilità indotta da p.
2. Se $\Omega$ è al più numerabile e $\mathcal{F}$ contiene tutti i singoletti, allora $\mathcal{F}=\mathcal{P}(\Omega)$ e ogni misura di probabilità P su $\mathcal{P}(\Omega)$ corrisponde a una densità discreta.
   Questa corrispondenza è biunivoca ed è data da
	 - $p(w)=P(\{w\}),\qquad w\in\Omega$
	 - $P(A)=\sum\limits_{w\in A}p(w),\qquad A\subseteq\Omega$

**Densità campionaria**
Sia $(x_{i})_{i\in\{1,...,n\}}$ un campione di numerosità n di dati a valori in X 
definiamo $p:\mathcal{X}\rightarrow[0,1]$ tramite$$p(x)\doteq\frac{\#\{i\in\{1,...,n\}:x_{i}x\}}{n},\qquad x\in\mathcal{X}$$Allora p è una densità discreta su $\mathcal{X}$, la *densità campionaria* di $(x_{i})_{i\in\{1,...,n\}}$,
-> p induce una misura di probabilità P su $\mathcal{P}(\mathcal{X})$:
	$P(A)=\sum\limits_{x\in A}p(x),\qquad A\subseteq\mathcal{X}$
-> p misura campionaria (empirica)
Nota: p(x) è la frequenza relativa del valore x.

Singoletti evento per cui accade un solo esito.

Teorema: proprietà fondamentali delle misure di probabilità
Sia $(\Omega,\mathcal{F},P)$ uno spazio di probabilità e siano $A,B\in\mathcal{F}$.
1. Se $A\subseteq B$, allora $P(B/A)=P(B)-P(A)$
   In particolare, $P(A^{c})=1-P(A),\qquad P(\emptyset)=0$
2. $P(A\cup B)=P(A)+P(B)-P(A\cap B)$
   In particolare, se $A\cap B=\emptyset$ allora $P(A\cup B)=P(A)+P(B)$
3. Se $(A_{n})_{n\in\mathbb{N}}\subseteq\mathcal{F}$, allora $P(\bigcup_{n\in\mathbb{N}}A_{n})\leq\sum\limits_{n\in\mathbb{N}}P(A_{n})$
   In particolare (assioma della $\sigma$-additività)
   se $A_{i}\cap A_{j}=\emptyset\text{ per }i\neq j,\text{ allora }P(\bigcup_{n\in\mathbb{N}}A_{n})=\sum\limits_{n\in\mathbb{N}}P(A_{n})$
4. Sia $(A_{n})_{n\in\mathbb{N}}\subseteq\mathcal{F}$ tale che $A_{i}\cap A_{j}=\emptyset\text{ per }i\neq j\text{ e }\bigcup_{n\in\mathbb{N}}A_{n}=\Omega$
   Allora $P(B)=\sum\limits_{n\in\mathbb{N}}P(B\cap A_{n})$
   In particolare, $P(B)=P(B\cap A)+P(B\cap A^{c})$
5. Sia 

Ricorda: distribuzione uniforme discreta
Sia $\Omega\neq\emptyset$ finito. Allora la distribuzione uniforme discreta su $\Omega$ è dato da$$P(A)=\frac{|A|}{|\Omega|},\qquad A\subseteq\Omega$$Applicazione: estrazione di m palline da un'urna con N palline di cui M rosse e N-M verdi
Osservazione: numero delle palline rosse tra le palline estratte
Due schemi
1. estrazione con reinserimento
2. estrazione senza reinserimento
Calcolare la probabilità che esattamente K delle n palline estratte siano rosse

Schema 1.
Modello: palline numerate da 1 a N, prime M palline quelle rosse
$\underrightarrow{\text{n estrazioni}}\quad\Omega\doteq\{1,...,N\}$
Nota: $|\Omega|=N^{m}$
Per simmetria: tutti gli singoletti devono avere la stessa probabilità
-> P distribuzione uniforme discreta su $\Omega$

Eventi di interesse: $A_{k}\doteq$ "esattamente k delle n palline estratte sono rosse"
$\underrightarrow{\text{nel modello}}\quad\begin{align*}A_{k}&=\{w\in\Omega:\sum\limits_{i=1}^{n}\perp_{\{1,...,M\}}(w_{i})=k\}\\&=\{w\in\Omega:\#\{i\in\{1,...,n\}:w_{i}\in\{1,...,M\}\}=k\}\end{align*}$

Calcolare $P(A_{k})$
P distribuzione uniforme discreta
$\rightsquigarrow P(A_{k})=\frac{|A_{k}|}{|\Omega|},\quad\text{dove }|\Omega|=N^{m}$

Gli elementi di $A_{k}$ sono determinati da tre scelte successive
1. scelta delle posizioni delle k palline rosse (questo determina anche le posizioni delle palline verdi)
   scelta di un sottoinsieme di k elementi da un insieme di n elementi
   $\displaystyle\rightsquigarrow\left({n\atop k}\right)=\frac{n!}{k!(n-k)!}=\left({n\atop n-k}\right)$
2. scelta dei numeri ("identità") delle k palline rosse
   $\rightsquigarrow\quad M^{k}$ alternative (reinserimento!)
3. scelta dei numeri ("identità") delle n-k palline verdi
   $\rightsquigarrow\quad(N-M)^{n-k}$ alternative

$\xrightarrow[\text{del calcolo combinatorio}]{\text{principio fondamentale}}|A_{k}|=\left({n\atop k}\right)\cdot M^{k}\cdot(N-M)^{m-k}$

$P(A_{k})=\left({n\atop k}\right)\cdot(\frac{M}{N})^{k}\cdot(\frac{N-M}{N})^{n-k},\quad k\in\{0,...,n\}$

Nota: $\tilde{p}(k)\doteq\left({n\atop k}\right)\cdot(\frac{M}{N})^{k}\cdot(\frac{N-M}{N})^{n-k}$ definisce una densità discreta su $\{0,...,n\}$
Infatti $\sum\limits_{k=\sigma}^{n}\tilde{p}(k)=(\frac{M}{N}+\frac{N-M}{N})^{n}=1^{n}=1$
oppure 

Schema 2. 
estrazione di n palline senza reinserimento
Poniamo $\tilde{\Omega}=\{w\in\Omega:w_{i}\neq w_{j}\text{ per }i\neq j\}$ -> esiti senza ripetizioni di numeri (palline)

Definiamo una nuova misura di probabilità $\tilde{P}$ tramite$$\tilde{P}(A)\doteq\frac{P(A\cap\tilde{\Omega})}{P(\tilde{\Omega})},\quad A\subseteq\Omega$$Nota: $\tilde{P}(\tilde{\Omega})=1$

Calcolare $P(A_{k})$
$|\tilde{\Omega}|=N(N-1)(N-2)...(N-n+1)=\frac{N!}{(N-n)!}$

Gli elementi di $A_{k}\cap\tilde{\Omega}$ sono determinati attraverso tre scelte successive
1. scelta delle posizioni delle k palline rosse
   $\left({n\atop k}\right)$
2. scelta dei numeri delle k palline rosse
   $\frac{M!}{(M-k)!}$ alternative
3. scelta dei numeri delle n-k palline verdi
   $\frac{(N-M)!}{(N-M-(n-k))!}$ alternative

##### Probabilità condizionali e indipendenza
Sia $(\Omega,\mathcal{F},P)$ uno spazio di probabilità.
> Def. Sia $B\in\mathcal{F}$ con $P(B)>0$. Sia $A\in\mathcal{F}$. La quantità$$P(A|B)=P\frac{A\cap B}{P(B)}$$si dice *probabilità condizionale (o condizionata)* di A dato B.

Interpretazione: P(A|B) è il grado di fiducia che si assegna all'evento A supponendo che si sia verificato l'evento B.
Nota: P(B|B)=1, mentre $P(B^{c}|B)=0$

Esempio: Nella situazione di estrazioni di palline da un'urna senza reinserimento.
$\Omega=\{1,...,N\}^{n},\quad w=(w_{1},...,1_{n})$
P distribuzione uniforme discreta su $\Omega$
$\tilde{w\in\Omega:w_{i}\neq w_{j}\text{ per }i\neq j}$
$\tilde{\Omega}$ l'evento di estrarre solo palline distinte
Abbiamo posto
$\tilde{P}(A)\doteq P\frac{A\cap\tilde{\Omega}}{P(\tilde(\pi))},\quad A\in \Omega$

Nota: $\tilde{P}=(i)=P(i|B)$

Proposizione: Proprietà delle probabilità condizionali
Sia $(\Omega,\mathcal{F},P)$ uno spazio di probabilità.
1. Sia $B\in\mathcal{F}$ con P(B)=0, allora$$\mathcal{F}=$$
2. Siano $A_{1},...,A_{n}\in\mathcal{F}$ con $P(\bigcap\Omega)$. Allora$$P(\bigcap_{i=1}^{n}A_{i})=P(A_{i})\cdot\prod_{i=1}^{n}P(A_{i}|A_{1}\cap...\cap A_n)$$In particolare, se $P(A_{1}\cap A_{2})>0$, allora $P(A_{1}\cap A_{2})=P(A_{i})\cdot P(A_{2}|A_{1})$
3. Sia $(B_{i})$, una partizione al più numerabile di $\Omega$, cioè 7 al più numerabile, $B_{i}\cap B_{j}=\emptyset\text{ se }i\neq j\text{ e }\bigcup_{i\in7}B_{i}=\Omega$ tale che $B_{i}\in\mathcal{F}$ con $P(B_{i})>0$ per ogni $i\in7$. Allora, per ogni $A\in\mathcal{F}$$$P(A)=\sum\limits_{i\in7}\underbrace{P(A|B_{i})\cdot P(B_{i})}_{=P(A\cap B_{i})}$$In particolare, se $B\in\mathcal{F}$ tale che $P(B)\in(0,1)$, allora
   $\begin{align*}P(A)&=P(A|B)\cdot P(B)+P(A|B^{c})\cdot P(B^{c})\\&=P(A|B)\cdot P(B)+P(A|B^{c})\cdot(1-P(B))\end{align*}$
   Attenzione: 
   si ha sempre $P(A^{c}|B)=1-P(A|B)$
   ma, in generale $P(A|B^{c})\neq1-P(A|B)$

Teorema: *formula di Bayes*
Siano $A,B\in\mathcal{F}$ eventi con $P(A)>0,\ P(B)>0$. Allora$$P(A|B)=P\frac{A}{P(B)}\cdot P(B|A)$$Dimostrazione: $P(A|B)=P\frac{A\cap B}{P(B)}=P\frac{A}{P(B)}\cdot\frac{P(A\cap B)}{P(B)}$

Corollario:
Siano $A,B\in\mathcal{F}$ con $P(A)>0,\ P(B)\in(0,1)$. Allora$$P(B|A)=\frac{P(A|B)\cdot P(B)}{P(A|B)\cdot P(B)+P(A|B^{c})\cdot(1-P(B))}$$