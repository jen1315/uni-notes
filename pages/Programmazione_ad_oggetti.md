---
layout: page
title: Programmazione ad oggetti
share: true
---

“Appunti di programmazione ad oggetti” Francesco Ranzato

Un programma è costituito da
- Algoritmi
- Dati su cui operano gli algoritmi

Focus su **algoritmi** (*programmazione procedurale*)
Focus su **dati** (*programmazione ad oggetti*)

Qualità del software
- verificabile
- mantenibile <-
- riparabile <-
- riutilizzabile <-
- portabile

Un linguaggio si dice oggetti quando ha le 3 seguenti caratteristiche
INCAPSULAMENTO, un programma può essere usato dentro un altro
EREDITARIETÀ, un programma può ereditare le funzioni di un altro
POLIMORFISMO, la chiamata di funzione si basa a runtime

**Template** per programmazione generica, ovvero indipendente del tipo delle variabili. Si gestiscono le eccezioni.

C++
- compilato
- tipizzazione forte statica
- no garbage collector
- standardizzato
- efficiente
- operatori e il loro overloading

Java
- interpretato, portatile
- forte orientamento agli oggetti, semplice e familiare
- robusto e sicuro
- dinamico
- processi thread e porte

``` c++
#include <iostream.h>
using namespace std;

int main() {
	cout << "Hello world!" << endl;
}
```
`#` direttiva del pre-processore
`main` alla base del code stack
`<<` operatore di output
``` c++
#include <iostream.h>

int main() {
	std::cout << "Hello world!" << std::endl;
}// preferibile
```

**Namespace**
Quando due variabili hanno lo stesso nome, li possiamo distinguere dal loro scope.
``` c++
namespace ns_name{
	struct X;
}
```
Alias di namespace 
``` c++
namespace alias = ns_name;
```
Direttiva di uso 
``` c++
using namespace ns_name;
```
Dichiarazione di uso
``` c++
using ns_name::X;
```

Invocazione compilatore `> gcc -xc++`

#### Stringa
Array di caratteri
``` c++
char *str = "ecco una stringa c"; // automaticamente aggiunge /0
const char *st_c = "hello"; // a solo lettura

for(int i=0; *(str+i); i++)
```

Classe stringa (istantazione di templare di classe `typedef basic_string<char> string`)
``` c++
#include <string>

int main() {
	string str = "ecco una stringa c++";
	int length = str.size();
}
```

Un tipo di dato viene detto **astratto** (ADT), quando la sua semantica è separata dalla sua implementazione. La sua rappresentazione interna è inaccessibile.
ADT = Valori + Operazioni (metodi pubblici)

Struct non è un ADT, tutto è accessibile.

>Principio dell’*Information Hiding*
>Metodo progettuale di segregazione delle informazioni che hanno più possibilità di cambiare in modo da proteggere le altre parti del programma da modifiche estensive quando viene cambiato il design

Classe implementa gli ADT. La dichiarazione di classe consiste da
- campi dato
- metodi, funzione di una classe, uno di loro è costruttore

``` c++
 class orario {
  private:  // specificatore di accesso
	short int seconds;
	
  public:
	orario();
	orario(short int o, short int m=0, short int s=0);
	short int Ore();
	short int Minuti();
	short int Secondi();
	// hanno un argomento implicito oggetto di invocazione del metodo
	
	orario::orario() {
		sec = 0;
	}
	
	orario::orario(short int o, short int m, short int ) {
		if(o<24 && m<60 && s<60) {
			sec = s + m*60 + o*3600;
		}
	}
	
	short int orario::Ore() {
		return sec / 3600;
	}// preferibile scritta separatamente dalla dichiarazione perché sarebbe inline e potrebbe essere interpretata come macro
	
	short int orario::Minuti() {
		return (sec / 60) % 60;
	}
	
	short int orario::Secondi() {
		return sec % 60;
	}
	
	int main() {
		orario o1;
		orario o2(15, 30, 15);
		orario o3 = orario(14, 20, 05); // costruttore di copia
		orario *ptr = new orario; // new è la malloc di C++
	}
};
```
Le diverse istanze di oggetti sono salvati individualmente mentre i metodi sono salvati una sola volta.
Oggetto di invocazione e metodo invocato sono legati dal parametro implicito `*C this`.

**Costruttore di Copia** `C(const T&)`
`orario o = orario(14, 20, 5);`
crea una istanza di oggetto anonimo e temporaneo (senza l-valore) che viene poi assegnato a un oggetto.

N.B. Diverso da `o = orario(14, 20, 5);` che è solo una assegnazione
``` c++
orario copia1 = o;
orario copia2(o); // preferibile
```

**Costruttore Standard**
quando non definiamo un costruttore, è già presente uno standard di default. Se definiamo un costruttore con argomenti, `orario o;` non è più un codice valido.

COMPCERT Xavier Lerox (compilatore ottimizzato che ritorna prova matematica)

new e delete in C++
malloc e free in C

**Argomenti di default**
`funzione func(int a, int b = 0, int c = 0);`
Tutti gli argomenti a destra di quello con default devono avere default.

**Conversione Implicita**
``` c++
orario s,t;
s = 8;    // equivale a s = orario(8);
t = 8+12; // equivale a t = orario(8+12);
```
Quando una variabile non è dello stesso tipo dell’oggetto a cui è assegnato, avviene una conversione implicita dove viene convertito in un oggetto ammissibile.

**Operatori Espliciti di Conversione**
``` c++
class orario {
public:
	operator int() {return sec;}
	. . .
}
orario o(12, 25);
int s = o; // richiama implicitamente int() su o
```
`explicit` blocca le conversioni implicite, utile quando non hanno senso.

Metodi e oggetti di invocazione costanti
``` c++
class orario {
public:
	. . .
	orario UnOraPiuTardi(); // sola lettura
	void AvanzaUnOra();  // lettura-scrittura
	
	orario orario::UnOraPiuTardi() const{ // non causa side-effects
		orario tmp;
		tmp.sec = (sec/3600) % 86400;
		return tmp;
	}
	
	void orario::AvanzaUnOra() {
		sec = (sec/3600) % 86400;
	}
}
const orario LE_TRE(15);
orario t;
t = LE_TRE.UnOraPiuTard();
```
Nei metodi costanti `this` è di tipo `const *C`. 
Ai oggetti costanti e nei metodi costanti si possono invocare solo metodi anche essi costanti.
L’eccezione sono i costruttori.
$$\boxed{\text{Make everything const, as much as possible.}}$$
**Riferimento**
``` c++
int x = 2;
int& a = x; // tipo rifermento, ALIAS
int& q = 4; // ILLEGALE

int y = 3;
a = y; // x=3

const int& r=x; // sola lettura
const int& rq=4; // LEGALE
```
Puntatori
``` c++
int *p1 = &x;
p1 = &y; // LEGALE
int *const p2 = &x; // costante l-valore
p2 = &y; // ILLEGALE
const int *p3 = &x; // protegge r-valore
p3 = &y; // LEGALE
*p3 = 5; // ILLEGALE

const int *const p = &x; // sola lettura
```
Differenza con i puntatori
- Non esiste riferimento `NULL`
- il riferimento è inizializzato a un oggetto e non può essere cambiato
- Alias non può essere definita senza inizializzazione.

*Passaggio dei parametri come riferimento* (invece dei puntatori)
modifica e legge le variabili passate.
``` c++
// PASSAGGIO PER RIFERIMENTO TIPO COSTANTE
void fun1(const Big& r);
void fun2(Big v); // per valore, da evitare

Big b(. . .);
fun1(b); // copia di riferimento a Big
fun2(b); // costruttore di copia di Big
```

*Ritornare un riferimento*
``` c++
int v[] = {3, 2, 6, 0, 5}; // variabile globale

int& setValue(int i) {
	return v[i];
}

int main() {
	setValue(2) = 5; // modifica v[2]
}
```
Non puoi ritornare un riferimento di una variabile locale.

*Ritorno di riferimento costante*
``` c++
const int& f() {return 4;}
int main() { f(); }

// warning: ritorna riferimento a un oggetto temporaneo

const int& f(int* p) {return *p;}
int main() { f(new int(4)); } // LEGALE
```

Esercizio
``` c++
class C {
private:
	int x;
public:
	C(int n=0);
	C F(C obj);
	C G(C obj) const;
	C H(C& obj);
	C I(const C& obj);
	C J(const C& obj) const;
	
	C::C(int n=0) { x=n; }
	C C::F(C obj) { C r; r.x = obj.x + x; return r; }
	C C::H(C& obj) { obj.x += x; return obj }
	// r è temp, C è senza l-valore
	C C::G(C obj) const { C r; r.x = obj.x + x; return r; }
	C C::I(const C& obj) { C r; r.x = obj.x + x; return r; }
	C C::J(const C& obj) const { C r; r.x = obj.x + x; return r; } // ha l-valore
};

int main() {
	C x, y(1), z(2), const C v(2);
	z=x.F(y);
	// v.F(v) non funziona, const può usare solo metodi const
	v.G(y);
	(v.G(y)).F(x); // G() ritorna C, quindi F() funziona
	(v.G(y)).G(x); // conversione C a const C
	// x.H(v) non funziona, cerca funzione c::H(const C&)
	// x.H(z.G(y)) non funziona, riferimento vuole l-valore
	x.I(z.G(y)); // riferimento const non ha bisogno di l-valore
	x.J(z.G(y));
	v.J(z.G(y));
}
```

### Metodi e dati static (di classe)

Metodo che non fa uso di `this` e dato di una classe utilizzabile ovunque
``` c++
class orario {
public:
	static orario OraDiPranzo();
	static int Sec_di_una_ora; // invece delle variabili globali
	static int Sec_di_un_giorno;
	
	orario orario::OraDiPranzo() {
		return orario(13,15);
	}
};

// da inizializzare fuori
int orario::Sec_di_una_ora = 3600;
int orario::Sec_di_un_giorno = 86400;

```

Nel caso vuoi rendere i dati statici costanti, si possono inizializzare inline dentro la classe.
``` c++
class orario {
public:
	. . .
	static const int Sec_di_una_ora = 3600;
	. . .
};
```

I metodi di una classe hanno accesso della parte privata anche delle istanze della classe passati per parametro.

### Overloading degli operatori

Funzionano come i metodi usati finora.
``` c++
class orario {
public:
	...
	orario operator+ (orario) const;
	
	orario orario::operator+(orario o) const {
		orario aux;
		aux.sec = (sec + o.sec) % 86400;
		return aux;
	}
};

int main {
	...
	orario ora(22,45);
	orario DUE_ORE_E_UN_QUARTO(2,15);
	ora = ora + DUE_ORE_E_UN_QUARTO;
}
```

**Regole di overloading**
1. Non si possono cambiare
	- posizione
	- numero operandi
	- precedenze e associatività (* prima di +)
2. Deve esserci un tipo definito dall'utente
3. Gli operatori "=", "\[ \]" e "->" si possono sovraccaricare solo come metodi
4. Non si possono overload ".", "::", "sizeof", "typeid", i cast e "? :"
5. Gli operatori "=", "&" e "," hanno versione standard
6. Non può essere metodo statico.

Se è un metodo allora l’oggetto d’invocazione è il primo argomento.

```
[OPERATORS]
+ - * / % == != < <= > => ++ --
<< >> = -> [] () & new delete
```
Gli operatori `“=“, “[]” e “->”` devono avere parametro `this`, quindi il loro overload è metodo interno

`++b` incrementa e ritorna b
`b++` ritorna b e incrementa

xcasa
- Definizione degli operatori `-, ==, > e <` per la classe orario
- Definizione degli operatori `+, -, ==, > e <` per la classe complesso

**Operatore di assegnazione =**
`C& operator =(const C&)`
> L’operatore di assegnazione per una classe, fa assegnamento membro per membro e i suoi sotto-oggetti. Ogni sotto-oggetto è assegnato in un modo appropriato per tipo.

``` c++
int x=1, y=4, z=7;
x = y = z;

cout << x << " " << y << " " << z; // ritorna 7 7 7
 ```
 
 Il costruttore di copia viene invocato
 1. quando una istanza di oggetto viene dichiarata e inizializzata con un altro oggetto della stessa classe
 2. quando un oggetto viene **passato per valore**
 3. quando una funzione **ritorna per valore**
	 Lo standard propone una ottimizzazione a questo punto: evita di creare un temporaneo anonimo che è usato per inizializzare un altro oggetto dello stesso tipo (questo cambia a seconda del compilatore usato).
``` c++
C fun(C a) { return a; }
C f(C a) {
	C b(a);
	C c=b;
	return c;
}

int main() { // con g++ ottimizzato quante invocazioni di c. di copia?
	C c;
	fun(c); // 2 invocazioni
	
	C y = fun(c); // 2 invocazioni, non 3
	
	C z; z = fun(c); // 2 invocazioni
	
	fun(fun(c)); // 3 invocazioni, non 4
	
	C x;
	C y = f(f(x)); // 7 invocazioni
}
```
`> g++ -fno-elide-constructors` al compilatore rimuove questa ottimizzazione

**Funzionalità di stampa**
Viene definito facendo overloading dell’operatore di output `<<`.
Non funziona come metodo di una classe perché sarebbe obbligato ad avere il `this` come primo parametro. È funzione esterna.
``` c++
// deve essere invocato a cascata, quindi ritorna lo stream
ostream& operator<<(ostream& os, const orario& o) {
	return os << o.Ore() << ":" << o.Minuti() << ":" 
			  << o.Secondi();
}
```
Possiamo raggrupparlo insieme alla classe con un namespace.

(Martedì iniziamo alle 14:00)

**Operatore di somma +**
Come metodo interno, NON È COMMUTATIVA
``` c++
class orario {
public:
	orario orario::operator+(const orario& o) const;
}

int main() {
	orario t(12,20), s;
	s = t+4; // FUNZIONA
	s = 4+t; // l’ordine è importante: 4 è un temp anonimo, NON FUNZIONA
}
```
Come funzione esterna
``` c++
orario operator+(const orario& t, const orario& s);

int main() {
	orario t(12,20), s;
	s = 4+t;
	s = 4+5;
}
```
MA! L’operatore non ha più accesso ai parametri interni di orario. 
``` c++
// File Point.h
class Point{
private:
	double _x, _y, _z;
public:
	Point(double x, double y, double z);
	Point();
	double getX() const;
	double getY() const;
	double getZ() const;
	void negate();
	double norm() const;
};

// File Point.opp
#include "Point.h"

// conversione double => Point
Point::Point(double x=0.0, double y=0.0, double z=0.0) {
	_x=x; _y=y; _z=z;
}

double Point::getX() const { return _x; }
double Point::getY() const { return _y; }
double Point::getZ() const { return _z; }

void Point::negate() {
	_x=-_x; _y=-_y; _z=-_z;
}

double Point::norm() const {
	return sqrt(_x^2+_y^2+z^2);
}
```

Preprocessore, sostituzione sintattica
- Direttive al preprocessore
- `#include`: direttive di inclusione
- `#define`: direttive di macro
- direttive di compilazione condizionale

-> Inclusione multipla di file header
``` c++
#ifdef ORARIO_H
#define ORARIO_H
class orario {
	...
};
#endif
```

`> g++ -c orario.cpp`
Compila e non linka, produce il file .o
Source —-> Object file
Source <-/- Object file
Impossibile ottenere source esatto, ma esistono decompiled per reverse engineering
Code obfuscation, codice inutile usato per offuscare il source code dal reverse engineering.

Qt Creator
Valgrind, Valkyria

### Modularizzazione classi (composizione)
Relazione *has-a*
Un oggetto è campo dato di un altro oggetto.
``` c++
#ifndef TELEFONATA_H
#define TELEFONATA_H
#include <iostream>
#include "orario.h"

class Telefonata {
private:
	orario inizio, fine;
	const int numero; // non possono essere modificati quindi deve essere assegnato in inizializzazione
public:
	telefonata(orario,orario,int);
	telefonata();
	orario Inizio() const;
	orario Fine() const;
	bool operator==(const telefonata&) const;
};
ostream& operator<<(ostream&, const telefonata&);
#endif
```
La posizione in memoria dipende dall’ordine di dichiarazione. \[obj orario | int\]
Parametri oggetto sono sempre costruiti di default.
``` c++
#include “telefonata.h”
// lista di inizializzazione, costruttore di copia esplicita
telefonata::telefonata(const orario& i, const orario& f, const int& n) : inizio(i), fine(f), numero(n) {}i

bool telefonata::operator==(const telefonata& t) const {
	return inizio == t.inizio &&
		fine == t.fine &&
		numero == t.numero;
}
```

#### Container (Abstract data type)
Contenitori sono implementati in congiunzione con gli iterattori.
Da STL (Standard Template Library): list, vector, map, …
``` c++
#ifndef BOLLETTA_H
#define BOLLETTA_H
#include "telefonata"
class bolletta {
public:
	bolletta();
	bolletta(const bolletta&);
	~bolletta();
	bool Vuota() const;
	void Aggiungi_Telefonata(const telefonata&);
	void Togli_Telefonata(const telefonata&);
	telefonata Estrai_Una();
	bolletta& operator=(const bolletta& y);
private:
	class nodo {
	public:
		nodo();
		nodo(const telefonata, nodo*);
		telefonata info; // campi possono ricadere in public: perchè 
		nodo* next;      // siamo in private: di bolletta
	};
	nodo* first; // puntatore al primo nodo della lista
	static nodo* copia(nodo*);
	static void distruggi(nodo*);
};

#endif
```

I namespace sono annidabili; per accedere a nodo usiamo bolletta::nodo.
``` c++
#include "bolletta.h"

bolletta::nodo::nodo() : next(nullptr) {} // da c++ 11, prima era 0
bolletta::nodo::nodo(const telefonata& t, nodo* s) : info(t), next(s) {}

bolletta::bolletta() : first(nullptr) {}
bool bolletta::Vuota() const {
	return first == nullptr;
}

void bolletta::Aggiungi_Telefonata(const telefonata& t) {
	first = new nodo(t,first);
}

void bolletta::Togli_Telefonata(const telefonata & t) {
	nodo* p=first, *prec=nullptr;
	while(p && !(p->info == t)) {
		prec = p;
		p = p->next;
	}
	if(p) {
		if(prec==nullptr)
			first = p->next;
		else
			prec->next = p->next;
		delete p;
	}
}

telefonata bolletta::Estrai_Una() {
	// precondizione: bolletta non vuota
	nodo* p = first;
	first = first->next;
	telefonata aux = p->info;
	delete p;
	return aux;
}
```
Attenzione: Aggiungi_Telefonata e Togli_Telefonata possono causare side effects.
Se assegno una bolletta b1 a una b2 (copia campo per campo), questi metodi applicati su una delle due, causa side effects anche l’altra. b1 e b2 hanno puntatori che puntano a uno stesso spazio di memoria (**aliasing**).

Dobbiamo fare **DEEP COPY**.
``` c++
class bolletta {
public:
	. . .
	bolletta(const bolletta&);
	bolletta& operator=(const bolletta& y);
private:
	. . .
	static nodo* copia(nodo*);
	static void distruggi(nodo*);

};

// ASSEGNAZIONE PROFONDA

bolletta::nodo* bolletta::copia(nodo* p) {
	if(p==nullptr) return nullptr;
	nodo* primo = new nodo(p->info,nullptr);
	nodo* q = first;
	while(p->next != nullptr) {
		p = p->next;
		q->next = new nodo(p->info,nullptr);
		q = q->next;
	}
	delete q;
}

bolletta::nodo* bolletta::copia(nodo* p) {
	if(!p) return nullptr;
	else
		return new nodo(p->info,copia(p->next));
}

bolletta::nodo* bolletta::distruggi(nodo* p) {
	if(p) {
		distruggi(p->next);
		delete p;
	}
}

bolletta& bolletta::operator=(const bolletta& b) {
	if(this != &b) {
		distruggi(first);
		first = copia(b.first);
	}
	return *this;
}

// COSTRUZIONE DI COPIA PROFONDA

bolletta::bolletta(const bolletta& b) : first(copia(b->first)) {}
```

Funzioni esterne costruita con l’interfaccia disponibile
``` c++
orario Somma_Durate(bolletta b);
bolletta Chiamate_A(int num, bolletta& b);

bolletta Chiamate_A(int num, bolletta& b) {
	bolletta selezionate, resto;
	while (!b.Vuota()) {
		telefonata t = b.Estrai_Una();
		if(t.Numero == num)
			selezionate.Aggiungi_Telefonata(t);
		else
			resto.Aggiungi_Telefonata(t);
	}
	b = resto;
	return selezionate; // temporaneo anonimo da ritornare fa garbage 
}
```

Al ritorno di un oggetto temporaneo anonimo si fa un costruttore di copia e il temporaneo rimane come *garbage*.

**Lifetime di un oggetto**
In linguaggi con **garbage collector**, gli oggetti sono in uno heap e il loro lifetime è determinata 
Le variabili statiche si trovano in uno spazio di memoria statica che dura per tutta la durata del programma.
Le variabili locali automatiche sono allocate e deallocate nel call stack. Le variabili dinamiche sono allocate dinamicamente nello heap.

| Tipo      | Nascita            | Morte                  |
| --------- | ------------------ | ---------------------- |
| Statiche  | Avvio programma    | Fine programma         |
| Locali    | { } nel call stack | Pop { } dal call stack |
| Dinamiche | Costruzione, new   | Distruzione, delete    |
### Distruttore
**Distruttore standard**: invoca il “distruttore” per tutti i campi dati della classe, nell’ordine *inverso* della loro dichiarazione.

DEEP DESTRUCTION
``` c++
class bolletta {
public:
	. . .
	~bolletta();
	. . .
}

bolletta::~bolletta() {
	distruggi(first); // applicata al delete di bolletta
}

// ALTRA OPZIONE - - - - - - - 
bolletta::nodo::~nodo() {
	if(next != nullptr)
		delete next; // chiamata ricorsiva
}
bolletta::~bolletta() {
	if(first) delete first;
} // ATTENZIONE: questa opzione, se si chiama remove di un singolo nodo c’è delete al nodo e nel caso sia first, tutta la lista diventa irraggiungibile
```
Nel g++ e clang l’ordine di distruzione nelle funzioni è variabili locali, parametri passati per valore e oggetto anonimo ritornato per valore.

>**Rule of three**
>Se una classe ridefinisce una dei tre
>- Distruttore
>- Costruttore di copia
>- Operatore di assegnazione
>probabilmente tutte e tre devono essere ridefinite.

``` c++
int arrayStatico[5] = {3,2,-3};
int *arrayDinamico = new int[5];
arrayDinamico[0] = 3;
*(arrayDinamico+1) = 2; // è uguale a arrayDinamico[1]
delete[] arrayDinamico; // dealloca tutto l’array
```

I file .h e .opp sono consegnati al cliente. Nel file .h si vede la definizione delle parti private.
Come nascondiamo le informazioni?
``` c++
// file C_handle.h
class C_handle{
public:
	// parte pubblica
private:
	class C_private; // dichiarazione incompleta
	C_privata* punt; // solo puntatore dell’oggetto
}
```
I puntatori posso essere definiti anche solo dopo una dichiarazione incompleta. La dichiarazione completa serve quando dobbiamo deferenziarli.
Oggetti così definiti si trovano sullo heap e sono puntati dall’handle.
``` c++
// file C_handle.cpp
class C_handle::C_privata{
	// parte privata
}
```

**Friend Function**
La funzione Friend viene usata per dare accesso alla parte privata della classe.
<u>Attenzione</u>: Se è usato molto spesso, c’è probabilmente un problema di design.
``` c++
// file bolletta.h
class bolletta{
	. . .
	friend ostream& operator<<(ostream&, const bolletta&);
	. . .
}
```

``` c++
// file .cpp
ostrema& operator<<(ostream& os, const bolletta& b)
```
(2003) Le classi annidate non hanno accesso alla classe contenitrice.
(2011) Una classe privata è un membro della classe contenitrice e come essa ha accesso alla parte privata.

La relazione di amicizia non è simmetrica e non è transitiva.
### Iteratore
``` c++
class contenitore {
private:
	class nodo{
		. . .
	};
	nodo* first;
public:
	class iterator {
		friend class contenitore; // NECESSARIA
	private:
		contenitore::nodo* punt;
	public:
		bool operator==(const iterator& i) const;
		bool operator!=(const iterator& i) const;
		iterator& operator++();
		// nessun costruttore, si usa quello standard
	};
	iterator begin() const;
	iterator end() const; // ritorna past-end
	int& operator[](const iteratore&) const;
} 
```
L’iteratore è annidato nella parte *pubblica* della classe che itera. La classe deve essere definita con friend nell’iteratore.

``` c++
bool contenitore::iterator::operator==(const contenitore::iterator& i) const {
	return punt == i.punt;
}

bool contenitore::iterator::operator!=(const contenitore::iterator& i) const {
	return punt != i.punt;
}

contenitore::iterator& contenitore::iterator::operator++() {
	if (punt) punt=punt->next; return *this;
}

contenitore::iterator contenitore::begin() const {
	iteratore aux;
	aux.punt = first; // per amicizia
	return aux;
}

contenitore::iterator contenitore::end() const {
	iteratore aux;
	aux.punt = 0; // per amicizia
	return aux;
}

int& contenitore::iterator::operator[](const contenitore::iterator& it) const {
	return it.punt->info; // per amicizia, nessun controllo su it.punt
}
```

Gli iteratori sono spesso usati per parse il contenitore (ad esempio nei cicli for).
``` c++
int main() {
	contenitore c;
	for(auto it=c.begin(); it!=c.end(); ++it)
		// it è puntatore di un oggetto in c
}

```

**Overloading dell’operatore di ->**
Operatore di selezione solitamente ritorna un puntatore a classe.
``` c++
class bolletta{
public:
	class iteratore{
		friend class bolletta;
		private:
			bolletta::nodo* punt;
		public:
			telefonata* operator->() const { return &(punt->info); }
			telefonata& operator*() const { return punt->info; }
			// solo il puntatore è costante, con questi metodi possiamo modificare la telefonata a cui punta
	}
};
```
#### Conversione di tipo
**Tipi di variabile**
- *primitivi*
  void
  integer: int e char
  floating: float (IEEE-754) e double
- *derivati*, puntatori
  array
  pointers
  references
- *definiti dall'utente*, oggetti
  structures
  union
  classes
  enumerations

Standard: `sizeof(char)<=sizeof(short)<=sizeof(int)<=sizeof(long)<=sizeof(long long)`

**Conversione di tipo**
Ogni linguaggio di programmazione ha le proprie regole sulla conversione di tipo.
Caratteristica conversioni
- implicite (coercions) / esplicite
- predefinite / definite dall'utente
- con (narrow) / senza (wide) perdita di informazione

*Conversione implicita*
Un'espressione e è convertibile implicitamente a un tipo T quando T può essere costruito da copia da e. `T t=e`
``` c++
// T& => T

// T[] => T*
int[2] a={3,1}; int* p=a;

// T* => void*
// puntatore generico, senza tipo
int* p=&x; void* q=p;

// T => const T
int x=5; const int y=x;

// const NPR => NPR
// NPR = tipo non puntatore o riferimento
const int x=5; int y=x;
int* const p=&x; int* q=p;

// T* => const T*
int* p=&x; const int* q=p;

// T => const T&
const int& x=5;

// e quelli tra TIPI PRIMITIVI con WIDE CONVERSION
```
Attenzione: se convertiamo i tipi primitivi dobbiamo tenere conto sul cambio di rappresentazione quindi, anche se funziona implicita, è meglio segnarla con uno static_cast.
``` c++
char c = 's';
int x = static_cast<int>(c);
```

*Conversione esplicita*
- `static_cast`
- `const_cast`, per rimuovere l'attributo const di un oggetto
- `reinterpret_cast`, converte il puntatore di un tipo a un puntatore di altro tipo
- `dynamic_cast`, fatto a runtime

STATIC_CAST
``` c++
// narrowing conversion
double d = 3.14;
int x = static_cast<int>(d);

// T* => void*
void* p; p=&d;

// conversione di void*
double* q = static_cast<double*>(p);
```

CONST_CAST
Permette di convertire un puntatore o un riferimento da const T a T.
Attenzione: quando si usa, probabilmente c'è un <u>errore di design</u>.
``` c++
const int i=5;
int* p = const_cast<int*>(&i);

void F(const C& x) {
	x.metodoCostante();
	const_cast<C&>(x).metodoNonCostante();
}
```

REINTERPRET_CAST
Permette di convertire il puntatore di un tipo a un puntatore di un altro tipo.
``` c++
Classe c;
int* p = reinterpret_cast<int*>(&c);
const char* a = reinterpret_cast<const char*>(&c);
string s(a);
cout << s;
```

### Template
Per funzioni uguali tra tipi differenti, senza il template, dobbiamo fare tante funzioni quanti i tipi che abbiamo.

Per sistemare questo potremmo usare macro MA
nel caso di operazioni negli argomenti, porta ad errori.

*Programmazione generica*
- generics
  Java, non introdotta nella ver.1 dove tutti i tipi sono sottotipi del tipo universale (ma aveva bug)
- template
  C++ e D

I template di C++ permette di operare funzioni e classi con tipo generico.

``` c++
template <class T> // oppure template <typename T>
T min(T a, T b) {
	return a < b ? a : b;
}
```
Il compilatore è fortemente tipato, questo codice non è compilabile.
Deve essere **istanziato**.
``` c++
int main() {
	int i,j,k;
	orario r,s,t;
	...
	// istanziazione implicita del template
	k = min(i,j);
	t = min(r,s);
	// oppure: istanziazione esplicita del template
	k = min<int>(i,j);
	t = min<orario>(r,s);
}
```
I parametri di un template posso essere
- Parametri di tipi, si possono stanziare con un tipo qualsiasi
- Parametri valore di qualche tipo, si possono stanziare con un valore letterale del tipo indicato
Attenzione: il tipo di ritorno non viene considerato nella deduzione degli argomenti (il return è opzionale).

L’istanziazione dei parametri di tipo deve essere UNIVOCA. L’uso di funzione template istanziata *implicitamente* su argomenti di tipo diverso, non compila.

Ci sono solo 4 conversioni implicite considerate:
- lvalue a rvalue
- array a puntatore
- quantificazione costante
- rvalue a riferimento costante
``` c++
template <class T> void E(T x) { . . . };
template <class T> void F(T* x) { . . . };
template <class T> void G(const T x) { . . . };
template <class T> void R(const T& x) { . . . };

int main() {
	int i=6; int& x=i;
	int a[3]={4,2,9};
	E(x), F(e), G(i), E(7);
}
```

L’uso di una funzione template istanziata esplicitamente su argomenti di tipo diverso, viene eseguita una conversione implicita.

``` c++
template <class T, int size> T min(T (&a) [size]) { 
	. . . 
};

int main() {
	int ia[20];
	orario ta[50];
	. . .
	cout << min(ia);
	cout << min(ta);
}
```

Qual è il modello di compilazione del template?

**Compilazione per inclusione**
Il template completo (dichiarazione, definizione) è nel “header file”. Non c’è concetto di compilazione separata di un template.
Problema 1: No information hiding.
Problema 2: Istanza multiple del template per ogni uso in file diversi.

Problema 2 è risolvibile con *dichiarazione esplicita di istanziazione*
``` c++
#include "min.h"
template int min(int, int);
template orario min(orario, orario);
```
E nella console:
> g++ -fno-implicit-templates -c file.cpp

Esisteva una compilazione per separazione (export) per cui si compilava solo quello che si riusciva a compilare. Era difficile da implementare: stata rimossa da C++11.
La keyword `export` è ora stata riutilizzata per la definizione di moduli.

Svantaggi dei template
- non tutti i compilatori supportano i template
- il tempo di build aumenta
- la codifica e il debug è più complesso
- il nesting di templates non è supportato da tutti i compilatori
- i template sono negli header quindi una loro modifica richiede un rebuild dell’intero progetto
- non c’è information hiding

#### Template di classe
Queue, coda FIFO (First In First Out)
``` c++
// file queue.hpp
template <class T>
class QueueItem {
public:
	QueueItem(const T&);
	T info;
	QueueItem* next;
};

template <class T>
class Queue {
public:
	Queue();
	~Queue();
	bool empty() const;
	void add(const T&);
	T remove();
private:
	static int contatore;
	QueueItem<T>* primo;
	QueueItem<T>* ultimo;
};
```
L’istanziazione di template di classe devono essere **esplicite** o devo definire un default.
`template <class Tipo=int, unsigned int size=1024>`

<u>Nota bene</u>: il compilatore genera una istanza di un template (di classe o funzione) *solo quando è necessario*.
Istanzia solo le classi/funzioni richieste dal codice per compilare.

Anche se tutto il template sta nel “header” file, i metodo devono essere definiti fuori dalla definizione di classe.
I campi dati statici sono istanziati fuori dal template di classe perché dipendono dal tipo del template.
``` c++
// sempre file Queue.hpp
template <class T>
class QueueItem { . . . };

template <class T>
class Queue { . . . };

// definizione esterna
template <class T>
int Queue<T>::contatore = 0; // campo dati statico

template <class T>
QueueItem<T>::QueueItem(const T& val) : info(val), next(0) {}

template <class T>
Queue<T>::Queue() : primo(0), ultimo(0) {}

template <class T>
bool Queue<T>::empty() const {
	return (primo==0);
}

template <class T>
void Queue<T>::add(const T& val) {
	if(empty())
		primo = ultimo = new QueueItem<T>(val);
	else {
		ultimo->next = new QueueItem<T>(val);
		ultimo = ultimo->next;
	}
}
```

##### Amicizie in template di classe
3 tipi di amicizie
- friend non template, come usati precedentemente
- friend associato
- friend non associato

**Friend associato**
``` c++
template <class U1,…,class Uk> class A;
template <class V1,…,class Vj> void fun(…);

template <class T1,…,class Tn> class C {
	friend class A<…,Ti,…>;
	friend void fun<…,Ti,…>(…);
}
```

**Friend non associato**
Non molto usato, da amicizia completa 
``` c++
template <class T>
class C {
	template <class Tp>       // amicizia di metodo
	friend int A<Tp>::fun();
	
	template <class Tp>       // amicizia di classe
	friend class B;
	
	template <class Tp>
	friend bool test(C<Tp>);  // amicizia di funzione
}
```

##### Annidamento di template
``` c++
template <class T>
class Queue {
private:
	// template di classe annidato “associato”
	class QueueItem {
	public:
		QueueItem(Const T& val);
		T info;
		QueueItem* next;
	};
	. . .
};
```
Un `QueueItem<T>` è un **tipo implicito** (typename) perché non è del tutto definito ma dipende implicitamente dai parametri di tipo di `Queue<T>`.

``` c++
template <class T>
class C {
public:
	class X {
	public:              // template di classe annidata associato
		T d;             // T del template contenitore
	};
	
	template <class U>
	class E {            // template di classe annidata
	public:              // non associato
		T x;             // T del template contenitore
		U y;             // suo parametro di tipo U
		void fun1() { return; }
	};
	
	template <class U>
	void fun2() {         // template di metodo istanza
		T x; U y; return; // non associato
	};
};

// ora voglio usare questi template per costruire una funzione
template <class T>
void templateFun(typename C<T>::D d) {
	// C<T> usa un tipo che dipende da T
	typename C<T>::X d2=d;
	
	// E<int> usa template di classe annidata che dipende da T
	// C<T>::E<int> usa un tipo che dipende da T
	typename C<T>::template E<int> e;
	e.fun1();
	
	// c.fun2<int> usa un template di funzione che dipende da T
	C<T> c;
	c.template fun2<int>; 
}
```

Per forward declaration, controlla il tuo compilatore.
#### STL (Standard Template Library)
Da non confondere con il C++ Standard Library, la libreria dei template di contenitori.

Contiene 
- Contenitori 
- Iteratori
- Algorithms

| Sequence Containers | Description        | Random access |
| ------------------- | ------------------ | ------------- |
| array               | array class        | x             |
| vector              | vector             | x             |
| deque               | double ended queue |               |
| forward_list        | linked list        |               |
| list                | double-linked list |               |

| Associative Containers | Description |
| ---------------------- | ----------- |
| set                    |             |
| alberi                 |             |

`for_each(InputIterator first, InputIterator last, UnaryFunction)`
funzioni passati come argomenti
##### Vector
Array dinamico.
![](img/Pasted%20image%2020241115145350.png)
capacity() da lo spazio allocato per il vettore.
size() da il numero di elementi salvati nel vettore.
begin() e end() danno il puntatore per l'inizio e il successivo alla fine degli elementi salvati.

- supporta l'**accesso casuale** (tempo costante)
- inserimento e rimozione *in coda* in *tempo costante ammortizzato*
- inserimento e rimozione *arbitraria* in *tempo lineare ammortizzato*
- capacità può variare dinamicamente (raddoppia)
- gestione della memoria automatica

Ci sono 2 modi di usare vector: come l'array di C e lo stile STL del C++.
``` c++
vector<int> v(10,-1) // vettore di 10 elementi da -1

// METODI CONTENITORI SEQUENZIALI
void push_back(const T&);
void pop_back(); // invoca distruttore
T& front();
T& back();
iterator begin();
iterator end();
```

Per fare input e output con un file, dobbiamo creare un oggetto ifstream.

Per scorrere il vettore, si deve fare uso di iteratori
- `C::iterator`, lettura e scrittura
- `C::const_iterator`, sola lettura
begin() e end() ritornano const_iterator o iterator dipendentemente da se vettore è const o no.

``` c++
template <class InputIterator>
vector(InputIterator, InputIterator)
...
int a[20];
vector<int> v(&a,&a+6);
```

Metodi di cancellazione
``` c++
vector<int> v{1,2,3,4};
v.pop_back(); // distrugge l'ultimo elemento
v.erase(2); // distrugge elemento in posizione 2, costo lineare
// funziona su contenitore qualsiasi
```
operator\[] funziona solo con contenitore a accesso casuale

`stack<deque>` e `queue<deque>`

List
Implementata come una lista doppiamente linkata.
- accesso sequenziale (`operator[]` non funziona)

## Ereditarietà
Classe che eredita da un'altra classe, si dice <u>derivata</u> (sottoclasse) -> D
Classe da cui viene derivata si chiama <u>classe base</u> (superclasse) -> B

<table>
	<thead>
	<tr><td>Classe base</td><td colspan="3">Classe derivata con derivazione</td></tr>
	</thead>
	<tbody>
	<tr><td>membro</td><td><i>pubblica</i></td><td><i>protetta</i></td><td><i>privata</i></td></tr>
	<tr><td><b>privato</b></td><td>inaccess.</td><td>inaccess.</td><td>inaccess.</td>
	<tr><td><b>protetto</b></td><td>protetto</td><td>protetto</td><td>privata</td></tr>
	<tr><td><b>pubblico</b></td><td>pubblico</td><td>protetto</td><td>privato</td></tr>
	</tbody>
</table>

La parte privata della classe base è <u>inaccessibile</u> alla classe derivata. Usiamo i metodi pubblici della base.
Possiamo usare la marcatura `protected` che da accessibilità alla derivata. Da usare limitatamente per non violare information hiding.

Derivazione 
- pubblica -> ereditarietà di tipo
- privata -> ereditarietà di implementazione
- protetta

Gerarchia di classi, se continuiamo ad ereditare da classi derivate, si arrivano a sottotipi diretti e indiretti.

Quando lo usiamo?
1) Estensione (data<:orario)
2) Specializzazione (qbutton<:qcomponent)
3) Ridefinizione (queue<:list)
4) Riuso di codice, non è subtyping

Differenza ereditarietà privata e composizione
- ered. privata può introdurre ere. multipla (problematica) non necessaria
- ered. privata permette alla derivata di convertire puntatore della classe derivata a quella della base
- ered. privata permette l'accesso alla parte privata della base
### Eredità di Tipo
Relazione *is-a*, sotto-tipaggio.
``` c++
class dataora:public orario {
private:
	int giorno;
	int mese;
	int anno;
}

enum giorno {"lun","mar","mer","gio","ven","sab","dom"=0};
// tipo enum definito da utente, lista finita

class dataorasett:public dataora {
public:
	giorno GiornoSett() const;
private:
	giorno giornoSett;
}
```

Questa relazione induce il *subtyping* (o subsumption).
B sono supertipo e D sottotipo, ovvero le funzioni che operano sul supertipo funzionano sui sottotipo. C'è conversione di tipo.

D => B estrae il sottooggetto
D* => B*$\qquad$D& => B&$\quad$ sono puntatori e riferimenti *polimorfi*. 
**Tipo dinamico**, tipo effettivo dell'oggetto puntato in un certo istante. Il compilatore conosce solo tipi statici.

Si possono fare `static_cast` tra puntatori e riferimenti polimorfi ma è può essere una operazione "pericolosa".
``` c++
class C {
public:
	int x;
	void f() {x=4;}
};
class D: public C {
public:
	double x;
}
```

Ereditarietà: le amicizie non si ereditano!
Dobbiamo nuovamente concedere le amicizie necessarie.

La parte protected è accessibile solo dalla derivata.
``` c++
class B {
protected:
	int i;
	void protected_printB() const {cout << ' ' << i;}
public:
	void printB() const {cout << ' ' << i;}
};
class D: public B {
public:
	. . .
	void stampa() const {
		cout << i << ' ' << z; // OK
	}
	static void stampa(const B& b, const D& d) {
		// cout << ' ' << b.i; ILLEGALE
		b.printB(); // OK
		// b.protected_printB(); ILLEGALE
		
		cout << ' ' << d.i;
		d.printB();
		d.protected_printB();
	}
};
```

Si può voler fare la ridefinizione dei metodi (usare lo stesso nominativo).

**Name hiding rule**
Se nella classe derivata D c'è una ridefinizione di un metodo `m()` nasconde sempre tutte le versioni sovraccaricate di `m()` disponibile in B, anche nel metodo ridefinito. Se le si vogliono accedere, si deve usare l'operatore di scoping `B::`.

E' possibile fare anche la ridefinizione dei campi.

**Costruttori, distruttori e assegnazioni**
I costruttori delle classi derivate devono costruire anche i sottooggetti; se non costruito, usa il costruttore di default del sottooggetto (deve essere disponibile).
``` c++
dataora::dataora() : giorno(1), mese(1), anno(2000) {}

dataora::dataora(int a, int me, int g, int o, int m, int s) : orario(o,m,s), giorno(g), mese(me), anno(a) {}
```

*Costruttore di copia*
Se non definito, usa la costruzione di copia standard.
Con la ridefinizione se non vengono usati i parametri, usa il costruttore di default (warning).

Operatore di assegnazione
Assegnamento con comportamento standard
``` c++
D& operator=(const D& x) {
	this->B::operator=(x); // assegnazione per sottooggetto
	z = x.z;
}
```

Distruttore funziona come i distruttori normali quindi, distrugge gli oggetti in modo inverso della costruzione.

9### Binding dinamico
*Static binding* nell'invocazione di metodi
``` c++
class Base {
	int x;
public:
	void f() {x=2;}
};
class Derivata: public Base {
	int y;
public:
	void f() {Base::f(); y=3;} // ridefinizione
};
int main() {
	Base b; Derivata d;
	Base* p=&b;
	p->f(); // Base::f()
	p=&d;
	p->f(); // cosa invoca?? Base::f()
}
```
Vorremo usare la versione della funzione `f()` della derivata, comportamento polimorfo.

*Dinamic binding* detto anche Late binding o Dinamic Lookup.
``` c++
class orario {
	. . .
	virtual void Stampa() const; // metodo virtuale
};

void G(const orario& o) {
	o.Stampa(); // chiamata polimorfa
}
```
Una classe con metodi virtuali (anche ereditati), si dice polimorfa o astratta.
Una funzione virtuale è detto contratto polimorfo. Tutti i metodi di Java sono virtuali.

``` c++
// OVERRIDING
class dataora : public orario {
	. . .
	void Stampa() const override; // opzione 1, preferibile
};
class dataora : public orario {
	. . .
	virtual void Stampa() const; // opzione 2, non distingue il overriding con il metodo virtuale base
};
class dataora : public orario {
	. . .
	void Stampa() const; // opzione 3, non esplicita che è metodo polimorfo
};
```
Per esserci un override, la segnatura della funzione deve essere *identica*.
La sua sola eccezione è con il return di *tipi covarianti*, ovvero di sottotipi del tipo della segnatura principale.

I valori di default fanno parte della segnatura e non devo metterli nell'override ma i parametri sì.

Overhead del late binding può arrivare anche fino al 50% del dispatch del programma.
Ormai con i progressi delle CPU, le prestazioni sono migliorate, soprattutto grazie al branch prediction.
Ogni classe ha una vptr (virtual pointer) che punta al Virtual method table, contenente tutti i metodi virtuali che puntano alle funzioni.

**Distruzione polimorfa (virtuale)**
E' importante tenere conto che se distruggiamo un oggetto derivato puntato da un puntatore di tipo base, il compilatore usa il distruttore della classe base.
Dobbiamo segnare virtual il distruttore base e override quelle derivate. Anche quando basta il distruttore base, è buona prassi comunque definire quelle override come `~D()= default;`.

Una classe con tutti metodi virtuali puri `virtual metodo() =0;` sono usati come dichiarativa di progettazione del tipo.
#### Run-time type information (RTTI)
Gli operatori di RTTI sono il `typeid` e il `dynamic_cast`.

Il typeid ha come argomento una espressione o tipo qualsiasi e ritorna un oggetto della classe type_info. 
``` c++
// typeinfo.h
class type_info {
private:
	type_info();
	type_info(const type_info&);
	type_info& operator=(const type_info&);
public:
	bool operator==(const type_info&) const;
	bool operator!=(const type_info&) const;
	const char* name() const;
};
```
La definizione della classe type_info è nel file header typeinfo.
Si usa per 
``` c++
#include <typeinfo>
. . .
int main() {
	int i=5;
	typeid(i).name(); // stampa int
}
```

**Upcasting e Downcasting**
Quando abbiamo un un puntatore di tipo che punta a un suo sottotipo, si può voler specializzare il puntatore (downcast).
``` c++
// B* => D*
dynamic_cast<D*>(p) != nullptr // TD(p) <= D*
```
Con `B& => D&` non viene solitamente usata perché mancano di un nullptr e devono usare `try-catch` eccezioni.
``` c++
// B <= D <= E
int main() {
	B* p = fun();
	if(dynamic_cast<D*>(p)) // downcast possibile
		(static_cast<D*>(p))->f();
}
```
Il dynamic_cast ha un costo run-time, meglio usare static_cast quando possibile.

Molti evitano il downcast perché lo ritengono un difetto di design. Infatti è poco estensibile nel caso ci siano modifiche delle classi.
- usare il downcast *solo quando è necessario*
- non fare type checking inutile
- ove possibile usare metodi virtuali

**Clone (or prototype) pattern**
Possiamo voler avere un costruttore di copia polimorfa, tuttavia il costruttore non può essere messo virtuale. Dobbiamo creare noi stessi il metodo.
``` c++
class clonable {
public:
	virtual ~clonable() = default;
	virtual clonable* clone() const = 0;
};

class Base : public clonable {
public:
	virtual Base* clone() const override {
		return new Base(*this);
	}
};
```

**5 principi della programmagione ad oggetti**
S.O.L.I.D.
- *Single responsibility principle*
  un tipo dovrebbe avere una singola responsabilità
- *Open/Closed principle*
  aperti per le estensioni ma chiusi per le modifiche
- *Liskov substitution principle* (di Barbara Liskov)
  possibilità di rimpiazzare un oggetto con i suoi sottotipi senza alterare la correttezza del programma
- *Interface segregation principle*
  è preferibile avere tante interfacce specifiche che una singola interfaccia general-purpose
- *Depency inversion principle*
  astrazioni non devono dipendere dai dettagli

-> Mantenibilità e estensibilità
### Ereditarietà multiple
Controversiale perché aumenta molto la complessità e soffre del problema del diamante. 

C'è un problema di ambiguità la quale per metodi con la stessa segnatura ereditati da D1 e D2 invocato su E, il compilatore non sa quale usare.
Per risolverlo si usa l'operatore di scoping oppure una ridefinizione in E del metodo.

**Problema del diamante**
![](img/Pasted%20image%2020241127175249.png)
Dentro E ci sono i sottooggetti D1 e D2 che hanno a loro stessi un sottooggetto B che è quindi duplicato in E.
``` c++
class B {
	int b;
	void print() { cout<< b; }
};
class D1 : public B {
	D1() : B(2) {}
};
class D2 : public B {
	D2() : B(3) {}
};
class E : public D1, public D2 { ... };

int main() {
	E* e;
	e->print(); // 2 o 3? Non definibile, ambiguo.
}
```
Causa problemi di ambiguità.

Soluzione: un unico sottooggetto A in ogni oggetto della classe D che chiude il diamante.
-> Derivazione virtuale
``` c++
class B { ... };
class D1 : virtual public B { ... };
class D2 : virtual public B { ... };
class E : public D1, public D2 { ... };
```
D1 e D2 non hanno un sottooggetto B ma un puntatore alla base virtuale B. E' E a costruire il sottooggetto B.

*Unique final overrider rule*
Quando chiudo un diamante con più metodi polimorfiche (virtuali e override), sono obbligato a fare un override finale unico.

La derivazione pubblica prevale su quella protetta che prevale su quella privata.

Ordine di costruzione di E
1. vengono richiamati, una sola volta, i costruttori delle basi virtuali (left-to-right, top-down)
2. vengono richiamati i costruttori delle superclassi derivate non virtuali

## Gerarchia di Input/Output
Gerarchia di classi per l'I/O
![](img/Pasted%20image%2020241202144449.png)

Stream = sequenza non limitata di celle ciascuna contenente un byte.
- bidirezionali, input e output.
- la posizione di una celle nello stream è indicizzata e parte da 0
- I/O effettivo avviene tramite un buffer associato allo stream
- deve gestire end-of-file

Lo stato dello stream è un tipo standard iostate, rappresentato da un attributo `std::ios` che può assumere il valore bad, fall, eof

ios è una *classe astratta* "virtuale" e polimorfa che permette di controllare lo stato di funzionament di uno stream.
``` c++
class ios: public ios_base {
public:
	enum iostate {good=000, bad=001, eof=010, fail=101};
}
```

iostream include l'overloading dell'operatore di input `operator>>` per i tipi primitivi e gli array di caratteri *passati per riferimento*. operator>> di char e stringa sono definiti esterni dalla classe.
``` c++
class istream: public virtual ios {
public:
	istream operator>>(bool&);
	istream operator>>(int&);
	istream operator>>(double&);
};

istream& std::operator>>(istream&, char&); // byte
istream& std::operator>>(istream&, char*); // stringhe
```
Tutti gli operatori di input ignorano le spaziature presenti prima del valore da prelevare. Nel caso ci sia un fail, non viene effettuato il prelievo.
Fare overloading di operator>> significa definire un algoritmo di parsing di una sequenza di byte.

iostream include l'overloading dell'operatore di input `operator<<` per i tipi primitivi e gli array di caratteri *passati per valore*. operator>> di char e stringa costante sono definiti esterni dalla classe.

I/O testuale converte da stream a testo e viceversa. Ci sono anche quelli binario/unformatted senza interpretazione.

``` c++
ifstream(const char* nomefile, int modalita=ios::in)
ofstream(const char* nomefile, int modalita=ios::out)
fstream(const char* nomefile, int modalita=ios::in | ios::out)
```
E' buona prassi usare la classe che risolve specificamente i nostri bisogni.

## Gestione di eccezioni
Le eccezioni sono gestite dall'exception handler. 
Il C non ha le eccezioni e dobbiamo quindi usare una variabile aggiuntiva per sapere se le funzioni hanno avuto buon esito.

In C++ sono opzionali. 
La funzione in cui si verifica la situazione eccezionale solleva una eccezione con `throw`.
``` c++
class Ecc_Vuota {}; // classe di eccezione

telefonata bolletta::Estrai_Una() {
	if(Vuota()) throw Ecc_Vuota(); // costruttore vuoto
	...
}

int main() {
	...
	try { b.Estrai_Una(); }
	catch(Ecc_Vuota e) {
		cerr << "La bolletta è vuota" << endl;
		abort(); // definita in stdlib.h, terminazione abnormale di programma
	}
}
```
Una throw non seguita da una funzione, rilancia l'eccezione al chiamante.

Per differenziare le diverse eccezioni si dovrebbero creare tante classi quante le diverse eccezioni. Allora si può usare un enum.
``` c++
enum Errori {ErrSintassi, ErrFineFile, ErrVuoto};
```

Flusso provocato da una throw
1) Se l'espressione throw è nel corpo stesso della funzione F collocata nel blocco try, l'esecuzione abbandona il blocco try e vengono eseguite le catch associate a tale blocco
2) Se si trova un type match per una catch, l'eccezione viene catturata e viene eseguito il codice della catch. Al termine dell'esecuzione del corpo del catch, l'esecuzione passa al punto di programma che esegue l'ultimo blocco catch
3) Se non si trova un type match per una catch, oppure se l'istruzione throw non era collocata all'interno di un blocco try della stessa funzione F la ricerca continua nella funzione cje ja invocato la funzione F
4) Questa ricerca top-down sullo stack delle chiamate di funzioni continua fino a che si trova una catch che cattura l'eccezione o si trova alla funzione main nel qual caso viene richiamata la funzione di libreria terminate() che per default chiama la funzione abort().

Attenzione: dobbiamo fare attenzione alla gestione di garbage quando usiamo throw.
``` c++
gestore () try {
	risorsa rs;
	... // codice che può sollevare eccezioni
	rs.rilascio();
}catch (...) { // catch (...) generico, cattura tutto
	rs.rilascio();
	throw; // rilancio l'eccezione al chiamante
}
```

Match del tipo di eccezioni
La catch che cattura un'eccezione E è la prima catch incontrata durante la ricerca che abbia un tipo T compatibile con E.
- il tipo T è uguale al tipo E
- il tipo T è un sottotipo di E

Quando facciamo catch di tipi polimorfi, l'ordine è importante: dobbiamo fare le catch delle sottoclassi prima delle superclassi.

Qt non usa eccezioni. 
Il C++ standard prevede una gerarchia di classi di eccezioni predefinita. La base è `exception`.

Critica delle eccezioni: Tony Hoare dice che le eccezioni sono pericolose, dobbiamo gestirle bene.

## C++ 11
#### Inferenze di tipo
``` c++
vector< vector<int> >::const_iterator cit=v.begin(); // pre C++11
auto cit = v.begin(); // dopo C++11
```
auto, dichiarazioni di variabili senza specifica del loro tipo.
Rimane comunque importante conoscere il tipo per sapere come gestirla.

decltype, determina staticamente il tipo di espressioni.
``` c++
int x = 3;
decltype(x) y = 4;
```

**Inizializzazione uniforme aggregata con { }**
Possiamo inizializzare contenitori di basso o alto livello con valori iniziali.
``` c++
int* a = new int[3] {1,2,0};

std::vector<string> vs = {"first", "second", "three"};
```

=default, dichiariamo esplicitamente che usiamo i metodi di default della classe
``` c++
class A {
public:
	A(int) {}
	A() = default;         // costruttore altrimenti non disponibile
	virtual ~A() = default; // distruttore virtuale
}
```

=delete, per non rendere disponibile una cosa che sarebbe disponibile altrimenti
``` c++
class B {
public:
	B& operator=(const B&) = delete;
	B(const B&) = delete;
}
```

`override`, marchiamo esplicitamente l'override di un tipo virtuale

`final`, proibisce alle classi derivate di effettuare overriding
permette di liberare il dinamic binding del compilatore da ora in poi

`nullptr`, sostituisce la macro NULL e il valore 0
è convertibile implicitamente a qualsiasi tipo puntatore e bool

chiamate di costruttori dentro costruttori
meccanismo chiamato *delegation*
è solitamente equivalente ai valori di default ma evade dall'obbligo per cui se un argomento precedente è di default allora lo devono essere tutti i suoi successivi

range based loop
``` c++
std::vector<int> v = (0,1,2,3,4,5);

for(int& i : v)
	std::cout << ++i << ' ';

for()
```

### Funtore
Un funtore è un oggetto di una classe che può essere trattato come una funzione (o puntatore a  funzione).
E' realizzato con l'overloading del metodo di chiamata di funzione `operator()`.
``` c++
class Functor {
private:
	int x;
public:
	Functor(int n): x(n) {}
	int opetator() (int y) const {
		return x+y;
	}
};

int main() {
	Functor sommaCinque(5);
	int z = sommaCinque(4); // z=9
}
```
Questo è interessante perché ci lascia passare una funzione come argomento di un'altra funzione.

``` c++
// template <class UnaryFunction>
std::transform

void fun(const vector<int>& v) {
	Functor f(2);
	// std::for_each(InputIterator first, InputIterator last, UnaryFunction f)
	std::for_each(v.begin(), v.last(), f);
}
```

#### Lambdas o closures
funtori definiti al momento, temporanei anonimi
``` c++
class C {
	...
	int f() const;
	int m(const vector<int>& v) const {
		int totale=0;
		int a=someClass::getSomeIntValue();
		std::for_each(v.begin(), v.end(), 
		// [capture list] (arguments) ->return-type { body }
		[&totale, a, this] (int x) { totale +=x*a*this->f(); }
		// this si può passare solo di valore
		)
	}
};
```
\[capture list] elenca la lista delle variabili della closure cioè variabili all'esterno della lambda usate come l-valore (lettura, scrittura) o r-valore (sola lettura) della lambda.

C++14
- auto come valore di ritorno della funzioen
C++17
- nested namespaces
- variable declaration in if

