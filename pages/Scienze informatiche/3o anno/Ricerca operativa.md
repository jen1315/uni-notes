---
title: Ricerca operativa
layout: page
share: true
---
Supporto ai processi decisionali in sistemi complessi
La scelta migliore per raggiungere un obiettivo con vincoli imposti. Ottimo certificato

Problema decisionale reale --formulazione->
Modello --deduzione-> Soluzione del modello
<-interpretazione-- Soluzioni del problema reale

*Costruzione del modello*
1. insiemi (elementi del sistema) e parametri (dati del problema)
2. variabili decisionali (incognite)
3. funzione obiettivo
4. vincoli del problema (relazione tra incognite)

Modelli matematici: funzione obiettivo e vincoli sono espressi come relazioni matematiche tra le variabili matematiche. I vincoli sono sempre a due a due. E’ dichiarativo.

> ❗ Ricordarsi i vincoli di dominio.

|           | Prodotti          | Risorse                                |
| --------- | ----------------- | -------------------------------------- |
| Insiemi   | {Lattuga, Patata} | {terreno, semi, tuberi, fertilizzante} |
| Parametri | 3000, 5000        | 11, 70, 10, 145                        |
Dobbiamo trovare 
$$x_{L}:$$ quantità in ettari da destinare a lattuga
$$x_{P}:$$ quantità in ettari da destinare a patata

Funzione obiettivo: $$\max 3000x_{L}+5000x_{P}$$

Vincoli
$$\begin{array}{l l}1x_{L}+1x_{P}\leq 11&\text{(ettari disponibili)}\\7x_{L}\leq70&\text{(semi disponibili)}\\3x_{P}\leq18&\text{(tuberi disponibili)}\\10x_{L}+20x_{P}\leq145&\text{(fertilizzante disponibile)}\\x_{L}\geq0, x_{P}\geq0&\text{(dominio)}\end{array}$$

Soluzione grafica
![[IMG_9469.png|IMG_9469.png]]
Area sotto i vincoli si chiama politopo e rappresenta il l’insieme delle soluzioni ammissibili.

Non funziona quando le variabili da trovare superano i 3.
Consideriamo che la soluzione ottima si trova sul perimetro del politopo. Con i *modelli di programmazione lineare* si trovano in particolare sui vertici, calcolabili con l'algebra.

> ❗ I vincoli di interezza rendono il problema molto più difficile.
> Non si può usare la geometria.

si devono definire le unità di misura se esistono
in questo corso, ignoriamo i parametri incerti

s.t. (subject to)

Si possono avere più variabili ma si deve controllare di gestire i vincoli tra essi
Quando si possono usare sia = che $$\geq\text{ o }\leq$$, quest'ultimi sono preferibili perché più

### Schemi base di modellazione

$$I:$$ insieme di risorse, $$J:$$ insieme di domanda
$$c_{j}:$$ coefficienti di costo (min) o profitto (max)
$$a_{ij}:$$ coefficienti tecnologici (parametri) 
$$b_{i}:$$ termini noti (parametri)
$$z:$$ funzione obiettivo
$$x_{j}:$$ variabili decisionali 

> **Modello di costo minimo**$$\begin{array}{lll}\min&\sum\limits_{i\in I}C_{i}x_{i}&\\ s.t.\\&\sum\limits_{i\in I}A_{ij}x_{i}\geq D_{j}&\forall i\in J\\&x_{i}\in\mathbb{R}_{+}[\mathbb{Z}_{+}|\{0,1\}]&\forall i\in I\end{array}$$

Il modello del mix ottimo di produzione è simile a quello del costo minimo ma usando il massimo e con vincoli al $$\leq$$ sulla quantità di risorse disponibili.

>**Modelli di trasporto**$$\begin{array}{lll}\min&\sum\limits_{i\in I}\sum\limits_{i\in J}C_{ij}x_{ij}&\\ s.t.\\&\sum\limits_{i\in J}x_{ij}\leq O_{i}&\forall i\in I\\&\sum\limits_{i\in I}\geq D_{j}&\forall i\in J\\&x_{ij}\in\mathbb{R}_{+}[\mathbb{Z}_{+}|\{0,1\}]&\forall i\in I, j\in J\end{array}$$

---
Al lunedì sono richiesti 17 infermieri, al martedì 13, al mercoledì 15, al giovedì 19, al venerdì 14, al sabato 16 e alla domenica ne servono 11. Ogni turno di lavoro dura 5 giorni ininterrotti.

$$y_{t}:\#$$ infermieri del turno t={lu, ma, me, gio, ve, sa, do}
$\begin{array}{llllllll}\min &y_{lu}+&y_{ma}+&y_{me}+&y_{gio}+&y_{ve}+&y_{sa}+&y_{do}&\\ s.t.\\&y_{lu}+&&&y_{gio}+&y_{ve}+&y_{sa}+&y_{do}&\leq17\\&y_{lu}+&y_{ma}+&&&y_{ve}&y_{sa}+&y_{do}&\leq13\\&y_{lu}+&y_{ma}&y_{me}+&&&y_{sa}+&y_{do}&\leq15\\&y_{lu}+&y_{ma}&y_{me}+&y_{gio}+&&&y_{do}&\leq19\\&y_{lu}&y_{ma}&y_{me}+&y_{gio}+&y_{ve}+&&&\leq14\\&&y_{ma}&y_{me}+&y_{gio}+&y_{ve}+&y_{sa}+&y_{do}&\leq16\\&&&y_{me}+&y_{gio}+&y_{ve}+&y_{sa}+&y_{do}&\leq11\\&y_{lu},&y_{ma},&y_{me},&y_{gio},&y_{ve},&y_{sa},&y_{do}&\in\mathbb{Z}_{+}\end{array}$

E' consigliato risolvere la formulazione del modello in modo incrementali dalle descrizioni del testo.

---
Si vuole scegliere le località in cui attivare un CUP in modo che il tempo medio di arrivo da ogni quartiere sia sotto i 15 minuti.

|      | loc1 | loc2 | loc3 | loc4 | loc5 | loc6 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| qt.1 | 5    | 10   | 20   | 30   | 30   | 20   |
| qt.2 | 10   | 5    | 25   | 35   | 20   | 10   |
| qt.3 | 20   | 25   | 5    | 15   | 30   | 20   |
| qt.4 | 30   | 35   | 15   | 5    | 15   | 25   |
| qt.5 | 30   | 20   | 30   | 15   | 5    | 14   |
| qt.6 | 20   | 10   | 20   | 25   | 14   | 5    |

$$L:$$ insieme delle località
$$Q:$$ insieme dei quartieri
$$x_{\ell}:$$ 1 se attivo e 0 se non attivo

$\begin{array}{llllllll}\min &5x_{1}&+20x_{2}&+7x_{3}&+15x_{4}&+10x_{5}&+16x_{6}&\\ s.t.\\&x_{1}&+x_{2}&&&&&\geq1\\&x_{1}&+x_{2}&&&&+x_{6}&\geq1\\&&&x_{3}&x_{4}&&&\geq1\\&&&x_{3}&+x_{4}&+x_{5}&&\geq1\\&&&&x_{4}&x_{5}&x_{6}&\geq1\\&&&&&x_{5}&x_{6}&\geq1\\&x_{1},&x_{2},&x_{3},&x_{4},&x_{5},&x_{6}&\in\{0,1\}\end{array}$

---
Si possono investire in A e B: A profitta 0.4 dopo due anni e B profitta 0.7 dopo tre anni. Dal secondo anno si può investire in C che profitta il doppio dopo 4 anni. Dal quinto anno si può investire in D che profitta 0.3 ogni anno. 
Vogliamo massimizzare i profitti in sei anni con un budget totale di 10000.

$$x_{ij}:\text{ investiti in }i\in\{A,B,C,D\}\text{ per l'anno }j\in\{1,2,3,4,5\}$$
$\max0.4(x_{A1}+x_{A2}+x_{A3}+x_{A4})+0.7(x_{B1}+x_{B2}+x_{B3}+x_{B4})+x_{A1}+x_{A2}+x_{A3}+x_{A4}+0.3$

| s.t.                           |                           |                                                                            |                                                                  |
| ------------------------------ | ------------------------- | -------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| $$x_{A1}+x_{B1}+x_{C1}+x_{D1}$$  | $$\leq10000$$               |                                                                            |                                                                  |
| $$x_{C1}=0,\ x_{D1}=0$$          |                           |                                                                            |                                                                  |
| $$x_{A2}+x_{B2}+x_{C2}+0x_{D2}$$ | $$\leq10000$$               | $$-x_{A1}$$<br>$$-x_{B1}$$                                                     | $$-x_{C1}$$<br>$$-x_{D1}$$                                           |
| $$x_{A3}+x_{B3}+x_{C3}+0x_{D3}$$ | $$\leq10000$$               | $+0.4x_{A1}-x_{A2}$$<br>$$-x_{B1}-x_{B2}$$                                    | $$-x_{C1}-x_{C2}$$<br>$$-x_{D1}-x_{D2}$$                             |
| $$x_{A4}+x_{B4}+x_{C4}+0x_{D4}$$ | $$\leq10000$$               | $$+0.4(x_{A1}+x_{A2})-x_{A3}$$<br>$$+0.7x_{B1}-x_{B2}-x_{B3}$$                 | $$-x_{C1}-x_{C2}-x_{C3}$$<br>$$-x_{D1}-x_{D2}-x_{D3}$$               |
| $$x_{A5}+x_{B5}+x_{C5}+x_{D5}$$  | $$\leq10000$$               | $$+0.4(x_{A1}+x_{A2}+x_{A3})-x_{A4}$$<br>$$+0.7(x_{B1}+x_{B2})-x_{B3}-x_{B4}$$ | $$-x_{C1}-x_{C2}-x_{C3}-x_{C4}$$<br>$$-x_{D1}-x_{D2}-x_{D3}-x_{D4}$$ |
|                                | $$x_{ij}\in\mathbb{R}^{+}$$ | $$\forall i\in\{A,B,C,D\}$$                                                  | $$\forall j\in\{1,2,3,4,5\}$                                      |

---
Vogliamo modelli lineari: min-max, max-min e abs non sono funzioni lineari.
Gestiamoli nei vincoli.

I batch 1,2,3,4,5 devono essere eseguite in ordine in una macchina monoprocessore e hanno una durata di 5,7,4,7,10 minuti. Il primo batch ha una consegna desiderata di 10.32, il secondo 10.38, il terzo 10.42, il quarto 10.52 e il quinto 10.57. l,,.z
Si ha una penale di 750 euro per ogni minuto in anticipo o ritardo alla consegna. Minimizzare la penale totale.

$$\min |i_{1}+5-H_{1}|+|i_{2}+7-H_{2}|+|i_{3}+4-H_{3}|+||$$
s.t.
	$$i_{1}+5\leq i_{2}\qquad i_{2}+7\leq i_{3}$$
	$$i_{3}+4\leq i_{4}\qquad i_{4}+7\leq i_{5}$$

---
Una catena ha un budget W per aprire nuovi ipermercati. J sono le possibili localizzacioni. Per aprire un ipermercato nella località i bisogno sostenere un costo fisso $$F_{i}$$ e un costo variabile $$C_{i}$$ ogni 100mq. Una volta aperti, ogni ipermercato produrrà entrate di $$R_{i}$$ ogni 100mq.
Vogliamo massimizzare i ricavi complessivi.

$$x_{i}:$$ quantità di m^[2] aperti in $$i\in I$$ (in 100mq)
$$y_{i}=\begin{cases}F_{i}&\text{se }x_{i}>0\\0&\text{se }x_{i}=0\end{cases}$$

$\begin{array}{lll}\max&\sum\limits_{i\in I}R_{i}{\color{red}x_{i}y_{i}}\\\text{s.t.}&&\\&\sum\limits_{i\in I}C_{i}{\color{red}x_{i}y_{i}}+F_{i}y_{i}\leq W&\text{(budget)}\\&x_{i}\in\mathbb{R}_{+},\ y_{i}\in\{0,1\}&\forall i\in I\end{array}$

Non è un modello lineare. Si definisce un *vincolo "big-M"* dove M è una costante sufficientemente grande per attivare le variabili binarie.

$\begin{array}{lll}\max&\sum\limits_{i\in I}R_{i}x_{i}\\\text{s.t.}&&\\&\sum\limits_{i\in I}C_{i}x_{i}+F_{i}y_{i}\leq W&\text{(budget)}\\&x_{i}\leq My_{i}\ \forall i\in I&\text{(attivazione delle variabili binarie)}\\&x_{i}\in\mathbb{R}_{+},\ y_{i}\in\{0,1\}&\forall i\in I\end{array}$$

Aggiungiamo vincoli:
Per ogni localizzazione i è prevista una dimensione massima $$U_{i}$$, e nel caso di apertura, una dimensione minima pari a $$L_{i}$. Non possono essere aperti più di K ipermercati.
$\begin{array}{lll}\max&\sum\limits_{i\in I}R_{i}x_{i}\\\text{s.t.}&&\\&\sum\limits_{i\in I}C_{i}x_{i}+F_{i}y_{i}\leq W&\text{(budget)}\\&x_{i}\leq U_{i}y_{i}\ \forall i\in I&\text{(dim massima/attivazione delle variabili binarie)}\\&x_{i}\geq L_{i}y_{i}\ \forall i\in I&\text{(dim minima ipermercato)}\\&\sum\limits_{i\in I}y_{i}\leq K&\text{(num massimo ipermercati)}\\&x_{i}\in\mathbb{R}_{+},\ y_{i}\in\{0,1\}&\forall i\in I\end{array}$
Da notare che senza la dimensione minima dell'ipermercato, c'è la possibilità che un ipermercato a dimensione nulla sia aperto.

---
Per risolvere i problemi di ricerca operativa, è utile isolare le informazioni non chiare e quelle chiare e iniziare la modellazione da queste ultime.

Un capitale di 100 000 deve essere investito.
A: privato, 2 rischio, 9 anni, 4.5%
B: pubblico, 3 rischio, 15 anni, 5.4%
C: stato, 1 rischio, 4 anni, 5.1%
D: stato, 4 rischio, 3 anni, 4.4%
E: privato, 5 rischio, 2 anni, 6.1%

I fondi pubblici e dello stato sono tassati del 30% e almeno il 40% del capitale deve essere riservato a questi. La durata media dell'investimento non deve superare i 5 anni.
Un investimento in C blocca l'investimento in D e viceversa. E' possibile investire in E solo se si 

$\max4.5x_{A}+0.7(5.4x_{B}+5.1x_{C}+4.4x_{D})+6.1x_{E}$
| s.t.                                 |                                                |
| :----------------------------------- | ---------------------------------------------- |
| $$x_A+x_B+x_C+x_D+x_E$$                | $$\leq100000$$                                   |
| $$x_B+x_C+x_D$$                        | $$\leq40000$$                                    |
| $$9x_A+15x_B+4x_C+3x_D+2x_E$$          | $$\leq5(x_A+x_B+x_C+x_D+x_E)$$                   |
| $$2x_A+3x_B+1x_C+4x_D+5x_E$$           | $\leq1.5(x_A+x_B+x_C+x_D+x_E)$$                 |
| $$y_C+y_D\leq1$$<br>(vincolo C nand D) | $$x_C\leq My_C$$<br>$$x_D\leq My_D$$ (attivazione) |
| $$x_A\geq10000y_E$$                    | $$x_E\leq My_E$$ (attivazione)                   |
| $$x_i\in\mathbb{R}_+,\ y_i\in\{0,1\}$$ | $$\forall i\in I$                               |

---
Ditta dispone di 20 operai esperti e deve pianificare le assunzioni per i prossimi 5 mesi. Ogni operaio esperto lavora 150 ore di lavoro e percepisce 1000 euro al mese. Un neoassunto, durante il suo primo mese, percepisce 500 euro, non fornisce lavoro utile e gli viene affiancato un operaio esperto. Ogni operaio esperto 

$$\min500(x_{1}+x_{2}+x_{3}+x_{4}+x_{5})+1000(y_{1}+y_{2}+y_{3}+y_{4}+y_{5})$$

| s.t.                   |                      |                                 |
| ---------------------- | -------------------- | ------------------------------- |
| $$y_i\in\mathbb{Z}_+$$   | $$x_i\in\mathbb{Z}_+$$ | $$\forall i\in\{1,2,3,4,5\}$$     |
| $$y_1=20$$               | $$x_1\leq y_1$$        | $$150(y_1-x_1)+70x_1\geq2000$$    |
| $$y_2=y_1+x_1$$          | $$x_2\leq y_2$$        | $$150(y_1-x_1)+70x_1\geq4000$$    |
| $$y_3=y_2+x_2$$          | $$x_3\leq y_3$$        | $$150(y_1-x_1)+70x_1\geq7000$$    |
| $$y_4=y_3+x_3$$          | $$x_4\leq y_4$$        | $$150(y_1-x_1)+70x_1\geq3000$$    |
| $$y_5=y_4+x_4$$          | $$x_5\leq y_5$$        | $$150(y_1-x_1)+70x_1\geq3500$$    |
| $$x_1+x_2\geq10\cdot z$$ | $$z\in\{0,1\}$$        | z: se è dipendente continuato   |
| $$w_3+w_4+w_5\leq1$$     | $$x_i\leq Mw_i$$       | w: se assumo in $$i\in\{3,4,5\}$$ |

---

| max  | $$120x_V+150x_S$$                                            |                            |
| ---- | ---------------------------------------------------------- | -------------------------- |
| s.t. | $$y_{A1}+y_{A2}+y_{A3}\leq5000$$                             |                            |
|      | $$y_{B1}+y_{B2}+y_{A3}\leq6000$$                             |                            |
|      | $$x_V=w_{V1}+w_{V2}+w_{V3}$$                                 |                            |
|      | $$x_S=w_{S1}+w_{S2}+w_{S3}$$                                 |                            |
|      | $$4y_{B1}=3y_{A1}$$<br>$$2w_{S1}=3w_{V1}$$<br>$$2w_{V1}=y_{A1}$$ | (Bilanciamento impianto 1) |
|      | $$3y_{B2}=4y_{A2}$$<br>$$2w_{S2}=w_{V2}$$<br>$$3y_{V2}=4y_{A2}$$ | (Bilanciamento impianto 2) |
|      | $$y_{B3}=y_{A3}$$<br>$$w_{S3}=w_{V3}$$<br>$$3w_{V3}=2y_{A3}$$    | (Bilanciamento impianto 3) |
|      | $$z_1+z_2+z_3\geq1$$                                         | (Vincolo logico)           |
|      | $$x_{V1}+x_{S1}\leq1000+M(1-z_1)$$                           |                            |
|      | $$x_{V2}+x_{S2}\leq1000+M(1-z_2)$$                           |                            |
|      | $$x_{V3}+x_{S3}\leq1000+M(1-z_3)$$                           |                            |

### Problema di Programmazione Lineare
Consideriamo problemi PL con variabili continue.

Un problema di PL può avere soluzione:
- inamissibile
- illimitato
- ottimo ammesso

Combinazione convessa
Si dice stretta quando non vengono considerati gli estremi.

![](img/Pasted%20image%2020251105094231.png)

$$\begin{array}{llllll}3x_{1}&+4x_{2}&+s_{1}&&&=24\\ x_{1}&+4x_{2}&&+s_{2}&&=20\\3x_{1}&+2x_{2}&&&+s_{3}&=18\end{array}$$
Si trovano i vertici ponendo alcune variabili a 0. In questo caso poniamo s1 e s2 a 0.

$$c^{T}$$, vettore c trasposto

>**Forma standard dei problemi PL**$$\begin{array}{lll}\min&c_{1}x_{1}+c_{2}x_{2}+...+c_{n}x_{n}\\s.t.&a_{i1}x_{1}+a_{i2}x_{2}+...+a_{in}x_{n}=b_{i}&(i=1,...,m)\\&x_{i}\in\mathbb{R}_{+}&(i=1,...,n)\end{array}$$dove 
	x è un vettore di n variabili reali di soluzioni ammissibili
	c è un vettore di n termini noti; sono costanti della funzione obiettivo
	b è un vettore di m termini noti; sono limiti dei vincoli
	a è una matrice mxn di termini noti; sono costanti dei vincoli

**Soluzioni di base**
Sistema $$Ax=b,\ A\in\mathbb{R}^{m\times n},\ p(A)=m,\ m<n$$
*Base di A*: sottomatrice quadrata di rango massimo, $$B\in\mathbb{R}^{m\times n}$$
F matrice delle variabili di slack
$$A=[B|F]\quad B\in\mathbb{R}^{m\times n},\ \det(B)\neq0$$
$$x=\left[{x_{B}\atop x_{F}}\right]\quad x_{B}\in\mathbb{R}^{m},\ x_{F}\in\mathbb{R}^{n-m}$$

$$Ax=b\quad\Rightarrow [B|F]\left[{x_{B}\atop x_{F}}\right]=Bx_{B}+Fx_{F}=b$$
$$\displaystyle x=\left[{x_{B}\atop x_{F}}\right]=\left[{B^{-1}b\atop 0}\right]$$

Usiamo il metodo di Gauss
Soluzioni di base sono vertici del problema di programmazione lineare.

$$z=c^{T}x=\underbrace{c_{B}^{T}B^{-1}b}_{z_{B}}+\underbrace{(c_{F}^{T}-c_{B}^{T}B^{-1}F)x_{F}}_{c_{F}^{T}}$$

Calcolare uno ad uno le soluzioni per trovare quella ottima può risultare un algoritmo molto pesante, usiamo il metodo del simplesso.

#### Metodo del simplesso
Troviamo una soluzione di base ammissibile
Da quella troviamo un'altra base ammissibile e migliorante modificando le variabili fuoribase da focalizzare e ponendo le altre a 0

Il problema si dice in *forma canonica* rispetto alla base B di A se in corrispondenza delle variabili base ho la matrice identità sormontati da 0 nella funzione obiettivo.

Esecuzione:
1. PL in forma standard $$\min\{c^{T}x:Ax=b,x\geq0\}$$ e una base ammissibile di partenza
	ripeti
2. mettere in forma canonica rispetto a B
   $$z=\bar{z}_{B}+\sum\limits_{j=1}^{n-m}\bar{c}_{F_{j}}x_{F_{j}}$$
   $x_{B_{i}}=\bar{b}_{i}-\sum\limits_{j=1}^{n-m}-\bar{a}_{iF_{j}}x_{F_{j}}\quad(i=1...m)$
3. *Condizione sufficiente di ottimalità*
   Quando tutti i costi ridotti delle variabili fuori base sono $$c_{B_{i}}\geq0$$ allora la soluzione è ottima.
4. *Condizione sufficiente di illimitatezza*
   Quando c'è un costo ridotto $$c_{B_{i}}<0$$ e ha tutti gli altri parametri della stessa colonna è 0. L'algoritmo termina.

c = costo ridotto
$$\bar{z}$$ = coefficiente di z

$$R_{0}$$ è la funzione obiettivo con z come valore obiettivo
$$TS=\left[\begin{array}{cc|c|c|c}&x_{B_{1}}...x_{B_{m}}&x_{F_{1}}...x_{F_{n-m}}&z &\bar{b}\\\hline(R_{0})&c_{B}^{T}&c_{F}^{T}&-1&0\\\hline(R_{1})&&&0\\\vdots&B&F&\vdots&b\\(R_{m})&&&0\end{array}\right]$$
Prima di procedere:
1. è in forma canonica? Diagonalizzare rispetto a B.
2. è una base ammissibile? $$\bar{b}\geq0$$
3. è una funzione ottima?
4. è illimitato?
5. $\min\{\underset{(x_{B_{1}})}{\dfrac{\bar{b}_{1}}{\bar{a}_{1h}}},...,\underset{(x_{B_{m}})}{\dfrac{\bar{b}_{m}}{\bar{a}_{mh}}}\}$ che scegliamo per cambio di base

Per fare cambio di base si devono fare operazioni di pivot dalla colonna.
Base non deve essere assolutamente nella nella posizione dello schema sopra, basta essere definita.

Vincolo è saturo quando $$s_{1}=0$$ e lasco quando $$\geq0$$.

0. Individuare base ammissibile da var slack in questo caso $$B=[x_{4}\ x_{5}\ x_{6}]$$
	Iter 1) $$B=[x_{4}\ x_{5}\ x_{6}]$$
		$$\begin{array}{cccccc|c|c}x_{1}&x_{2}&x_{3}&x_{4}&x_{5}&x_{6}&-z&\bar{b}\\\hline-3&-1&-3&0&0&0&-1&0\\\hline2&1&1 &1&0&0&0&2\\1 & 2 & 3 & 0 & 1 & 0 & 0 & 5 \\2 & 2 & 1 & 0 & 0 & 1 & 0 & 6 \end{array}$$
		(1) FC? Sì
		(2) Ammissibile? Sì
		(3) Ottima? Non so
		(4) Illimitata? Non so
		(5) entra x1 ed esce $$\min\{\frac{2}{2},\frac{5}{1},\frac{6}{2}\}=x_{4}$$
	Iter 2) $$B=[x_{1}\ x_{5}\ x_{6}]$$
		$$\begin{array}{cccccc|c|c\quad c}x_{1}&x_{2}&x_{3}&x_{4}&x_{5}&x_{6}&-z&\bar{b}\\\hline0&1/2&-3/2&3/2&0&0&-1&0&R'_{0}=R_{0}+3R'_{1}\\\hline1&1/2&1/2&1/2&0&0&0&1&R'_{1}=R_{1}/2\\0&3/2&5/2&-1/2&1&0&0&4&R'_{2}=R_{2}-R'_{1}\\0&1&0&-1&0&1&0&4&R'_{3}=R_{3}-R'_{1}\end{array}$$
		(1) FC? Sì
		(2) Ammissibile? Sì
		(3) Ottima? Non so
		(4) Illimitata? Non so
		(5) entra x3 ed esce $$\min\{\frac{1}{\frac{1}{2}},\frac{4}{\frac{5}{2}},\frac{4}{0}\}=x_{5}$$
	Iter 3) $$B=[x_{1}\ x_{3}\ x_{6}]$$
		$$\begin{array}{cccccc|c|c\quad c}x_{1}&x_{2}&x_{3}&x_{4}&x_{5}&x_{6}&-z&\bar{b}\\\hline0&7/5&0&6/5&3/5&0&-1&6/5&R'_{0}=R_{0}+\frac{3}{2}R'_{2}\\\hline1&1/5&0&3/5&0&0&0&4/5&R'_{1}=R_{1}-\frac{1}{2}R'_{2}\\0&3/5&1&-1/5&2/5&0&0&8/5&R'_{2}=\frac{2}{5}R_{2}\\0&1&0&-1&0&1&0&4&\end{array}$$
		(1) FC? Sì
		(2) Ammissibile? Sì
		(3) Ottima? Sì, non ci sono costi ridotti negativi

*Base degenere*: ci sono più di una $\min\{\frac{\bar{b}_{1}}{\bar{a}_{1h}},...,\frac{\bar{b}_{m}}{\bar{a}_{mh}}\}$.
Scegliamo albitrariamente quale fare uscire.
E' possibile che con basi diverse si hanno le stesse soluzioni.

Costi ridotti negativi, mettere in forma canonica. Attenzione a non avere mai b<0 (non ammissibile).

>**Regola anticiclo di Bland**
>1. Fissare un ordine tra le variabili (indice).
>2. Tra le variabili candidate al cambio di base, *scegliere sempre la prima* (con indice minimo).
>Applicando Bland, il simplesso visita una base al più una volta.

Perché sappiamo di ottenere soluzione degenere? Perché la soluzione del quoziente minimo $$\theta=0$$.

Teorema: se esiste una soluzione ottima, allora esiste una base ottima con costi ridotti tutti non negativi.
Corollario: le regole anticiclo garantiscono di raggiungerla.

Utilizzando la regola di Bland, il metodo del simplesso converge sempre al più $$({n\atop m})$$ iterazioni.

Come trovare una base ammissibile? Usare il metodo della ricerca di ottimo.

Programmazione lineare
Cambiamo punto di vista: definiamo un valore per la funzione obiettivo w
>Se z* esiste finito allora esiste anche w*.

w*=max w che soddisfa tutti i vincoli sul valore obiettivo. I vincoli sono infiniti.
$\begin{array}{lcll}w^{*}=&\max&w\\ &\text{s.t.}&w\leq c^{T}x&\forall x\in P\\ &&x\in\mathbb{R}\end{array}$$

PL2
Condizioni necessarie e sufficienti:
$$\begin{cases}w\leq c^{T}x,\ \forall x\in P\\ P\neq\emptyset\wedge z^{*}>-\infty\end{cases}\quad\Longrightarrow\quad\boxed{\exists u\in\mathbb{R}^{m}\begin{cases}u^{T}A\leq c^{T}\\ w\leq u^{T}b\end{cases}}$$

| $$PL_{1}$$                                                                         | $$PL_{2}$$                                                                                                 |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| $$\begin{array}{lcl}z^{*}=&\min&c^{T}x\\ &\text{s.t.}&Ax=b\\ &&x\geq0\end{array}$$ | $$\begin{array}{lcl}w^{*}=&\max&u^{T}b\\ &\text{s.t.}&u^{T}A\leq c^{T}\\ &&u\in\mathbb{R}^{m}\end{array}$$ |

La funzione funzione obiettivo del duale è $$u^{T}b=u_{1}b_{1}+...+u_{m}b_{m}$$


-Sufficienza, definire $$u^{T}A\sim c^{T}$$ e u
$$c^{T}x\underbrace{\geq}_{x\geq0,\text{ serve }u^{T}A\leq c^{T}}u^{T}Ax\underbrace{\geq}_{Ax}u^{T}b\geq w_{i},\ \forall x\in P$$

Affinché $$u^{T}Ax\leq c^{T}x$$ è sufficiente che a $$$u^{T}A_{j}x_{j}\leq c_{j}x_{j},\ \forall j=1...n$$ si consideri una variabile primale alla volta:
- se $$x_{j}\geq0$$, la condizione sufficiente è che $$u^{T}A_{j}\leq c_{j}$$
- se $$x_{j}\leq0$$, la condizione sufficiente è che $$u^{T}A_{j}\geq c_{j}$$
- se $$x_{j}$$ è libera, la condizione sufficiente è che $$u^{T}A_{j}=c_{j}$$

Affinché $$u^{T}Ax\geq u^{T}b$$ è sufficiente che a $$u_{i}a_{i}^{T}x\geq u_{i}b_{i},\ \forall j=1...m$$ si consideri una vincolo primale alla volta e:
- se $$a_{i}^{T}x\geq b_{i}$$, la condizione sufficiente è che $$u_{i}\geq0$$
- se $$a_{i}^{T}x\leq b_{i}$$, la condizione sufficiente è che $$u_{i}\leq0$$
- se $$a_{i}^{T}x=b_{i}$$ la condizione $$u_{i}a_{i}^{T}x\geq u_{i}b_{i}$$ è soddisfatta se $$u_{i}\in\mathbb{R}$$

| Primale ($$\min c^{T}x$$) | Duale ($$\max u^{T}b$$)  |
| ----------------------- | ---------------------- |
| $$a_{i}^{T}x\geq b_{i}$$  | $$u_{i}\geq0$$           |
| $$a_{i}^{T}x\leq b_{i}$$  | $$u_{i}\leq0$$           |
| $$a_{i}^{T}x= b_{i}$$     | $$u_{i}$$ libera         |
| $$x_{j}\geq0$$            | $$u^{T}A_{j}\leq c_{j}$$ |
| $$x_{j}\leq0$$            | $$u^{T}A_{j}\geq c_{j}$$ |
| $$x_{j}$$ libera          | $$u^{T}A_{j}=c_{j}$$     |

esempio:
$\begin{array}{lllll}\min&10x_{1}&+20x_{2}\\\text{s.t.}&2x_1&-x_{2}&&\geq1\\&&x_{2}&x_{3}&\leq2\\&x_1&&-2x_3&=3\\&&3x_{2}&-x_{3}&\geq4\\&x_{1}&&&\geq0\\&&x_2&&\text{libera}\\&&&x_{3}&\leq0\end{array}\Longrightarrow\begin{array}{llllll}\max&1u_{1}&+2u_{2}&+3u_{3}&+4u_{4}\\\text{s.t.}&u_{1}&&&&\geq0\\&&u_{2}&&&\text{libera}\\&&&u_{3}&&\leq0\\&&&&u_{4}&\geq0\\&2u_{1}&&+u_{3}&&\leq10\\&-u_{1}&+u_{2}&&+3u_{4}&\leq20\\&&u_{2}&-2u_{3}&-u_{4}&=0\end{array}$

> Teorema: trasformazione duale doppia
> Il duale del duale è la primale.

>Teorema della *dualità forte*
>Data coppia (PL) e (DL)
>(PL) ammette ottimo finito $$\Longleftrightarrow$$ (DL) ammette ottimo finito e i valori delle funzioni obiettivo coincidono.

> Teorema della *dualità debole*
> Siano P e D poliedri delle regioni ammissibili dei problemi primale e duale rispettivamente, 
> per ogni coppia di soluzioni ammissibili per il primale e duale $$x\in p,\ u\in D$$, vale la relazione $$u^{T}b\leq c^{T}x$$
> 
> Corollario
> Sia $$\bar{x}$$ soluzione ammissibile per (PL) e $$\bar{u}$$ per (DL), $$c^{T}\bar{x}=\bar{u}^{T}b\quad\Longleftrightarrow\quad{\bar{x}\text{ è soluzione ottima (PL),}\atop\bar{u}\text{ è soluzione ottima (DL)}}$$ inoltre
> 1. (PL) è illimitato $$\Longrightarrow$$ (DL) è inammissibile
> 2. (DL) è illimitato $$\Longrightarrow$$ (DL) è inammissibile

|      |              |                | (DL)            |                 |
| ---- | ------------ | -------------- | --------------- | --------------- |
|      |              | Finito         | Illimitato      | Inamissibile    |
|      | Finito       | SI e (z\*=w\*) | NO              | NO              |
| (DL) | Illimitato   | NO             | NO              | SI (corollario) |
|      | Inamissibile | NO             | SI (corollario) | SI (\*)         |

Teorema di complementarietà
$$x,u\text{ ottime}\Longleftrightarrow\left.{u_{i}(a_{i}^{T}x-b_{i})=0,\ \forall i=1 ...m\atop(c^{T}-u^{T}A)x=0,\ \forall j=1 ...n}\right\}\text{ (ortogonalità)}$$
x e u sono ottime se e solo se
1. variabile primale positiva $$x_{j}>0\quad\Rightarrow\quad u^{T}A_{j}=c_{j}$$ variabile duale saturo
2. vincolo duale lasco $$u^{T}A_{j}$$
3. variabile duale positiva
4. vincolo primale lasco

### Problemi dei cammini minimi
Un problema sui grafi per trovare il Shortest Possible Path (SPP).
Variabili decisionali: $$x_{ij}=\begin{cases}1&\text{l'arco (i,j) è sul cammino minimo}\\0&\text{altrimenti}\end{cases}$$
$$\begin{align}\min&\sum\limits_{(i,j)\in A}c_{ij}x_{ij}\\s.t.&\underbrace{\sum\limits_{(i,v)\in A}x_{iv}\sum\limits_{(v,j)\in A}x_{vj}}_{\text{vincoli del bil. del flusso}}=\begin{cases}-1&\\+1&\\0&v\in N\backslash\{s,d\}\end{cases}\\&x_{ij}\in\{0,1\}\quad\forall(i,j)\in A\end{align}$$ 
Gestire cicli di lunghezza negativa perché il problema sarebbe mal posto: non esiste un cammino minimo.

Matrice dei grafi
Matrice di adiacenza, righe nodi e colonne nodi
Matrice di incidenza, righe nodi e colonne archi
-1 dove esce +1 dove entra

>Sia E la matrice corrispondente ai vincoli di bilanciamento di flusso e D una qualsiasi sottomatrice quadrata (di qualsiasi dimensione). Allora $$\det(D)\in\{-1,0,+1\}$$: E è *Totalmente Uni-modulare*.

Sia B sottomatrice quadrata di E (meno una riga...). Si ha:
- $$(B^{-1})_{i,j}=(-1)^{i+j}\frac{\det()}{\det()}$$
- 
Le soluzioni sono intere.
Possiamo quindi considerare il vincolo $$x_{ij}\in\{0,1\}\equiv\mathbb{R}_{+}$$.

Costruiamo il duale al problema SPP
$$\begin{align}\max\quad&\pi_{d}-\pi_{s}\\s.t.\quad&\pi_{j}-\pi_{i}&\forall(i,j)\in A\\&\pi_{v}\in\mathbb{R}&\forall v\in N\end{align}$$ 
**Algoritmo Label Correcting generico per SPP**
>$$pi_s:=0$$; set p(s)=^
>for each $$v\in N-s$$ {set $$\pi_{v}:=+\infty$$, set p(v)=^}
>while ($$\exists(i,j)\in A:\pi_{j}>\pi_{i}+c_{ij}$$) do {
>	set $$\pi_{j}:=\pi_{i}+c_{ij}$$ // ipotesi di soluzione duale
>	set p(j) := i //ipotesi di cammino (sol. primale)
>}

Lemma
Alla fine di ogni iterazione, se $$\pi_{j}<+\infty$$ allora
- esiste cammino P da s a j
- p(j) è il predecessore di j su P
- costo di P è $$\pi_{j}$$
Al termine dell'algoritmo, se esiste un cammino da s a j, allora $$\pi_{j}<+\infty$$.

In presenza di un ciclo di lunghezza negativa, l'algoritmo non converge.

Senza cicli di lunghezza negativa, l'algoritmo converge in $$O((|N|-1)(\overline{M}-\underline{M})|A|)$$.
- N-1 etichette da $$+\infty$$ a costo minimo
- $$+\infty:$$ usiamo upper bound $$\overline{M}=(|N|-1)\cdot\max\{0,\underset{(i,j)\in A}{\max}x_{ij}\}$$
- $$\underline{M}:$$ lower bound per il costo minimo $$=(|N|-1)\cdot\min\{0,\underset{(i,j)\in A}{\min}x_{ij}\}$$
- $$|A|:$$ costo di ogni iterazione

Complessità *non è polinomiale* dato il fattore $$(\overline{M}-\underline{M})$$ che dipende dai valori del problema.

> L'algoritmo LCG calcola l'albero dei cammini minimi da s verso tutti i nodi.

E' possibile trovare tutti i cammini minimi costruendo il grafo dei cammini minimo:
$$G_{s,\pi}=(N,A_{s\pi})\quad\text{dove}\quad A_{s,\pi}=\{(i,j)\in A:\pi_{j}=\pi_{i}+c_{ij}\}$$

**Algoritmo di Bellman-Ford**
> $$pi_s:=0$$; set p(s)=^
>for each $$v\in N-s$$ {set $$\pi_{v}:=+\infty$$, set p(v)=^}
>for h=i to |N| {
>	set flag_aggiornato := falso; set $$\pi':=\pi$$;
>	for all ($$(i,j)\in A:\pi_{j}>\pi'_{i}+c_{ij}$$) do {
>		set $$\pi_{j}:=\pi'_{i}+c_{ij}$$;
>		set p(j) := i;
>		set flag_aggiornato := true;
>	}
>	if (not flag_aggiornato) then { STOP: $$\pi$$ è ottima}
>} 
>STOP: $$\exists$$ ciclo di costo negativo

- senza cicli negativi: 
  le iterazioni sono terminate al più all'iterazione h=|N|-1 e a h=|N| semplicemente nessuna etichetta è cambiata (flag_aggiornato=false)
- con cicli negativi: 
  all'iterazione h=N continuano a migliorarsi le etichette (flag_aggiornato=true), usciamo quindi dal ciclo e viene segnalato
Questo algoritmo finisce sempre e ha una complessità di $$O(|N|A)$$.

Implementazione mediamente più efficiente, tenendo conto dei flag nodi aggiornati

Costruire il cammino minimo seguendo i flag all'indietro.

Generalizzazione del cammino minimo con più inizi e fini
Variabile decisionale $$x_{ij}\in\mathbb{Z}_+$$
$\begin{align}\min&\sum\limits_{(i,j)\in A}c_{ij}x_{ij}\\s.t.&\sum\limits_{(i,v)\in A}x_{iv}\sum\limits_{(v,j)\in A}x_{vj}=\begin{cases}\leq q&\\\geq q&\\0&v\in N\backslash\{s,d\}\end{cases}\\&\underbrace{x_{ij}\leq a_{ij}}_{\text{vincoli di capacità}}\\&x_{ij}\in\{0,1\}\quad\forall(i,j)\in A\end{align}$
Problema del flusso di costo minimo
Vincoli di capacità

problema di flusso massimo

**L'algoritmo di Dijkstra (label setting)**
> 0. $$\pi_{s}:=0$$; set p(s):=^; set $$S:=\emptyset$$; set $$\bar{S}:=N$$;
>    for each $$v\in N\backslash\{s\}\{\text{set }\pi_{v}:=+\infty,$$ set p(v):=^}
> 1. set $$\hat{v}:=\arg\underset{i\in S}{\min}\{\pi_{i}\}$$
>    set $$S:=S\cup\{\hat{v}\};\text{set }\bar{S}:=\bar{S}\backslash\{\hat{v}\}$$
>    if $$\bar{S}=\emptyset$$ then STOP: $$\pi$$ è ottimo
> 2. for all ($$j\in\Gamma_{\hat{v}}\cap\bar{S}:\pi_{j}>\pi_{\hat{v}}+c_{\hat{v}j}$$) do {
>     set $$\pi_{j}:=\pi_{\hat{v}}+c_{\hat{v}j}$$
>     set $$p(j):=\hat{v}$$
>    } go to 1.

Applicabile solo se *tutti i costi sono >= 0*.

Lemma
Alla fine dell'iterazione: ogni nodo
- $$i\in S: \pi_{i}$$ è costo di un cammino minimo da s a i, p(i) è il predecessore di i su tale cammino
- $$i\in\bar{S}:\pi_{i}$$ è costo cammino da s a i tale che sia costo minimo sotto vincolo di usare solo nodi in S, p(i) è il predecessore di i su tale cammino

Le operazioni che aggiungono complessità sono la ricerca del minimo (O(n)) e le iterazioni con i nodi (O(n)). Notiamo però che i nodi, dopo che sono selezionati, i loro successori non vengono più considerati: il costo ammortizzato di iterazione è (O(log n)).
La complessità è $$O(|A|\log N)$$ con heap binario.

### Branch and Bound: problema di programmazione lineare intera
$$\begin{array}{rcll}z_{I}=&\max\backslash\min &c^{T}x\\&\text{s.t.}&Ax=b\\&&x_{i}\in\mathbb{Z}_{+}^{n}&i\in I\end{array}$$
**Rilassamento continuo**
$\begin{array}{rcl}z_{L}=&\max\backslash\min &c^{T}x\\&\text{s.t.}&Ax=b\\&&x\geq0\end{array}$$
Nei problemi di massimo $$z_{L}\geq z_{I}$$ è *Upper Bound* (sempre arrotondato in eccesso)
Nei problemi di minimo $$z_{L}\leq z_{I}$ è *Lower Bound*.

**Branching**
Usiamo il metodo divide-et-impera per trovare l'ottimo di ogni porzione della soluzione ammissibile. Il migliore tra queste è la soluzione ottima del problema.

Costruiamo due sotto-problemi (branch) con una soluzione del rilassamento continuo in arrotondamento a difetto e eccesso.

**Metodo del Branch-and-Bound (B&B)**
> *Inizializzazione:* Risolvi rilassamento per $$x_{0}^{R}$$ e stima ottimistica $$B_{0}$$ e poni $$L=\{(P_{0},B_{0})\},\bar{x}=\emptyset,\bar{z}=+\infty(\min)[-\infty(\max)]$$
> `repeat`:
> 	*Criterio di stop:* Se $$L=\emptyset$$, allora `stop`: $$\bar{x}$$ è la soluzione ottima
> 	*Selezione nodo:* Seleziona ed estrai $$(P_{i},B_{i})\in L$$ per effettuare branch
> 	*Branching:* Dividi $$P_{i}\text{ in }P_{|L|+1}(x_{ik})\leq\lfloor x_{ik}^{R}\rfloor\text{ e }P_{|L|+2}(x_{ik}\geq\lceil\hat{x}_{ik}^{R}\rceil)$$
> 	`for each` sotto-problema $P_{j},\ j=|L|+1...|L|+2$$:
> 		*Bounding:* Risolvi il rilassamento di $$P_{j}$$ ottenendo la stima ottimistica $$B_{j}$$ e soluzione $$x_{j}^{R}$ o inammissibilità
> 		*Fathoming:* 
> 			`if` $P_{j}$ non è inammissibile: `continue`
> 			`else if` $B_{j}$$ non è migliore di $$\hat{z}$: `continue`
> 			`else if` $x_{j}^{R}$ è intera:
> 				`if` $x_{j}^{R}$$ è migliore di $$\bar{z}$$:
> 					aggiorna
> 					elimina da L tutti i nodi k con $$L_{k}$$ non migliore di $$\bar{z}$
> 				`continue`
> 		*Ricorsione:* `else` aggiungi $(P_{j},B_{j})$ a L

Possiamo usare il criterio del Best Bound First sui nodi attivi.

Non trovare un incumbent subito porta all'algoritmo ad avere una complessità alta.

Ragioniamo: se tutti i coefficienti delle variabili nella funzione obiettivo sono interi e c'è un vincolo di interezza, allora la soluzione obiettivo è intera. Possiamo rendere i bound interi.

Nei problemi di massimo \[SA:UB] upper-bound diventa più piccolo da padre a figlio mentre, nei problemi di minimo\[LB:SA] il lower-bound diventa più grande da padre a figlio.

**Scelte progettuali**
Branch: scelta di branch (es. più frazionaria, più intera, etc.), ovvero costruire sotto-problemi sempre più semplici; almeno convergere (soluzione)
$$E_{i}:\cup_{i}E_{i}=E$$ (must!)

Fathoming:
- \[N.M.] Nessuna soluzione migliorante
- \[S.A.] Valutazione ottimistica
- \[N.A.] Sotto-problema non ammissibile

Strategie di esplorazione: Depth First, Best Bound First, mista, diving etc.

Valutazione di soluzioni ammissibili: euristiche e rounding sulla soluzione frazionaria (a condizione di interezza)

Arresto standard ($$\bar{x}$$ ottima), anticipato (max time, $$\bar{x}$$ possibilmente non ottima) o *optimality gap* entro soglia (bound vicino all'ottimo, variabili intere)

Valore ottimo del min \[LB : UB]
LB >= del parente
UB <= LB di tutte le altre foglie
LB = UB

B&B vengono anche chiamati path-finding o alpha-beta pruning

Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform