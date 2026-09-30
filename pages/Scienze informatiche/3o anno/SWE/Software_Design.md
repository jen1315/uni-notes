---
title: Software design
layout: page
share: true
---
Ingegneria deve essere ripetibile

Il problema di OOP è come definiamo gli oggetti. Le inheritance spesso sono da evitare.
Dipendenza (coupling): A->B, al cambio di B è probabile che anche A deve cambiare. Sono da ridurre il più possibile.
> "Prefer Composition over Inheritance"

- *Dipendenza (relation)*: quando un metodo di A è usato in qualche parte del codice di B. C'è una dipendenza sulla firma del metodo e lo scope è quello del metodo in cui è stato chiamato.
- *Associazione*: quando B ha un parametro di tipo A. La dipendenza ha una scope in tutta la classe A.
- *Aggregazione*: B è creato in A. Si deve gestire la sua creazione e la sua distruzione (composition).
- *Ereditarietà*: il codice di A è condiviso a B

I design pattern non sono volti a fornire soluzioni ma a definire meglio un problema e proporre una soluzione definendo pro e contro.
## Diagrammi di Casi d'uso
E' una delle metodologie. Un'altra sono le user story.

Si usa l'**UML (Unified Modeling Language)**
Visuale, comprensibili anche da attori senza conoscenze tecniche.

Individuare il dominio:
	<u>COSA</u> fa parte del *sistema*, tutto ciò su cui si ha responsabilità

Un *attore* interagisce con il sistema per accedere a delle funzionalità (*casi d'uso*). Gli attori hanno ruoli.

A->B
Precondizione A: stato del sistema prima dello scenario
Postcondizione B: stato del sistema dopo l'avvenuta dello scenario principale

IAM (Identity and Access Management)
![](img/auth.png)
> **Specifica Use Case**
> *Caso d'uso:* UC1 - Autenticazione
> *Attore principale (attivo):* cliente non riconosciuto
> *Precondizioni:* l'utente non è ancora autenticato presso il sistema
>* Postcondizioni:* l'utente è
> *Scenario principale:* 
> 1. L'utente accede al sistema
> 2. L'utente inserisce l'username
> 3. L'utente inserisce la password
> *Estensioni:*
> a. L'utente inserisce la password errata
> 	1. L'utente non accede al sistema
> 	2. Viene visualizzato errore di autenticazione

Scenario alternativo: Autenticazione esterna
Attore secondario: Google, passivo

![](img/ruoli-autore.png)
L'attore principale può avere diversi ruoli che accedono a diversi use case.

Attenzione: non concentratevi sull'ui, separazione dei casi uso per funzionalità.

## Diagrammi delle Classi
La loro precisione dipende da quanto valore fornisce.

Individuare le classi e le loro proprietà (attributi, metodi).
Attributo = $$O_{\text{scope}}$$ nome : tipo $[*=>0...n,n\in\mathbb{N}^*]$$
$$O_{\text{scope}}$$ può essere 
	+ pubblico, - privato
	# protetto, ~ default

Metodi = $$O_{\text{scope}}$ nome (attr_nome : tipo) : tipo

![](img/diagramma_classi.png)
Dipendenze 
$$\dashrightarrow$$ dipendenza semplice
$$\rightarrow$$ associazione
$$\lozenge\rightarrow$$ aggregazione; può essere condiviso
$$\blacklozenge\rightarrow$$ composizione; non può essere condiviso
$$\lhd-$$ ereditarietà, estensione

Classi astratte non possono essere istanziate. Sono scritte in italico o {abstract}.

Interfaccia può avere solo dipendenza semplice o ereditarietà quando estende un'altra interfaccia.
___ implementazione
Una linea tratteggiata collegata a una associazione rappresenta una relazione. Non sono rappresentabili nei linguaggi di programmazione.

![](img/generics.png)
\[T] per rappresentare tipi generici
<u>sottolineato</u> per metodi statici; meglio evitarli perché è difficile definire le dipendenze e non può essere sottomesso a unit test

\<T extends E> type bound non può essere rappresentato in UML.

## Diagrammi di Attività
Concorrenza è caratteristica del problema.
Parallelismo è caratteristica del sistema (runtime). Contiene la concorrenza.

![](img/diagramma_attivita.png)
Il diagramma deve essere mantenuto; non deve divergere dal codice.
Una attività può avere un solo input, usare il join per unire il risultato di più attività.

Quando le attività sono eseguite da attori con ruoli (responsabilità) diversi, si possono usare le *swimlanes*.

Evitare di progettare cicli 

## Design Pattern architetturali
Definisce le dipendenze tra i componenti. Ci sono 5 tipi.
Guidati da requisiti non funzionali.
Secondo la legge di Conway, un software viene progettato rispecchiando i rapporti sociali nelle organizzazioni.
### Architettura di tipo logico
**Layered Architecture**
Agli inizi l'organizzazione aziendale era a piramide: diversi tier dipendenti con quelli sopra e centrati da un CEO. Non funziona in aziende con molti dipendenti.
Programma back-end
1. *Application Logic*
   validazione sintattica delle applicazioni (classi controller)
   adapting delle informazioni in oggetti usabili
2. *Business Logic*
   dominio applicativo per cui sto andando a sviluppare (classi service)
   validazione semantica o di dominio
3. *Persistent Logic*
   ciò che va a comunicare con l'esterno e come vengono salvati (repository)
   le classi che si scrivono sul database si chiamano entity
Problema: la persistent logic è la più importante perché è la più vicina a quella fisica. Si inizia a strutturare l'architettura da questo strato.

**Hexagonal Architecture**
![](img/hex-logic.png)
Business logic è la più importante. Comunica con l'esterno tramite porte (driver). Gli adapting vengono fatte su queste e implementano gli use case.
### Architettura di tipo deployement
Basato sulla build, installazione del software.
**Architettura monolite**
E' composto da un monolite, detto anche artifact o installazione, indipendente dalle altre applicazioni. Da un monolite si definiscono i servizi.
Scaling
- verticale: capacità fisiche
- orizzontale: duplicazione dei servizi

Ha un problema di "big ball of mud" dove un solo monolite fatto male può portare a una serie di servizi fatti male.
Per risolvere questo si può applicare il modular monolith.

**Architettura a microservizi**
E' un'applicazione definita come una serie di microservizi, indipendenti l'uno con l'altro.
Deve stabilire come i microservizi interagiscono tra loro.
I microservizi *non possono condividere risorse* nel sistema di persistenza.

La problematica dei microservizi è la rete.
Da un sistema locale a un sistema distribuito: si perde la la proprietà di transazionalità (certezza che tutti i processi richiesti vengano eseguiti).

CAP theorem = un sistema distribuito può assicurare solo due proprietà tra Consistency, Availability e Partitioned.
Se tutte e tre sono assicurate dal sistema questa è ACID, ovvero ha la proprietà di transazionalità ed non è un sistema distribuito.
Database sQL sono ACID.

Domain Driven Design è riprodurre al livello software il dominio applicativo. 

Circuit breaker = definisce un circuit break nel caso di errore in un microservizio.
Rate limiter = definisce un limite di traffico mandato da un microservizio.
Back pressure = 

Idempotenza = gestione dati duplicati.

SemVer
Semanthic Versioning stabilisce che ogni versione può essere
- x Major, non retrocompatibile
- y Minor, retrocompatibile
- z Patch, piccole modifiche retrocompatibili

### Dependency Injection
Risolve il problema di risoluzione delle dipendenze.

Albero delle dipendenze, Direct Acyclic Graph
![](img/dag.png)
La dipendenza non ha proprietà transazionali.

```c++
class A {
	B b;    // Field injection
	A(B b); // Constructor(Ctor) injection
	void setB(B b); // Method injection
}
```

Problema
gli errori di dipendenza sono rilevabili solo in fase di esecuzione.

Injector = risolve le dipendenze per conto mio, framework.

@Inject per dichirare che le injections

*Spring (in Java)*
@Configuration, classe che specifica
	@Bean definisce come costruire un oggetto
```java
@Configuration
public class CoffeeConfig {
	@Bean
	public CoffeeLister lister() {
		return new CoffeeLister(finder());
	}
	
	@Bean
	public CoffeeFinder finder() {
		return new ColonCoffeeFinder("coffee.csv");
	}
}
ApplicationContext ctx = new AnnotationConfigApplicationContext(CoffeeCongif.class);
```
Aiutano a costruire un Context Map, oggetti costruiti e le loro dipendenze (singlets).

Con il metodo tradizionale ci sono più copie diverse del codice in ambienti diversi.

### Pattern Model-View
Pattern front-end
E' una architettura di tipo logico perché l'unico deployment che fa sono sulla macchina del cliente.

Programma front-end
0. *Presentation Logic* (classe view)
   presentazione grafica
1. *Application Logic*
2. *Business Logic* (classe model)
   implementata da un modello
3. *Persistent Logic*

View<>Model
Si deve risolvere il problema di sincronizzazione tra vista e modello.
Separation of concern, competenze per risolvere una logica

**Model-View-Controller Pattern**
Controller: reazione agli input utente (application logic)

![[model-view-controller.png|model-view-controller.png]]
View notifica il Controller quando l'utente ci interagisce
Modello notifica la View quando è stato modificato

Push Model
Pull Model

**Model-View-Presenter Pattern**
*Presenter (passive view)*
- man in the middle
- osserva il modello
- View $${-\circ\ \leftarrow\atop\longrightarrow}$$ Presenter -> Model
  modello ritorna un valore al presenter
- aggiorna e osserva la vista

View è solo un template di visualizzazione e un'interfaccia di comunicazione.

**Model-View-ViewModel Pattern**
*ViewModel*
- proiezione del modello per una vista
- binding con la vista e il modello
View
- dichiarativa
- data-binding a due vie con proprietà del ViewModel
- non possiede più lo stato dell'applicazione

## Design Pattern Creazionali
Design pattern per la creazione di istanze.
### Builder
Dobbiamo costruire oggetti complessi cioè si deve passare un grande numero di informazioni alla loro costruzione.
Problemi
- Telescoping: diversi costruttori da costruire e mantenere
- è possibile passare valori non validi

```java
public class BuilderPattern {
	static class HappyMeal {
		private String panino; //obbligatorio
		private String contorno; //obbligatorio
		private String frutta;
		private String bibita; //obbligatorio
		private String gioco;
		
		
		private HappyMeal(String panino, String contorno, String frutta, String bibita, String gioco) {
			if(panino==null || panino.isBlank())
				throw new IllegalArgumentException("Panino cannot be null or empty");
			this.panino = panino;
			this.contorno = contorno;
			this.frutta = frutta;
			this.bibita = bibita;
			this.gioco = gioco;
		}
		
		public HappyMealBuilder withPanino(String panino) {
			this.panino = panino;
			return this;
		}
		//... metodi with degli altri campi
		
		public HappyMeal build() {
			return new HappyMeal(panino, contorno, frutta, bibita, gioco);
		}
	}
	
	static enum Bibita {
		FANTA,
		COLA,
		ACQUA
	}
	
	public static void main(String[] args) {
		final HappyMeal happyMeal = new HappyMeal(panino:"Fanta");
		
		final HappyMeal happyMeal1 = new HappyMeal.HappyMealBuilder(panino:"Toast", contorno:"Patatine", bibita: "Fanta")
			.withGioco("Barbie");
	}

}
```

Kotlin è un linguaggio modello
```kotlin
data class HappyMeal(val panino:String="Toast", val bibita:String="Fanta")

val HappyMeal hm = HappyMeal(bibita="Cola")

object Singleton
```

### Singleton
Assicurarsi l'esistenza di un'*unica istanza* di classe ed avere un *accesso globale* a questa.
Motivazione: ci sono entità che non devono avere più di una istanza.
Usato per classi service.
![[singleton.png|singleton.png]]
```java
public enum Singleton {
	INSTANCE;
	public void print();
}
```

Problema: race condition e accoppiamento con tutto il codice che lo usa
Usiamo i metodi di gestione di race condition e limitiamo il suo scope.

Non è possibile effettuare i test con i Singleton.
Nei caso non si vuole far in modo che il Singleton sia recuperabile ovunque, costruire un singleton  classe con dipendenza esplicitata nel costruttore

### Abstract Factory
Fornisce una interfaccia per creare famiglie di prodotti senza specificare classi concrete.
Motivazione:
- Risulta una applicazione configurabile con diverse famiglie di componenti (es. toolkit grafico). 
- Ci sono classi astratte *factory* che definiscono le interfacce di creazione che vengono concretizzate e costruite una sola volta.

```java
public interface AbstractFactory {
	interface AbstractButton {}
	class ConcreteButton implements AbstractButton {}
	
	public static void main(String[] args) {
		final WidgetAbstractFactory widgetFactory =
			new WindowsWidgetFactory();
		
		ConcreteButton button = widgetFactory.createButton();
	}
}
```

## Design Pattern Strutturali

### Adapter
Permette di convertire l'interfaccia di una classe con un'altra.

Object adapter
```java
class PerimeterCalculator { // libreria
	interface Shape {}
}
class MySquare {} // mia applicazione

interface PerimeterCalculatorTarget {
	double perimeter(MySquare square);
}
class PerimeterCalculatorAdapter implements PerimeterCalculatorTarget {
	private final PerimeterCalculator delegate;
	
	double perimeter() {
	}
}

public static void main(String[] args) {
	final PerimeterCalculatorTarget perimeterCalculator =
		new PerimeterCalculatorAdapter(new PerimeterCalculator());
	p
}
```

Class adapter non viene spesso usata. 

### Decorator
Si vogliono mantenere le funzionalità base ma aggiungere qualcosa prima o dopo.
Funziona meglio quando la base non ha troppi metodi.
Riduce le implementazioni ai diversi

```java
public abstract class PreToppedDecorator implements Pizza {
	private final Pizza pizza;
	@Override
	public List<String> ingredients() {
		return pizza.ingredients();
	}
}
public class TomatoPizza extends PreToppedDecorator {
	public List<String> ingredients() {
		return addIngredients(pizza.ingredients());
	}
}
```

### Facade
Fornisce una interfaccia unica semplice per un sottosistema complesso. Struttura un sistema di sottosistemi.

Può essere usato per nascondere il sottosistema e gestire le classi a cui il client può interagire.

E' un single point of failure e complica le dipendenze: va utilizzato solo quando il client chiama almeno 2 classi SEMPRE.

### Proxy
E' un surrogato che condivide la stessa interfaccia della classe da mediare.
![[proxy.png|proxy.png]]

L'oggetto viene costruito solo quando viene usato (on demand) come collegamenti al server.
Es. smart pointer

## Pattern comportamentali
Permettono la definizione d
### Command Pattern
Definisce l'interfaccia per eseguirle una richiesta (oggetto)
![[command.png|command.png]]

Gestisce richieste di cui non si conoscono i particolari
Passare in input tutti parametri necessari
Lambda, funzioni passate come parametri
### Strategy Pattern
Definisce una famiglia di algoritmi intercambiabili.
![[strategy.png|strategy.png]]

Problema: non è detto che tutte le implementazioni hanno bisogno delle stesse informazioni, i metodi devono richiamare loro le informazioni aggiuntive di cui hanno bisogno

### Template Method Pattern
Fornisce un template del processo senza specificare il comportamento dei singoli


```java
public abstract class LoginManager {
	protected validateInput(username, password);
	protected authenticate(username, password);
	public User login(String username, String password) {
		validateInput(username, password);
		authenticate(username, password);
		return authorize(username);
	}
}
```

Problema: è un pattern che si basa sull'estensione, è buono finché non permette override
### Iterator
Fornisce l'accesso sequenziale a un aggregato.
Abstract

L'iteratore può essere esterno (attivo) dove l'utente controlla l'iterazione o interno (passivo) dove è controllato dall'iteratore stesso.

## SOLID Principles
- Single Responsibility principle
- Open-Close principle
- Liskov Substitution principle
- Interface Segregation principle
- Dependency Inversion principle

**Single Responsibility principle** (coesione)
Un oggetto deve avere una singola responsabilità ovvero, tutti i suoi client devono usare tutti i suoi metodi.

Problema: crea una dipendenza transitiva difficilmente tracciabile.

**Open-Close principle**
Il metodo deve essere aperto alle estensioni ma chiuso alle modifiche. 
I programmi che seguono questo principio non subiscono "cascade of changes".
es. Polimorfismo

**Liskov Substitution principle**
Funzioni che usano puntatori e riferimenti nella classe base devono poter usare oggetti dalle classi derivate senza saperlo.

Evitare override di un metodo concreto pubblico.

Design by contract: definire le pre e post definizioni dove la pre-condizione delle classi derivate devono essere più lasche della classe base mentre la post-condizione devono essere più forte.

**Interface Segregation principle**
La riduzione di accoppiamento significa dipendere dalle interfacce e non dalle implementazioni. 
Problema: implementazioni non danno errori, sono più difficili da trovare
