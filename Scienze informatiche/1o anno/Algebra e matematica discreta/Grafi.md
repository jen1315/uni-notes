(Mat discreta)
Lezione 19/03
Königsberg

Un grafo (non orientato) denotato con $G(V,E)$ consiste di
- un insieme finito $V=\{v_1,…,v_n\}$ di vertici
- un insieme finito $E=\{e_1,…,e_n\}$ di archi (o lati)
dove ogni arco è identificato con le coppie (non ordinate) di due vertici opportuno.

(non vedremo archi che ritornano a un vertice e vertici a cui passano più di un arco)


Due vertici $v_1$ e $v_2$ sono detti adiacenti se esiste un lato di cui $v_1$ e $v_2$ sono gli estremi.

Esempio. Un grafo può essere rappresentato in molti modi


Osservazione Ci sono varie terminologie in uso per grafi non orientati

| $\mathrm{I}$ terminologia | $\mathrm{II}$ terminologia | Esempio            |
| ------------------------- | -------------------------- | ------------------ |
| Grafo                     | Multigrafo                 | ![[Graph.png]]     |
| Grafo semplice            | Grafo                      | ![[SimpGraph.png]] |
Definizione
Dato un grafo $G(V,E)$, il grafo di un vertice $v\in V$ è il numero di lati incidenti in $v$.

Dato $G(V,E)$ grafo, possiamo scrivere la tabella (o matrice) di adiacenza del grafo.

Esempio:

|       | $e_1$ | $e_2$ | $e_3$ | $e_4$ | $e_5$ | $d(-)$ |
| ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| $v_1$ | 1     | 1     |       |       |       | 2      |
| $v_2$ |       | 1     |       | 1     | 1     | 3      |
| $v_3$ |       |       | 1     | 1     |       | 2      |
| $v_4$ | 1     |       | 1     |       | 1     | 3      |
Osserviamo che$$\sum_{v\in V}d(v)=2+3+2+3=10=2|E|$$
<u>TEOREMA</u> Per ogni grafo $G(V,E)$ si ha$$\sum_{v\in V}d(v)=2|E|$$<u>COROLLARIO</u> (Lemma della stretta di mano)
Il numero di vertici di grado dispari è pari.

Definizione
Sia $k\in\mathbb{N}$, un grafo $G(V,E)$ è detto $k$-regolare se ogni vertice del grafo ha grado $k$.

Osservazione Per $k_n=k_n(V,E)$
- $d(v)=n-1$
- $\displaystyle|E|=\frac{n(n-1)}{2}\qquad2|E|=\sum_{v\in V}d(v)=n(n-1)$

Definizione
Sia $G(V,E)$ un grafo, il grafo $G(V’,E’)$ è detto **sottografo** di $G(V,E)$ se $V’\subseteq V$ e $E’\subseteq E$

Un sottografo $G(V’,E’)$ di $G(V,E)$ è detto **sottografo indotto** se gli elementi di $E’$ sono gli elementi di $E$ che possiedono gli estremi in $V’$.

Sia $G(V,E)$ un grafo. Un **percorso** è una sequenza di vertici, $v_1,v_2,…,v_k$ (non necessariamente distinti) e una sequenza finita di archi $e_1,…e_{k-1}$ in cui ogni arco $e_i$ ha per estremi i vertici $v_i\text{ e }v_{i+1}\quad\forall1\leq i\leq k-1$.
I vertici $v_1\text{ e }v_k$ sono detti estremi del percorso.
In altre parole un percorso è una sequenza del tipo $v_1\ e_1\ v_2\ …\ v_{k-1}\ e_{k-1}\ v_k$

- La **lunghezza** di un percorso è il numero di archi che attraversa.
- Un percorso si dice **chiuso** se ha gli estremi coincidenti.

- Un **cammino** è un percorso con tutti i vertici distinti.
	Un ciclo o circuito è un percorso con tutti i vertici distinti e gli estremi coincidenti. Ciclo = “cammino chiuso”

	Dato un percorso non chiuso, contiene un cammino

<u>TEOREMA</u> Un percorso chiuso di lunghezza dispari, contiene un ciclo di lunghezza dispari.

In un grafo, due vertici $u\text{ e }v$ si dicono connessi se esiste un cammino che li abbia come estremi.

Definizione
>Dato un grafo $G(V,E)$, la sua sequenza di gradi è la successione dei gradi di tutti i suoi vertici scritti in modo decrescente.

Es. ![[SeqGrad.png]]
La sua sequenza di gradi è 4 2 2 1 1

Un grafo si dice **bipartito** se l’insieme $V=V_1\cup V_2,\ V_1\cap V_2=\emptyset$, e se ogni suo arco (i suoi vertici è unione disgiunta dei suoi vertici)

Un grafo $G(V,E)$ bipartito, dove $V=V_1\cup V_2,\ V_1\cap V_2=\emptyset$ con $|V_1|=n_1,\ |V_2|=n_2$, è detto completo se ogni vertice di $V_1$ è adiacente ad ogni vertice di $V_2$. Si indica $k_{n_1,n_2}$.

**NB.** Grafo bipartito completo $\centernot\Longrightarrow$ completo
Inoltre, posto $k_{n_1,n_2}=G(V,E)$, allora $|E|=n_1n_2$

Es. 

<u>TEOREMA</u> Un grafo è bipartito se e solo se NON contiene cicli di lunghezza dispari.

NB. 
- Percorsi chiusi di lunghezza dispari non sono bipartiti.
- Un ciclo è bipartito se e solo se è pari.

>Sia $G(V,E)$ un grafo. Il grafo complementare di $G(V,E)$ è il grafo $\overline{G}=(V,\overline{E})$, dove $\overline{E}$ è l’insieme di archi, con estremi in $V$ che non ci sono in $G(V,E)$.

NB. Dato $G(V,E)$ con $|V|=n$, allora $G(V,E)\cup\overline{G}(V,\overline{E})=k_n$

#### Isomorfismi di grafi
(Isomorfismo, elementi con le stesse proprietà algebriche)
Abbiamo visto che lo stesso grafo può ammettere diverse rappresentazioni grafiche


Vediamo che la funzione$$V:\{1,2,3,4,5\}\xrightarrow{f}\{a,b,c,d,e\}$$è biiettiva e rispetta le adiacenze: per ogni $i,j\in\{1,2,3,4,5\}$ allora $i,j$ sono adiacenti $\Longleftrightarrow\underbrace{f(i)f(j)}_{\in\{a,b,c,d,e\}}$ sono adiacenti.

> Due grafi $G(V,E)$ e $G’(V’,E’)$ sono isomorfi se esiste una biiezione $f(V\rightarrow V’)$ che preserva le adiacenze, cioè$$\boxed{\forall u,v\in V,\quad uv\in E\Longleftrightarrow f(u)f(v)\in E’}$$$f:V\rightarrow V’$ è detta isomorfismo (di grafi) e si scrive $G(V,E)\simeq G’(V,E’)$

Vogliamo Capire, dati due grafi $G(V,E),G’(V’E’)$, se sono isomorfi. Abbiamo delle condizioni necessarie di isomorfismo
- $|V|=|V’|$
- $|E|=|E’|$
- $G(V,E)\text{ e }G’(V’,E’)$ hanno la stessa sequenza di gradi
- $G(V,E)\text{ e }G’(V’,E’)$ hanno gli stessi (=isomorfi) grafi indotti
In particolare se $G(V,E)\simeq G’(V’,E’)$, allora $G$ è bipartito $\Longrightarrow G’$ è bipartito.

<u>TEOREMA</u> I grafi $G$ e $G’$ sono isomorfi $\Longleftrightarrow\overline{G}\text{ e }\overline{G’}$ sono isomorfi.

Es 1-5 foglio 4

Dire se esiste un grafo con questa sequenza di gradi
5, 5, 4, 4, 3, 3, 2, 1
No, avrei un numero dispari di vertici di numero dispari.

Dire se esiste un grafo $G(V,E)$ tali che $d(v)\neq d(w)\quad\forall v\neq w$.
Sia $|V|=n$. Poiché il grado ogni vertice ha cardinalità diverse
$n-1\quad n-2\quad…\quad1\quad0$
tuttavia è impossibile perché il primo $n-1$ include l’ultimo $0$.

Siano grafi $G(V,E)\text{ e }\overline{G}(V,\overline{E})$ complementari. Avendo

Sia $G$ tale che $G\simeq\overline{G}$.
1. Dire quanti archi h $G$
2. Trovare grafo $G$ con 4 vertici tale che $G\simeq\overline{G}$
3. Dire se esiste grafo con 6 vertici $\simeq$ al suo complementare

Siano $G,G’$ due grafi con sequenza di gradi 2, 2, 1, 1
Dire se $G$ e $G’$ sono isomorfi. In caso affermativo, dire quanti isomorfismi $G\simeq G’$ ci sono.

#### Connettività degli archi
Dato un grafo $G(V,E)$ e due vertici $u,v\in V$ connessi, quanti vertici e archi dobbiamo “” per rimuovere

> Sia $G(V,E)$ un grafo (o multigrafo) e sia $S\subseteq V$. Si chiama **taglio associato ad $S$** il sottoinsieme $\delta(S)\subseteq E$$$\boxed{\delta(S)=\{u,v\in E:|S\cap\{u,v\}|=1\}}\atop\text{archi che hanno un solo estremo in S}$$inoltre si dice che $S\subseteq V(\text{o }\delta(S))$ separa i due vertici $u,v$ se solamente uno tra $u,v$ appartiene a $S$.

**NB.** $\delta(S)=\delta(V\setminus S)$

Connettività tra archi
> Sia $G(V,E)$ un (multi-)grafo e siano $u,v\in V$. Si chiama **arco-connettività tra $v$ e $u$**$$k_{u,v}^E(G)=\min\{|\delta(S)|:\delta(S)\text{ taglio che separa u e v}\}$$(= cardinalità minima del taglio che separa $u$ e $v$)

<u>TEOREMA</u> Sia $G(V,E)$ un grafo (o multigrafo),
1. $k_{u,v}^E(G)$ è il minimo numero di archi da togliere per disconnettere $u$ da $v$
2. $k_{u,v}^E(G)$ è il numero di cammini da $u$ e $v$ che non hanno archi in comune. Cioè: è il numero di cammini disgiunti sugli archi.

Grafo non co
Dato un sottoinsieme di vertici $G\setminus S$, il grafo ottenuto da $G$ che ha per vertici l’insieme $V\setminus S$ e per archi di $G$ di cui nessuno appartiene a $S$

Il grafo appena ottenuto è disconnesso. 

> Sia $G(V,E)$ un grafo (connesso, non completo)e $u,v\in V$ vertici non adiacenti$$k_{u,v}(G)=\text{minima cardinalità di un separatore S tale che u e v appartengono a componenti distinte in }G\setminus S$$

<u>TEOREMA</u> Per ogni grafo $G(V,E),|V|\leq2$$$\boxed{k(G)\leq k^E(G)\leq d^{m,n}(G)}$$
#### Foresta di grafi
> Una **foresta** è un grafo senza cicli (grafo aciclico). Un **albero** è una foresta connessa.

<u>PROPRIETÀ</u> Sia $T(V,E)$ un albero con almeno due vertici $(|V|\leq2)$
1. ci almeno due vertici di grado 1
2. $|E|=|V|-1$
##### Algoritmo di Kunskal
**Problema:** Albero di peso minimo
Dato un grafo $G(V,E)$ connesso, con $|V|=n$, ad ogni arco si associa un peso (costo, distanza…) si vuole un albero $T(V,E’)$ di peso minimo (somma di pesi o minimale) con $E’\leq E$.

**Primo step** Ordino gli archi $\{e_1,…,e_m\}$ in ordine crescente di peso $w(e_1)\leq w(e_2)\leq…\leq w(e_m)$
**Secondo step** Considero l’i-esimo arco
- se nell’albero che sto formando non abbia cicli,
- altrimenti lo scarto
**Ultimo step** Ottengo albero con $n=|V|$ vertici ed $n-1$ archi.

#### Algoritmo di Dijkstra
> Un $G(V,E)$ un grafo connesso pesato positivamente 

> La distanza tra $u\text{ e }v\ (d(u,v))$ è la lunghezza minima di un cammino tra $u\text{ e }v$.

Siano $G(V,E)$ un grafo connesso pesato positivamente e $u\in V$ fissato.
Notazione: Per ogni $v\in V$
$\Delta(v)=\{x\in V|x$ è adiacente a $v\}$

$\begin{align*}d_i(e)&=\text{distanza tra u e v al passo i-esimo dell’algoritmo}\\&=\min\{d_{i-1}(v),d_{i-1}(x)+\ell()\}\end{align*}$

<u>TEOREMA</u> Le seguenti affermazioni sono equivalenti per un grafo $G(V,E)$
1. $G$ è un albero
2. $G$ è interconnesso
3. Per ogni $u\neq v$ in $V$, esiste un unico cammino di estremi $e\text{ e }v$
#### Grafo planare
Un grafo si dice **planare** se lo si può disegnare senza che gli archi si intersechino (rappresentazione planare)

**Minori di un grafo**
Introduciamo le seguenti 3 operazione sui grafi
1. Rimozione di un vertice isolato
2. Rimozione di un arco (cioè $G(V,E\setminus\{S\})$)
3. Contrazione di un arco
> Un **minore** del grafo $G$ è qualsiasi grafo ottenuto da $G$ con le operazioni precedenti.

**NB1.** Le operazioni non creano intersezioni sugli archi, pertanto, per ogni minore $G’$ di $G$$$\begin{align*}G\text{ planare}&\Longrightarrow G’\text{ planare}\\ G’\text{ non planare}&\Longrightarrow G\text{ non planare}\end{align*}$$
<u>TEOREMA (Kuratowski)</u> Un grafo $G$ è planare se e solo se non ha come minori i grafi $k_5\text{ e }k_{3,3}$.

> Un **circuito hamiltoniano** in un grafo è un circuito che passa per tutti i vertici per una sola volta del grafo (tranne gli estremi).

<u>Metodo degli archi e delle corde</u>
Individua il circuito hamiltoniano.
Colloca i vertici trovati in un grafo circolare.
Individua gli archi esclusi. Se il grafo è planare, è possibile disegnarli nel grafo circolare senza che si intersechino.

**NB2.** Il numero di facce dipende solo dal grafo e non dalla rappresentazione piana.

<u><b>Formula di Eulero</b></u>
Dato un grafo planare $G$, ogni sua rappresentazione (planari) divide il piano in **regioni** o **facce**.

<u>TEOREMA</u> Per ogni planare $G(V,E)$ con $\gamma$ regioni si ha$$\boxed{\gamma=|E|-|V|+1}$$
Sia $G$ planare e $T(V,E’)$ un albero generante che ha lo stesso numero di $V$ e $E’\leq E$. Tale albero ha una sola faccia
$1=|E’|-|V|+1$
poiché $|E’|=|V|-1$ riguardiamo $G$ come il grafo ottenuto da $T$ aggiungendo $E\setminus E’$. Allora
$\begin{align*}\gamma&=1+(|T|-|G|)\\&=(|E’|-|V|+1)+(|E|-|E’|)\\&=|E|-|V|+1\end{align*}$

<u>TEOREMA</u> In un grafico semplice connesso e planare con $|E|\geq2$ si ha$$\boxed{|E|\leq3|V|-1}$$<u>DIM.</u> Per ogni faccia $f$, sia $\ell_F$ la lunghezza del percorso chiuso che passa per gli archi che delimitano $f$. È $\ell_F\geq3$
$\sum\ell_F=2|E|-1$

#### Grafi hamiltoniani
> Un grafo è hamiltoniano se contiene un circuito hamiltoniano.

<u>Proposizione</u>
Il grafo bipartito completo $k_{rs}$ è hamiltoniano se solo se $r=s\geq2$.

**Condizioni necessarie** 
Sia $G(V,E)$ un grafo hamiltoniano e sia $\gamma$ un circuito hamiltoniano. Sia $H(V,E’)$ il grafo che ha per archi quelli che formano $\gamma$
1. in $G$ ho $D_H(v)=2$ per ogni $v\in V$, pertanto in $G$ ho $d(v)\geq2$ per ogni $v\in V$
2. $K(H)=2\Longrightarrow K(G)\geq2$
3. Per ogni $\emptyset\neq S\subseteq V$
	$|S|\geq$

<u>TEOREMA (di Dirac)</u> Sia $G(V,E)$ un grafo semplice con $|V|\geq2$ 

#### Grafo euleriano
> Il percorso in un grafo è detto **euleriano** se 
> - è chiuso 
> - attraversa tutti gli archi del grafo una sola volta.
> Un grafo è euleriano se possiede un percorso euleriano.

<u>TEOREMA (di Eulero)</u> Un grafo $G$ è euleriano se e solo se è connesso ed ha grado pari.

Proprietà Le seguenti sono equivalenti per un grafo $G(V,E)$
1. $G$ è un albero
2. $G$ è aciclico e $|E|=|V|-1$
3. $G$ è connesso e $|E|=|V|-1$

