---
share: true
---

Algoritmo: Insieme ordinato e finito di istruzioni elementari e non ambigue, per risolvere un problema.

Problema > Sequenza istruzioni > Soluzione
C’è chi crea istruzioni e chi lo esegue

Top-down, problema in sottoproblemi (funzione)

Formalizzare problema > Ideare algoritmo > Comunicare algoritmo > Controllo errori

### Linguaggio di programmazione
Linguaggio di basso livello:
- funzioni atomiche
- dipende dall’architettura
 
Linguaggio di alto livello:
ha compilatore/interprete che traduce il linguaggio in quello macchina
Equilibrio tra:
- bassa complessità del traduttore
- lingua potente (molte librerie)

Usiamo C, progettato da Ken Thompson e Dennis Ritchie nel 1970
- efficienza come obiettivo principale
- vicino ai linguaggi di basso livello
Standard ANSI C

Controllo errori: test, prove di correttezza
Molti algoritmi possibili per uno stesso problema, si valutano per
- Correttezza (più IMPORTANTE)
- Efficienza in tempo e spazio (memoria)
- Organizzazione, codice riusabile
- Stile, leggibile
### Compilazione
Il calcolatore sa solo compilatore in linguaggio macchina

Traduzione può essere
- Interprete: traduce in alto livello e esegue immediatamente
- Compilatore: traduce tutte le istruzioni in linguaggio macchina che può essere eseguito
- Ci sono linguaggi che fanno intermedio (java)
``` C
#include <stdio.h>
int main() {
	/* Stampa sullo schermo la scritta Hello world! */
	printf("Hello world!\n");
}
```

La traduzione avviene nelle seguenti fasi
1. Preprocessore, elabora il codice
	- Rimuove commento
	- `#include <pacchetto>
	- `#define name Y` macro è sostituita con valore
	- Compilazione condizionale
2. Compilatore
	- Traduce in linguaggio macchina
	- Genera errore quando non ci riesce
	- Genera file tradotto
1. Linker
	- Fornisce riferimenti alle funzioni invocate

**Pseudocodice**
Usato per comunicare la bozza di una soluzione a un’altra persona
Inizializziamo sempre le variabili.
Un pseudocodice può essere richiamato da un’altro.

Definire la PRE e POST condizione. Design by Contract
``` C
/*
	PRE Descrizione dati input
	POST: Descrizione return
*/
```
```
// trova il minore tra 3 numeri
leggi x, y, z
se (x < y) {
	se (x < z)
		ritorna x
} altrimenti se (y < z) {
	ritorna y
} 
ritorna z
```
```
// dire se il punto p è dentro il rettangolo sd
leggi sx, sy, dx, dy, px, py
se (px < dx e px > sx)
	se (py < dy e py > sy)
		scrivi (px, py) interno al rettangolo
altrimenti
	scrivi (px,py) esterno al rettangolo
```
```
sum = 0
leggi n
ripeti finché (n > 0) {
	sum = sum + n
	n = n - 1
}
scrivi sum
```
`sizeof([var]) \\byte della variabile` 
C non ha un controllo overflow.

`printf(”%.2f”, 3.1475); \\3.15 arrotondamento eccesso a 2 cifre`

``` c
#include <stdio.h>
int fahr_deg(int f) {
	return (5.0/9.0)*(f-32);
}
int main() {
	int d = fahr_deg(x);
	printf("%d gradi %d", d)
}
```

``` 
int in_giorni = 750;
int anni = 0, mesi = 0, giorni = 0;

anni = in_giorni/365;
giorni = in_giorni%365;
mesi = giorni/7;
giorni = giorni%7;
```

```c
// condizione in una riga
condizione? valore_se_vero; valore_se_falso;
```
```c
int P_whi(int n) {
	int p0=0, p1=1, p=2;
	
	while (n<2) {
		
		p=2*
	}
}
// sequenza Pell con ricorsione
int P_ric(int n) {
	if(n<2)
		return n;
	return 2*P(n-1)+P(n-2);
}
```

### Correzione del programma
Capire il problema, ovvero valutare lo stato della macchina, ovvero i valori delle variabili in un dato istante (PRE e POST locale)
1. `PRE => [while(B) a] POST` ciclo
	cercare proprietà invarianti nei cicli, ovvero le componenti sempre vere (anche quando si esce dal ciclo)
	- INV & B => \[a\] INV
	- INV & $\neg$B => POST
3. `PRE => [if(B) P else Q] POST` condizione
	- PRE & B => \[P\] POST
	- PRE & $\neg$B => \[Q\] POST


## C Ansi
Compila sul terminale
`> gcc [-c] [-o output_file] nome_file.c`
Debugger sul terminale
`> gdb nome_file.c`

In C, l’indentazione non conta.
``` C
if()
	if()
		/* SINGOLA LINEA CODICE */
else // questa else si riferisce all’if interna
	/* CODICE */
```

**Variabili locali** sono visibili solo dentro il blocco in cui sono dichiarate.
**Variabili globali** sono dichiarate fuori da tutte le funzioni.

Con una variabile dichiarata esternamente se, una nuova con lo stesso nome viene dichiarata dentro un blocco, non è più possibile accedere alla variabile dichiarata inizialmente finché non si esce dal blocco.
``` c
int x=2 // x_ext
{
	int x=3; // x_int, x_ent non è piú visibile
}// x_ent è visibile nuovamente
```
Avviene, per esempio, nelle ricorsioni.

Funzioni senza return è definita con void.
In C, le funzioni non possono restituire più di un valore.
In C, non si definiscono funzioni dentro delle altre.

Le funzioni sono visibili solo a quelle successive (dopo la sua dichiarazione).

**Parametro formale**, definizione del parametro nelle tonde della funzione.
**Parametro attuale**, valore passato alla funzione alla sua invocazione.

Un singolo carattere usa ‘’.
Con la conversione da float a int, avviene il troncamento. `(tipo) x`

#### Puntatori 
Esistenti solo in C.
Hanno come r-valore l’indirizzo di memoria.
`tipo *nome` definizione
Per sicurezza, deve sempre essere inizializzato. Mettiamolo a `= NULL` quando non abbiamo un indirizzo da assegnare.

`&x` restituisce l-valore(indirizzo) di x
`*p` restituisce il valore(tutto, non solo r-valore) all’indirizzo p

& e * hanno precedenza minore di () e \[\], ma maggiore degli operatori aritmetici; sono associativi da destra a sinistra.
Mettere uno spazio tra * operazione puntatore e * operazione aritmetico per la corretta esecuzione.

`tipo **p` definisce un puntatore a un puntatore
`**p` restituisce il valore puntato `p` dal valore puntato `*p`

`scanf(“%tipo”, &x)` lettura da tastiera

Fare attenzione ai puntatori a variabili deallocate.
Si possono compiere
- somma di un intero al puntatore
- sottrazione di due puntatori
- confronti tra puntatori

Passaggio per riferimento, modifica variabili definite fuori dalla funzione a cui viene passata.
``` c
#define BASE 10
void function(int param) { param = BASE; }
void functionPunt(int *param) { *param = BASE; }

int main() {
int x = 2;
function(x); // x = 2
function(&x); // x = 10 
}
```
#### Array
```
tipo c[n];
c[i] = *(p + i*sizeof(tipo))
```

La stringa è un array di caratteri che terminano con `\0`
`char string1[]= “ciao mondo”` (in questo caso è messo in automatico)

Array passato come parametro viene modificato dalla funzione.

`tipo *p[n] \\ array di n puntatori`
Usato per array di elementi di dimensione diversa.

**Array di due dimensioni**
``` c
int ar[2][3] = { {1,2,3},{4,5,6} } = {1,2,3,4,5,6}
printf("%d\n", *(*(ar+1)+2)); // =ar[1][2]=6
```
#### Ricorsione
Trova la relazione tra il problema e il problema leggermente più semplice. Determina il caso base.

``` C
void stampa_decre_cre(int n) {
	if(n > 0) {
		printf("%d\n", n); // stampa decrescente
		stampa_decre_cre(n-1);
		printf("%d\n", n); // stampa crescente
	}
}
```
Tenere conto che la stampa prima o dopo la chiamata da risultati differenti.

``` c
#include <stdlib.h>
int seed;
srand(seed);
int r = rand(); 
```
#### Puntatore a funzione
``` c
void selectionSortGeneral(int *X, int size, int(*seleziona_elem)(int*A, int size)) {
	int elem;
	for(int i=0; i<size; i++) {
		elem = (*seleziona_elem)(X+i, size);
		scambia(elem)
	}
}

int main() {
	int size, int A[size];
	selectionSortGeneral((int *)A, size, min());
}
```
Utile per passare le funzioni come parametri di funzioni generiche.

**Considerazioni**
`i++` esegue e poi incrementa, non usarlo fuori da cicli

#### Parametro passato da terminale
`int main(int argc, char *args[])`
Per leggere i parametri, inizia da args\[1\] perché a indice 0 c’è il nome del programma.
`scanf()`

#### Switch case e break
``` c
switch (var) {
	case ‘0’:
		// codice
		break; // quando var è catturato dal caso, tutto il codice in poi, viene eseguito. Usare break per uscire dalla switch
	case ‘1’:
		// codice
		break;
	default:
		// codice
}
```
Break è usabile anche in altri casi, ma per didattica, non lo usiamo in questo corso.
#### Progetti con file multipli
Si devono creare 2 file
- `.h` con le intestazioni (prototipi) delle funzioni
- `.c` per l’implementazione delle funzioni (includi il prototipo)
```
#include <stdio.h> // funzione di libreria
#include "header.h" // funzione nel progetto
```
Per evitare di includere un file header più volte, si implementa una direttiva pre-processore.
```
#ifndef HEADER_FILE // continua se non è definito
#include HEADER_FILE
#endif
```

Invece di dover scrivere ogni volta
`> gcc -o hello file1.c file2.c file3.c`
per testare un progetto multi-programma.

Esiste un programma che permette di salvare il comando di compilazione
`> make hello`
`> make test`
`> make clean`

``` makefile
CC = gcc
CFLAGS = -g

all: hello

hello:
	$(CC) -o hello file1.c file2.c file3.c
test:
	$(CC) $(CFLAGS) -o hello file1.c file2.c file3.c
clean:
	rm hello test
```
Permette anche di
- compilare versioni diverse del programma
- cancellare eseguibili
- esegui test
- Installare software

Programmazione strutturata: limiti sui salti, iterazione invece di ricorsione

##### Particolarità C
Variabili Statiche la sua inizializzazione viene eseguita una sola volta e salva il valore a lui associato.

Heap per gestione dinamica della memoria
``` C
int *p=(int *)malloc(sizeof(int)*20)
free(p); // dealloca p
```
Concettualmente è analogo a `int p[20]` ma il compilatore non riesce a conoscere l’estensione della variabile e fare le stesse operazioni che farebbe con la seconda definizione

#### Numeri casuali
Non esiste un vero random in programmazione. Si una funzione di generazione “casuale” dipendente da seed

#### Funzione passato come parametro
$\begin{array}{rcl}\text{Umano}&-&\text{Problema}\\\backslash& &/ \\&\text{Macchina}\end{array}$

Nella programmazione classica:
$$Programma(Dato)\rightarrow Dato$$
Nella programmazione di ordine superiore questa distinzione viene eliminata. $$Programma\cong Dato$$La macchina di Turing introduce Universalità ovvero la capacità del calcolatore di simulare nuove istruzioni grazie a queste salvate come dati.

``` C
int minimo(int *X, int size);
int massimo(int *X, int size);
void selectionSortGeneral(int *X, int size, int (*selezione_elem)(int *A, int size));

int main() {
	int n = 10;
	int A[n] = {10,9,8,7,6,5,4,3,2,1};
	selectionSortGeneral(A[], n, minimo());
}
```

Standard input, flusso input (tastiera, mouse etc)
Standard output, flusso output (a schermo, in file)
Standard error, flusso errore

Classificazione file
- accesso sequenziale
- accesso diretto
- file di testo, caratteri organizzare in righe
- file binario

``` c
FILE *fp;
fp = fopen("file.txt", "r");
if(f_in==NULL) {
	fprintf(stderr, "Il file non può essere aperto.\n");
	return EXIT_FAILURE;
}else {
	…
	fclose(f_in);
}
```

Queste operazioni avvengono al buffer di output che viene salvato su file a chiusura.

Con i file binari, se si è a conoscenza della lunghezza di record, si può accedere casualmente (a un record specifico).
``` c
struct record r;
fread(r, <dim_record>, <num_record>, fp);
fwrite(r, sizeof(struct record), 2, fp);
```
Ci possono essere problemi di portabilità causati dalla differenza di memorizzazione. 
`fseek(fp, <offset>, <origine>)` spostare il puntatore

Allocazione memoria
- statica (avviene all’avvio programma)
- automatica (avviene a run-time)
- dinamica (allocata specificamente dal programmatore)

##### Lista concatenata
- successione di elementi
- relazione di ordine tra gli elementi

Operazioni Specifiche
- inserimento e cancellazione
- visita / ricerca
- inizializzazione

``` c
struct nodo {
	int dato;
	struct nodo *next;
}; typedef struct nodo Node;

void init();
void insertTop(Node **list, int val);
void insertLast(Node **list, int val);
Node removeTop(Node **list);
Node removeTop(Node **list);
void printList(Node *list);

int main() {
	Node *LinkedList = init();
	
	malloc(sizeof(Node));
}
```

**Pila (stack)**, LIFO
**Coda (queue)**, FIFO

##### Albero
Nodo iniziale dalla quale si collegano figli che a sua volta ha figli così ricorsivamente.

**Albero binario di ricerca**: il massimo dei figli è 2 ed è ordinato in modo tale che a sinistra ha valori minori e destra maggiori.

Definire se l’albero segue
- visita _simmetrica_, inizia dal nodo sinistro, poi parente e nodo destro
- visita anticipata, inizia dalla radice e poi visita il sotto-albero sinistro e poi quello destro
- visita posticipata/in profondità, dalle foglie senza figli da sinistra poi in salita fino alla radice
``` c
struct bleaf {
	int dato;
	struct nodo *left;
	struct nodo *right;
}; typedef struct bleaf bTree;

```
Cancellazione di un nodo parente
- figlio destro prende il suo posto
- occorre riordinare il sotto albero suo figlio