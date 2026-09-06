---
layout: page
title: Appunti di programmazione ad oggetti
share: true
---
Una carrellata di informazioni utili per l'appello di Programmazione ad Oggetti @unipd
### Cosa stampa
- `const T` vuole `const f()`
- classe dinamica deve avere `f()` chiamata
- costruttore di copia su T con eredità virtuale PPc P Tc
- `delete` se `~` non virtuale, solo `~` della classe dinamica
- chiamata `f1()` in `f()` di classe T, priorità `f1()` in T (se non virtual)
- `T* p = new TD` non richiama costruttore di copia

### Funzioni
#### controllo di tipo 
`typeid(T)` per comparazioni
`dynamic_cast<T*>(p)` per cast dinamico, false quando non possibile
#### costruttori e distruttori
``` c++
class A {
private:
	int num;
};

class B : public virtual A {
private:
	std::string str;
public:
	B(int n) {this.num = n+1};
};

class C : public B {
private:
	Object* ref;
};

class D : public C {
private:
	vector<double>* v;
public:
	D();     // costruttore di default
	D(D& d); // costruttore di copia
	~D();    // distruttore
	D* clone() const;
};
```

Costruttore di default chiama costruttori delle classi base e non ha niente nel parametro.
``` c++
D() : A(0), C() {
	v = new vector<double>();
}
```

Per ridefinire un costruttore di copia standard si procede:
1) invocando il costruttore di copia della sua base virtuale
2) invocando il costruttore di copia delle sue superclassi DIRETTE e solo di quelle dirette. Sarebbe insensato chiamare le sue superclassi non dirette, visto che queste verranno già invocate dai costruttori di copia delle superclassi indirette
3) I campi dati dell'oggetto (non di quelli dei sottooggetti che sono costruiti dai vari costruttori di copia)

``` c++
D(D& d): A(d), C(d), v(d.v) {}
```

Distruttori profondi gestiscono i campi puntatore della propria classe.

Funzione di clonazione chiama il costruttore di copia su \*this;
``` c++
D* clone() const {
	return new D(*this);
}
```

### Altre informazioni utili

| `vector<T*> v`     | descrizione                               |
| ------------------ | ----------------------------------------- |
| push_back(const T) | aggiungere T al vettore                   |
| pop_back()         | rimuovere ultimo elemento                 |
| erase(iterator)    | rimuovere elemento puntato dell'iteratore |
| begin()            | iteratore iniziale                        |
| end()              | iteratore successivo alla fine            |
| empty()            | check se il vettore è vuoto               |
| size()             | grandezza del vettore                     |

