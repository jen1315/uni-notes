1) $f(n)=O(g(n))$ sse $g(n)=\Omega(f(n))$
	(=>) assumendo $f(n)=O(g(n))$
	ovvero $\exists n_{0},\exists c>0\qquad0\leq f(n)\leq cg(n)$
	e vorremo far vedere che esistono $n_{1},c^{'}$ tali che $0\leq c^{'}f(n)\leq g(n)$
2) se $f(n)=O(g(n))$ e $g(n)=O(h(n))$ implica che $f(n)=O(h(n))$
	quindi per $n\geq n_{0}^{n}=\max\{n_{0},n_{0}^{'}\}$
	$0\leq f(n)\leq cg(n)\leq c\cdot c^{'}h(n)$

Esercizi Master Theorem
1) $T(n)=\underbrace{2}_{a=2}T(\underbrace{\frac{n}{2}}_{b=2})\underbrace{\log n}_{f(n)}$
   $\begin{align*}f(n)&=\log n\\&=O(n^{\log_{2}2})=O(n)\end{align*}$
   unica possibilità del MT (caso 1)
   per applicarlo deve esistere $\varepsilon>0$ tale che
   $f(n)=\log n=O(n^{(\log_{b}a)-\varepsilon})=O(n^{(\log_{2}2)-1})$
xcasa
1. Implementare InsertionSort in modo ricorsivo (mai iterazione)
2. Valuta duplicati in un array `(i,j) e i<j t.c. A[i]=A[j]`
	boolean DupCheck(A)
	int DupCount(A)
	 array elemDup(A)
	 array idDup(A)
3. Dato `A[1,…,n]` e key(valore), verificare se esistono i,j tale che `A[i]+A[j]=key`
Esercizi MergeSort
1) Evita la copia dell’ input nel Merge e usa A e B alternativamente come sorgente/destinazione.
```
MergeSort(A)
	n = A.lenght
	B[1,...,n] = A[1,...,n]
	MergeSortRec(A,B,1,n)

MergeSortRec(A,B,p,r)
	if (p < r)
        q = (p+r/2)
	    MergeSortRec(A,B,p,q)
	    MergeSortRec(A,B,q+1,r)
		Merge(A,B,p,q,r)

Merge(A,B,p,q,r)
	n1 = q-p+1
	n2 = r-q
	i=j=1
	for k=p to r
		if (B[i]<=B[j])
			A[k] = B[i]
			i = i+1
		else
			A[k] = B[j]
			j = j+1
```
1) Versione iterativo divide fino a un k ordinato in InsertionSort (Timsort)
2) In loco

Esercizi alberi binari di ricerca
- funzione booleana IsABR(T) che verifica se T è una ABR.
$(h=0)$ vuoto `x=nil`, triviale
$(h>0)$ T ha la forma
`InOrder(x)` $\underbrace{x_{1}...x_{k}}_{\text{InOrder(x.left)}}\leq x\leq\underbrace{x_{1}...x_{k}}_{\text{InOrder(x.right)}}$
```
IsABR(T)
	if(T.root!=nil)
		InOrder
```

- Dato albero binario T, dimostra che InOrder(T.root) elenca gli elementi di T in ordine crescente se e solo se T è ABR.
$(h=0)$ `x=nil` albero vuoto è ABR
$(h>0)$ allora T
$\overbrace{\underbrace{x_{1}...x_{k}}_{\text{InOrder(x.left)}}\leq x\leq\underbrace{x_{1}...x_{k}}_{\text{InOrder(x.right)}}}^{\text{ordinata}}$
T1 e T2 sono due alberi binari di ricerca

- dato A -> ABR in tempo lineare
No, con un array A qualsiasi, il limite inferiore degli algoritmi di ordinamento è $O(n\log n)$, impossibile farlo $O(n)$.
Con l'ipotesi di A ordinato invece, è possibile.

- max-heap: elencare i suoi elementi in ordine crescente in tempo lineare?
No, per lo stesso motivo precedente.

- BST senza campo parente p e reimplementare tutte le operazioni con costo O(h)
```
class BST {
	left
	right
	succ
	key
}

Succ(x) // O(1)
	return x.succ

Insert(T,z)
	x=T.root
	y=nil
	pred=nil
	while x!=nil
		y=x
		if z.key<x.key
			x=x.left
		else
			x=x.right
			pred=y
	if y==nil
		T.root=z
	else if z.key<y.key
		y.left=z
	else
		y.right=z
	if pred!=nil
		z.succ=pred.succ
		pred.succ=z
	else
		z.succ=y

Parent(T,z) // nel caso ci siano chiavi ripetute, l'unico modo di ritornare agli antenati è percorrere tutto il cammino sinistro fino ad arrivare al massimo che ha come successore l'antenato

Pred(x) // chiama Parent() h volte -> O(h^2)
Delete(T,z)
```

- **(Pairing)** È dato un mazzo di carte numerate che contiene una coppia di carte per ogni valore 1, ..., n. Le carte sono quindi divise in due sequenze (disordinate)  
$a_{1} a_{2}  .... a_{n}^{2}$
Voglio riavvicinare tutte le coppie. A tal fine posso spostare ogni carta inserendola in una posizione diversa nella stessa o nell'altra sequenza. Determinare la carta di valore massimo che devo necessariamente spostare.

"idea": è lineare verificare se è sufficiente spostare carte di valore $\leq$ v dato
idea1: ricerca binaria
```
// verifica se spostare carte di valore <=v è sufficiente a formare tutte le coppie
checkMax(A,n,v)
	pending=0 // prima carta non accoppiata di valore >v
	j=1
	ok=true
	while(j<=2n) and ok
		if A[i]>v
			if pending=A[j]
				pending=0
			else if pending=0
				pending=A[j]
			else
				ok=false
	return ok

find(A,n) // ricerca binaria del minimo v che è "ok"
	p=1
	r=n
	while p<r
		q=(p+r)/2
		if checkMax(A,n,q)
			r=q
		else
			p=q
	return p
```
idea2: soluzione tempo lineare

Es di programmazione dinamica
1) Algoritmo di Fibonacci con complessità $\Theta(\log n)$
```
FastFib(n)
	if n==0 or n==1
		return 1
	A = {1,1,1,0}
	for i=
```

Esercizi algoritmi greedy
1) ci sono attività
   $s=(1,5,2,3,7,10)\quad f=(3,7,9,10,11,18)$
   determiniamo l'output e l'algoritmo

2) scelta greedy alternativa per selezione di attività
   - scegli l'attività di densità inferiore
     NO, controesempio: un'attività breve può sovrapporsi su due attività lunghe
   - scegli l'attività che inizia prima
     NO, controesempio: l'attività che inizia prima è lunga la durata di multiple attività
   - scegli l'attività con il numero minore di sovrapposizioni
     NO, controesempio: 
   - scegli l'attività che inizia per ultima
     Sì, è il duale di GreedySel (dimostralo)
$\Longrightarrow$ la maggior parte degli algoritmi greedy non sono sempre corretti

3) Domanda: Indicare, in forma di albero binario, il codice prefisso ottenuto tramite l'algoritmo di Huffmann per l'alfabeto \{a,b,c,d,e\} supponendo che ogni carattere appare con le seguenti frequenze

| a   | b   | c   | d   | e   |
| --- | --- | --- | --- | --- |
| 12  | 10  | 13  | 17  | 8   |
	Spiegare il processo di soluzione del codice.

4) Si consideri un file definito sull'alfabeto \{a,b,c\} con frequenze $f(a),f(b),f(c)$. Per ognuna delle seguenti codifiche determinare, se esiste, un opportuno assegnamento di valori alle 3 frequenze per cui l'algoritmo di Huffmann restituisce tale codifica, oppure argomentare che tale codifica non è mai fattibile
1. $e(a)=0\quad e(b)=10\quad e(c)=11$
2. $e(a)=1\quad e(b)=0\quad e(c)=11$
   e(a) e e(c) non sono prefix code
3. $e(a)=10\quad e(b)=01\quad e(c)=00$

5) Matching sulla linea
   Sia $S=\{s_{1},s_{2},...,s_{n}\}$ un insieme di punti ordinati sulla retta reale rappresentanti dei server. Sia $C=\{c_{1},c_{2},...,c_{n}\}$ un insieme di punti ordinati sulla retta reale , rappresentanti dei client. Il costo di assegnare un client $c_{i}$ ad un server $s_{j}$ è $|c_{i}-s_{j}|$. F ornire un algoritmo greedy che abbina ("match") ogni client ad un server distinto e che minimizzi il costo totale (equiv, medio) dell'assegnamento.
-> Abbiniamo ogni server ad ogni client in ordine.

Correttezza?
<u>Proprietà della scelta greedy</u>: esiste un matching ottimo che contiene la scelta greedy $c_{1}\rightarrow s_{1}$
Dimostrazione: sia $M^{*}$ una soluzione ottima.
se $(c_{1}\rightarrow s_{1})\in M^{*}$, ho finito
altrimenti vari casi, tra cui
caso $c_{1}\leq s_{1}\leq c_{i}\leq s_{j}$,
$(c_{1}\rightarrow s_{j},c_{i}\rightarrow s_{1})$ ha costo $(s_{j}-c_{1})+(c_{i}-s_{1})$
$(c_{1}\rightarrow s_{1},c_{i}\rightarrow s_{j})$ ha costo $(s_{1}-c_{1})+(s_{j}-c_{i})$

$\begin{array}{ccc}(s_{j}-c_{1})+(c_{i}-s_{1})=&s_{j}-c_{1}+&(c_{i}-s_{1})\geq0\\&\shortparallel&\shortparallel\\(s_{1}-c_{1})+(s_{j}-c_{i})=&s_{j}-c_{1}+&(c_{i}-s_{1})\geq0\end{array}$

<u>Proprietà della sottostruttura ottima</u>: sia $M^{*}$ un matching ottimo che contiene la scelta greedy $c_{1}\rightarrow s_{1}$. Allora gli assegnamenti di $c_{1},c_{2},...,c_{n}$ a $s_{1},s_{2},...,s_{n}$ sono un matching ottimo $M'$ per il sottoproblema $C\setminus\{c_{1}\},\ S\setminus\{s_{1}\}$.
Dimostrazione: 

1) Sia $X=\{x_{1},x_{2},...,x_{n}\}$ un insieme di punti ordinati sulla retta reale. Fornire un algoritmo greedy che determini un insieme I di cardinalità minima di intervalli chiusi di ampiezza unitaria $([a,b]\in I\Rightarrow b-a=1)$ tale che $\forall x_{i}\in X\quad\exists j\in I\text{ tale che }x_{i}\in j$.

Correttezza?
<u>Proprietà della scelta greedy</u>: esiste un insieme ottimo di intervalli di copertura per X che contiene la forma greedy $[x_{1},x_{1}+1]$
Dimostrazione: col cut&paste, sia $I^{*}$ una soluzione ottima, sia $[a,a+1]\in I^{*}$ un intervallo che copre x1 (deve esistere)
$a\leq x_{1}\leq a+1$
se $a=x_1$, ho finito
se $a<x_{1}$, tutti i punti coperti da $[a,a+1]$ sono anche coperti da $[x_{1},x_{1}+1]\Longrightarrow I'=I^{*}\setminus\{[a,a+1]\}\cup\{[x_{1}+x_{1}+1]\}$
è soluzione ammissibile.
Inoltre $|T'|=|T^{*}|\Rightarrow I'$ è soluzione ottima.

<u>Proprietà di sottostruttura ottima</u>: sia $I^{*}$ una soluzione ottima che contiene la scelta greedy. Allora $I^{*}\setminus\{[x_{1},x_{1}+1]\}$ è soluzione ottima del sottoproblema $X\setminus\{x_{j}\in X:x_{j}\leq x_{1}+1\}$
Dimostrazione: $I^{*}\setminus\{[x_{1},x_{1}+1]\}$ è soluzione ammissibile per il sottoproblema. Suppongo per assurdo che non sia ottima: allora esiste una soluzione con meno intervalli, ci aggiungo la scelta greedy, ottenendo così una soluzione per il problema originale X che ha meno intervalli; assurdo.

Esercizi appelli passati
Equazioni di ricorrenza: 
$T(n)=\begin{cases}4T(\frac{n}{2})+n^{3}+1\end{cases}$ 

Max-heap: 
Data la sequenza di elementi \[7,1,17,0,5,17\] li inseriamo in un max-heap vuoto e poi togliamo \[0\]. Spiega cosa avviene

L'insert avviene con l'aggiunga del numero nella prima foglia disponibile e poi una max-heapify-up.
Inserisco 7 a un max-heap vuoto e prende la posizione della prima foglia utile che, in questo caso, è la radice.
La 1 che finisce sotto a 7 nel suo lato sinistro. 17 è inizialmente inserito al suo lato destro ma, dopo l'invocazione della max-heapify, scambia posizione con il 7. 0 finisce sotto a 1 nel suo lato sinistro e il 5 al suo lato destro prima di scambiare posizione con 1 dopo il max-heapify. 
L'array max-heap è \[18,7,17,5,1\]

Alberi binari:
Aggiungiamo agli BST un metodo che ritorni il loro grado di bilanciamento calcolato con $\frac{h_{x}}{\log_{2}(n_{x}+1)}$
```
x { key
	p     //parente
	l; r  //figlio destro e sinistro
	h     //altezza del sottoalbero
	size }

Bal(x)
	if(x==null) return 0
	return (x.h)/log2(x.size+1)
```
Definiamo il suo metodo di inserimento.
```
Insert(T,z)
	x = T.root
	y = null
	while(x!=null)
		y = x
		x.size++
		if(z.key<x.key)
			x = x.l
		else
			x = x.r
	z.size = 1
	z.h = 1
	z.r = z.l = null
	z.p = y
	if(y!=null)
		if(z.key<y.key)
			y.l = z
		else
			y.r = z
		x = z
		while(y!=null and y.h<x.h+1)
			y.h = x.h+1
			x = y
			y = y.p
```

BST completi memorizzati in un'array. Scrivere una funzione Max(T, n) che ritorna il valore massimo nell'albero.
```
Max(T,n)
	return T[n]
```

Scrivere una funzione Merge(T1,T2,k) tale per cui $\forall n\in T_{1}:n<k\quad\forall m\in T_{2}:m>k\qquad |T|=2n+1$
```
Merge(T1,T2,k)
	T.len(2n+1)
	T[1] = k
	t=1, t1=1, i=2
	while(i<2n+1)
		T[i+t] = T1[t1:t]  //splice()
		i+=t
		T[i+t] = T2[t1:t]
		t1+=t
		i+=t
		t*=2
	return T
```
