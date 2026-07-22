---
layout: page
title: Appunti di Programmazione ad Oggetti
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
`dynamic_cast<T*>(p)` 
#### costruttori e distruttori
Costruttore di default chiama costruttori delle classi base.

Costruttore di copia standard chiama i costruttori di copia delle classi base, esistono anche quando non sono ridefinite.

Distruttori profondi gestiscono i campi puntatore della propria classe.

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

