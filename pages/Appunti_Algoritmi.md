---
layout: page
title: Appunti algoritmi e strutture dati
share: true
---
## Definizione

O grande
g(x) = O(f(x)) 

*Gerarchia di grandezza*
1. $$f\rightarrow0$$
2. costante
3. logaritmo 
4. radice e potenza frazionaria ($$\sqrt{n},\ n^{\frac{a}{b}}$$)
5. lineare (n)
6. potenza ($$n^{a}$$)
7. esponenziale ($$a^{n}$$)
8. super esponenziali ($$n^{n}$$)

*Max-heap* è un albero binario completo che ha ogni nodo minore dei suoi antenati e maggiore dei suoi discendenti.
Inserimento al prossimo nodo disponibile e max-heapify
Rimozione del'elemento e max-heapify

*Hoffmann* = max-heap in cui i parenti sono somma delle frequenze dei loro nodi figli. Le foglie sono i caratteri da codificare e il codice è ottenuto seguendo il percorso dalla foglia alla radice dove un ramo sinistro è 0 e quello destro è 1. La sua costruzione inizia con i caratteri dalla minore frequenza.

## Algoritmi
Correttezza?
- Analisi invarianti
### Algoritmo greedy
1. Scelta greedy
2. Risolvi il sotto-problema 
```
Sort(A)

```
### Algoritmo dinamico
Algoritmo Memoizzato, memorizza i risultati delle soluzioni

```
/* Inizializza con i casi base, 
 * gestire i casi ricorsivi 
 */

InitA (A)

RecA (A, i, j)
```