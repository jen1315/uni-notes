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