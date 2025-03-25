Paradigmi
- *concorrenza*, asincrone con risorsa condivisa
- *parallelismo*, asincrone che si coordinano per risolvere uno stesso calcolo
- *in rete*, collaborazione con altri sistemi tramite comunicazione asincrona in rete
- *distribuito*, nodi indipendenti in una rete non affidabile che si coordinano per eseguire uni stesso lavoro. Devono condividere il consenso dello stato complessivo del sistema
- *reattività*, sistema distribuito costruito sulle basi della comunicazione asincrona con caratteristiche di

Alan Kay, inventore della programmazione ad oggetti.

Usiamo Java.
Ogni parte del codice fa parte di una classe (tipo). 
Per convenzione ogni classe è maiuscola. Ogni classe fa parte in un package gerarchici. l package di default è "".
Package sono definite come nome di dominio all'inverso. La compilazione di un insieme di sorgenti Java è un processo deterministico. 

Visibilità 
- Default, la classe è visibile a tutte le altre classi nello stesso package
- Public, la classe è visibile a qualsiasi altra classe caricata nella JVM
  un file sorgente 

Una classe può non essere unica in diversi ClassLoader.
Variabile statica esiste "una sola copia" legata alla classe. Assomigliano a variabili globali e vengono allocate e inizializzate al caricamento (tempo variabile, problema se mutabili).
static final in maiuscolo, altre variabili in minuscolo.
Un metodo stati è legato all'oggetto e non vede le sue variabili istanza. 

Tutte le eccezioni derivano dalla classe Throwable che si suddivide in Exception e Error. 
RuntimeException sono lanciate direttamente dalla JVM.

Classe interne
Static nested classes, sono classi nello stesso package
Inner classes, classi dentro altre

Inizializzatori, blocchi static
Ereditarietà singola, una sola superclasse
Tutte i metodi sono virtual. A una classe final non si possono derivare sottoclasse. Sealed permette la derivazione a specifiche classe. Queste classi possono riaprire l'ereditarietà con non-sealed.

Interfaccia dichiara le caratteristiche del Tipo senza implementarla. Tutti i suoi metodi sono publici.
Un'interfaccia può essere private o protected se è membro di una classe.
Può essere estesa solo da un'altra interfaccia.
Una classe può implementare multiple interfacce.

Dal Java 8, è possibile definire metodi privati e sono stati aggiunti metodi di default.
``` java
interface Top {
	default String name() { return "unnamed"; }
}
interface Left extends Top {
	default String name() { return getClass().getName(); }
}
interface Right extends Top {}

```
Viene così reintrodotto il diamond problem. Vengono bloccate al momento di compilazione.

Un'interfaccia il cui nome inizia con @ è un tipo particolare: l'annotazione. Questo viene usato per arricchire i metadati.

| Tipo                 | Uso                                                                           |
| -------------------- | ----------------------------------------------------------------------------- |
| @Deprecated          | metodo che verrà rimosso                                                      |
| @Override            | metodo che implementa un membro di superclasse o interfaccia                  |
| @SuppressWarnings    | istruisce al compilatore di sopprimere i warning del costrutto annotato       |
| @FunctionalInterface | indica al compilatore che l'interfaccia può essere usata in modo "funzionale" |

**Tipo generici**
Nella versione 5, vengono introdotti i Generics, ovvero *1-kind parametric types*.
Una classe generica dichiara uno o più parametri di tipo che verranno specificati successivamente.
``` java
interface MappableList<T> {
	void add(T element);
	T head();
	List<T> tail();
}
class StringList implements MappableList<String> {
	public void add(String element);
	public String head() { return ""; }
	public List<String> tail() {
		return Collectrion.emptyList();
	}
}
```
Le eccezioni non possono essere generiche.

E' possibile estendere i tipi anche senza averli specificati.
``` java
interface SortableList<T extends MappableList<T>> {}
```
E' possibile non esprimere vincoli sul tipo ma solo sul tipo parametrizzato.
``` java
class Test {
	static void printCollection(Collection<?> c) {
		for(Object o:c) {
			System.out.printIn(o);
		}
	}
	public static void main(String[] args) {
		Collection< > cs = new ArrayList<String>();
	}
}
```

Le informazioni sui generici viene cancellato al runtime. Al runtime è possibile violare i vincoli espressi al momento di compilazione.

**Valori primitivi**

| Universo  | Tipo Corto         | Tipo Lungo |
| --------- | ------------------ | ---------- |
| Interi    | `byte, short, int` | `long`     |
| Decimali  | `float`            | `double`   |
| Caratteri | `char`             |            |
| Booleani  | `boolean`          |            |

I valori primitivi sono in minuscolo Tutti i caratteri sono utf-16.
Non è possibile indicare una costante di tipo byte o short senza l'operatore di cast.

I valori primativi non sono oggetti. Esistono una loro contropparte oggetto con la maiuscola.
Gli array sono oggetti istanziati autonomamente dal compilatore quando viene incontrata la loro dichiarazione.
``` java
array = new int[10];
```

enum è una particolare categoria di classe che può contenere un solo determinato numero di elementi. Può implementare metodi e campi ed è utile per definire classi piccole che non estendiamo.

*records* sono un lontano parente dello struct in C. Sono disponibili dal Java 14.
``` java
record Name(String firstName, String lastName) {}
```
Il record è immutabile ed è final. Ottiene automaticamente
- membri privati con metodi di accesso pubblici (stesso nome dei membri)
- costruttore di default
- metodi di equals, hashCode, toString
E' strato introdotto per aggiungere a Java, una sintassi di decostruzione delle classi per arrivare a un Pattern Matching.

**Classi non testuali** 
``` java
interface Top {
	default String name() { return "unnamed"; }
}
Top inst = new Top() {
	@Override public String name() { return "anonymous"; }
};
```
Una *classe anonima* è una classe che non ha un nome e quindi non può essere indicato in altre parti del codice.

Una *classe nascosta* è usata dal compilatore per la generazione del codice, definendo tecniche che usano caratteristiche della JVM non documentate o private.
- non può essere individuata
- non può essere usata in nessuna definizione
- può estendere il control nest (più classi in un singolo file, così connessi) a cui appartiene
Le Lambda Expressions sono implementate con la classe nascoste.

Lynn Conway, *Generalized Dynamic Instruction Handling (OOOE)*
Non c'è nessuna garanzia che l'ordine delle istruzioni sia lo stesso di quello del codice. Il compilatore, lo JVM e pure il processore hanno la libertà di riorganizzare il codice in uno con la stessa sintassi funzionale.
var è usato quando il tipo della variabile è ovvio così ne assume una automaticamente dal valore da cui è inizializzato.

Gli oggetti String
- non hanno bisogno dell'operatore `new`
- possono essere su più righe
- sono immutabili, evitare concatenazioni in un ciclo

E' possibile istanziare direttamente un'interfaccia implementandola al momento della creazione
``` java
Comparator<> reverse = new Comparator<String>() {
	@Override
	public int compare(String o1, String o2) {
		return -o1.compareTo(o2);
	}
};
```

Operatore ternario `<cond> ? <val1> : <val2>`

`this` indica l'oggetto corrente
`super` indica la superclasse da cui si eredita

Lambda expression `(<lista param>) -> istruzione`
Attenzione: la lambda espression non rende Java un linguaggio funzionale. La lambda expression non ha tipo di ritorno e serve solo per abbreviare la sintassi.

Method Reference è usato per indicare un metodo di una classe o oggetto da usare come lambda. `Class::method`

Switch-case usato come
- *istruzione switch*: sceglie un blocco di istruzioni da eseguire
  `case :` interrompiamo il fall-through con `break`, non ha bisogno di default
  `case ->`  inserire una sola espressione o blocco, no fall-through
``` java
switch (seasonName) {
	case "Spring" -> {
		System.out.print("primavera!");
		numLetters = 5;
	}
	case "Summer", "Winter" -> numLetters = 6;
	case "Fall" -> numLetters = 4;
	default -> numLetters = -1
}
```
- *espressione switch*: sceglie un valore da restituire
  `case :` ritorniamo un valore con `yield`; fall-through possibile
  `case ->` seguito da un valore letterale, un'espressione o un blocco che ritorna yield, no fall-through
``` java
int numLetters = switch (seasonName) {
	case "Spring":
		System.out.print("primavera!");
	case "Summer", "Winter":
		yield 6;
	case "Fall":
		yield 4;
	default:
		yield -1;
};

int numLetters = switch (seasonName) {
	case "Spring" -> {
		System.out.print("primavera!");
		yield 5;
	}
	case "Summer", "Winter" -> 6;
	case "Fall" -> 4;
	default -> -1;
};
```

*Pattern matching*, costruzione di una condizione basandoci sulla struttura dell'oggetto

For può ciclare su un oggetto che implementa un Iterable o array. `for(String s:List.of("a","b","c"))`

`assert` consente di verificare le condizioni al momento di esecuzione del programma.
`syncronized` davanti a un blocco o metodo, cambia il suo comportamento rispetto alla concorrenza.

#### Libreria standard
Haskell Brooks Curry
- logica combinatoria
- isomorfismo Curry-Howard
- Currying, multiple funzioni che compongono una funzione
- linguaggi Haskell, Brooks, Curry

JDK (Java Development Kit)
JRE (Java Runtime Environment)

Un modulo è un'insieme di package e moduli e controlla il loro accesso all'esterno. Consentono di separare il JDK (per compilare) in parti più piccole e creare distribuzioni più leggere.

Per il corso basta java.base
java.io per input e output
La libreria standard è organizzata per gerarchia di capacità che promuove l'uso della composizione.

System è in java.lang che è sempre implicitamente implementato.

**Collection API**
L'interfaccia Collection ha i metodi più semplici che viene inclusa da interfacce più specifiche. Diversi metodi sono marcati come opzionali per cui viene lanciato UnsupportedOperationException.

`java.lang.Object::equals()` è diverso da == che confronta solo l'identità dell'oggetto. Tutti i oggetti sono riferimenti.
Hashcode viene usato per distinguere gli oggaetti

Iterator permette di percorrere una Collection e controllare se si è raggiunti la fine. Una classe Iterable fornisce un Iterator.

| Iterator           | Significato                       |
| ------------------ | --------------------------------- |
| `next`             | Prossimo elemento                 |
| `hasNext`          | Se ci sono altri elementi         |
| `remove`           | Rimuove l'elemento attuale        |
| `forEachRemaining` | Applica al resto della collezione |

| Iterable      | Significato                                                     |
| ------------- | --------------------------------------------------------------- |
| `forEach`     | Applica ad ogni elemento                                        |
| `iterator`    | Fornisce un iterator                                            |
| `spliterator` | Fornisce un spliterator, usato per percorrere in modo parallelo |

**Sequenced Collections**
L'interfaccia List rappresenta un elenco ordinato di elementi, indirizzati per posizione.

L'interfaccia Set definisce un insieme, ovvero un contenitori senza ripetizioni (equals da false) non ordinato.

L'interfaccia Dequeue rappresenta una coda a doppia entrata (Double Ended Queue). Può essere usata come coda FIFO o stack LIFO.

L'interfaccia Map definisce una mappa chiave-valore. I metodi equals e hashCode devono essere ben definite.
Può essere implementata come
- HashMap, chiavi distinte per hashCode
- TreeMap, chiavi ordinate
- HashTable, sincrona
- EnumMap, chiavi enum
- IdentityHashMap, basata sull'identità
Si può definire una mappa immutabile con Map.of.
` var map = Map.of("A", 1, "B", 2, "C", 3); `

Stream è una sequenza anche infinita di elementi. Può essere costruita da collezioni o anche altre astrazioni come file, canali di I/O e generatori casuali.

| Stateless        | Significato                                          |
| ---------------- | ---------------------------------------------------- |
| `filter`         | Prende solo gli elementi che soddisfano un predicato |
| `drop/takeWhile` | Esclude/mantiene elementi finché vale un predicato   |
| `map`            | Trasforma ogni elemento                              |
| `peek`           | Esegue un'operazione senza consumare l'elemento      |

al-Khwarizmi
- cifre indiane
- zero
- al-jabr, algebra

**TDD (Test Driven Development)**
1. pensare al problema e a come scrivere il test
2. scrivere un test
3. osservarlo fallire
4. scrive il <u>minimo</u> codice necessario a farlo passare
5. ristruttura
6. ripeti

pair supporta la scrittura di test

**Kata**, risolvere un problema più volte ponendo attenzione sul processo che ci porta alla soluzione piuttosto che sul risultato

Lady Augusta Ada Byron King, Countess of Lovelace
il primo programma per il calcolo dei numeri di Bernulli (1843)

### Programmazione concorrente
Teorie e tecniche per la gestione di più processi sulla stessa macchina che operano contemporaneamente condividendo le risorse disponibili.

La macchina di Turing è un fondamentale teorico mentre quello di Von Neumann è base dal punto di vista tecnologico. Subito però anche quello Von Neumann non riesce a tenere il passo: la singola CPU è un bottleneck. IBM introduce il concetto di I/O "intelligente" che non avevano bisogno di interagire costantemente con la CPU.
Abbiamo bisogno di gestire questi processi paralleli.

Legge di Amhdal individua i limiti matematici della possibile efficienza che si può ottenere con la parallelizzazione.

“The purpose of abstracting is not to be vague, but to create a new semantic level in which one can be absolutely precise.” - Dijkstra

Un processo descrive per il sistema operativo un programma in esecuzione e tutte le risorse che gli sono dedicate:
- memoria
- canali I/O
- interrupt e segnali
- stato dello CPU

Per gestire il parallelismo in uno stesso processo si instaurano i thread. I thread condividono le risorse di uno stesso processo rendendo più economico il costo di passaggio da un ramo di esecuzione all'altro.
La gestione dei thread ricade però sul programma.

| Dati / Stato | Condiviso            |                        Non condiviso |
| ------------ | -------------------- | -----------------------------------: |
| Mutabili     | **prog concorrente** |                   *prog distribuita* |
| Immutabili   | prog funzionale      | prog funzionale / *prog distribuita* |

#### I problemi della programmazione concorrente
- *Non determinismo*
  un'esecuzione concorrente è inerentemente non deterministica (nessun ordine sequenziale)
- *Starvation*
  un thread che non riceve abbastanza risorse non può fare il suo lavoro
  sono da gestire
- *Race Conditions*
  l'ordine di esecuzione può essere rilevante per il risultato ma è difficile da determinare
- *Deadlock*
  se due thread hanno ciascuno bisogno di una risorsa che è stata presa da un'altra, nessuna dei due può proseguire

**Coffmann Conditions** individua le condizioni necessarie per cui avvenga una deadlock. La mancanza di anche una sola di queste porta all'eliminazione di possibilità di deadlock.
- <u>mutual exclusion</u>
  la mutua esclusione può essere fondamentale per alcune risorse
- <u>hold and wait or resource holding</u>
  rimuovere l'attesa può portare a situazioni di starvation
- <u>no preemption</u>, non è possibile sottrarre una risorsa che è stata assegnata
  introdurre la preemption può essere molto costoso o impossibile
- <u>circular wait</u>

| Tipi di concorrenze | Strutture               |
| ------------------- | ----------------------- |
| Collaborativa       | Co-routines             |
| Pre-emptive         | Processi, threads       |
| Real-time           | Processi, threads       |
| Asincronica         | Future, events, streams |

Nella concorrenza collaborativa, i programmi devono esplicitamente cedere il controllo ad intervalli regolari. Viene ancora usato in ambiti embedded o che richiedono high performance.

Nella concorrenza pre-emptive, il sistema operativo è in grado di interrompere l'esecuzione di un programma e sottrargli il controllo delle risorse per affidarle a un altro.

La concorrenza real-time è un caso specifico di quello pre-emptive che richiedono prestazioni precise sulla suddivisione delle risorse fra i programmi.

Nella concorrenza event driven/async, i programmi dichiarano le operazioni che vanno eseguite e lasciano all'ambiente di esecuzione la decisione di quando eseguirle e come assegnare le risorse. Non si usano più i thread ma gli stream.

Nel linguaggio Java un Thread è rappresentato da un'istanza dell'omonima classe.
``` java
public Thread(Runnable target); 
void start(); // avvia un nuovo percorso di esecuzione (simile a un fork)
static void sleep(long millis); // setta un timer nella quale il processo dorme, usato per sincronizzazione
```

L'interfaccia Runnable modella un compito da cui non ci si aspetta un risultato.
``` java
@FunctionalInterface
public interface Runnable {
	/* Definizione di metodi
	 * Non puoi gestire qui le eccezioni. Da fare quando viene implementato.
	 */
	void run();
}
```

Adele Goldberg
- GUI
- Alto's demo

Il thread è "alive" quando è in uno stato in cui può rientrare in esecuzione. 
`final boolean isAlive();`

Ci sono 3 tipi di attesa
- *blocked* quando il thread è in attesa che le si venga assegnata una risorsa hardware dal sistema.
- *waiting* quando il thread è in attesa di una risorsa software e deve quindi sincronizzarsi con un altro processo in esecuzione. Se ne esce quando riceve una notify().
- *timed_waiting* quando il thread è in una attesa a tempo limite.
Si può uscire da tutte queste attese quando si viene interrotti.
``` java
public void Interrupt(); // throws InterruptException
```

Runnable sono privi di risultato. Usiamo Callable quando vogliamo thread che ritornano risultato.
``` java
public interface Callable<E> {
	/* Definizione di metodi
	 * Può gestire eccezioni
	 */
	 void run();
}
```

La classe Future viene usata per catturare il risultato della Callable alla fine della sua esecuzione.
``` java
T get(); // ritorna il risultato del Callable in Future
boolean isDone();
```

``` java
<T> T invokeAny(
	<T>
);

<T> List<Future<T>> invokeAll(callables);
```

I virtual thread sono simili ai thread normali ma non sono legati da una OS thread e sono molto più leggeri.
Le operazioni di montaggio e smontaggio sono molto più economiche di un passaggio di Thread. 