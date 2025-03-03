### 1. Overview
Strumento cross-platform (windows, mac, linux).
Usato per progettare i GUI.
Supporto per
- containers
- accesso SQL
- XML e JSON
Tutte le classi utilizzate devono essere incluse.

Dopo aver codificato il progetto
1. `> qmake -project` genera project file.
   da aggiungere QT += widgets
2. `> qmake` genera il makefile dal project file.
3. `> make` per generare l'eseguibile.
Passi 3 e/o 2 da riavviare alla modifica di file.

file in più .moc da ignorare.
### 2. Layout e strutture
1. Fissiamo un'idea e facciamo sketch del layout.
2. Lo sketch è fondamentale per visualizzare tutte le entità atomiche.
3. Separiamo lo sketch in rettangoli e individuiamo le posizioni, le dimensioni e come variano a seconda della modifica della finestra.
4. Pianifica il modello logico (classi, i suoi campi e le loro relazioni)
   UML (Unified Model Logic)
   - rettangoli sono classi
   - : rappresenta il tipo
   - - per privato, # protetti e + pubblico
   - frecce per l'ereditarietà
   - rombo per composizione
   - italics per virtuali e grassetto virtuale puro
5. Pianificare il widget GUI, questo dovrebbe dipendere dal modello
   Qt ha garbage collector per i suoi widgets.
6. Codifichiamo.
   I widget ereditano da QWidget e devono contenere la macro `Q_OBJECT`. Hanno il metodo show()
   I layout indicano come i widget vengono presentati. Nel costruttore dei widget, istanziamo un layout con this. Usiamo su esso un setAlignment().
   Nel metodo show() facciamo setText ai label. Non possiamo usare stringa c++ ma devo usare QString (concatena con +). 
   Alcuni metodi di visualizzazione immagine usano path locale es. ":assets/"
layout->AddStretch

Widgets
- organizzati ad albero
- relazione parent-child
- fatti con composizione
### 3. Behaviour
Associare una funzione ad una azione è un evento.
Sono detti signal in Qt. Un signal può attivare un altro signal. 
I segnali sono scritti come metodi ma non sono implementati. Sono passati come argomento della funzione connect ereditato da QWidget. 
``` c++
// connect(source_widget, signal, destination_widget, signal)
connect(source, &Sour::signal, this, &Dest::signal);
```
In caso di multipli segnali a uno stesso widget, non possiamo fare assunzioni sull'ordine dei segnali.
Non si possono connettere segnali a segnali con diversi argomenti.
### 4. Polimorfismo
Problema: vogliamo mostrare dettagli differenti dei diversi sottotipi.

Comuni e *sbagliati* metodi
- `string Character::getContent()`, non funziona quando Character ha campi che non sono stringhe
- `QWidget* Character::render()`, restituisce direttamente il widget del Character ma, accoppia il modello logico con l'interfaccia
  cattiva pratica perché fallisce quando: cambiamo framework, mostrare versioni diverse dello stesso oggetto, traduzione
- RTTI / dynamic_cast / typeid, funziona per gerarchie piccole che non cambiano con il tempo
  cattiva pratica: si deve ricordare dove è usata, multipli if il quale ordine importa, ereditarietà multipla è complessa, lento
- `string Character::getType()`, stessi problemi del RTTI più problemi di implementazione
  da *non usare mai* (da bocciatura)

Metodo corretto: usare classi di supporto
**Visitor**
- separare il modello logico con l'interfaccia
- espandere la classe dinamicamente
- error checking assistito dal compiler
- comune design pattern
ma costa più codice.

Visitor esegue azioni dipendentemente dal tipo concreto.
``` c++
void Hero::accept(CharacterVisitorInterface& visitor) {
	visitor.visitHero(*this);
}
```
Il modello logico può implementare questo metodo senza sapere com'è l'interfaccia.

``` c++
class CharacterInfoVisitor: public Game::CharacterVisitorInterface {
private:
	QWidget* widget;
public:
	QWidget* getWidget();
	void visitHero(Hero& hero);
	void visitMonster(Monster& monster);
}
```

RTTI, costo implementazione basso, costo mantenimento alto
visitor, costo implementazione alto, costo mantenimento basso

Vantaggi:
- completo separamento tra modello e GUI
- debugging fatto per sottoclassi
- può essere usato per motivi diversi
- visitor differente per layout/framework differenti
- hanno uno stato interno

Le informazioni visualizzate devono essere aggiornate.
Possiamo usare un metodo refresh che richiama la visualizzazione dell'oggetto. Però la chiamata del metodo refresh è manuale.
Per una chiamata automatica: **Observer**
``` c++

```
## Progetto
Progetto a gruppi di 2 o da soli
"Sviluppo di una biblioteca virtuale estesa" con Qt
Vincoli
1. non copiate
2. scritto interamente in C++
3. interfaccia grafica in Qt
4. compilare senza errori (macchina virtuale su moodle)
5. information hiding e incapsulamento
6. metodi parte tecnica separato da quella grafica (non viceversa)
7. eseguibile in modo efficiente e robusto
8. polimorfismo "non banale"
9. non utilizzare get_type nella scelta metodi
10. una classe astratta e almeno 3 classi concrete (5 se coppia)
11. CRUD+S, Create Read Updare Delete e Search
12. persistenza dei dati, esportabili in almeno un formato strutturato (json, xml)
13. salvataggio e caricamento con finestra di dialogo
14. quando uso CRUD+S, uso la stessa finestra
15. relazione in pdf
    matricola e nome
    descrizione del progetto
    commenti ai metodi CRUD+S
    descrizione sul polimorfismo
    descrizione metodo persistenza dati
    descrizione delle funzionalità aggiuntive
    contazione del numero di ore effettive
    se progetto di coppia, indicare chi ha fatto cosa e relazioni diverse
    ai progetti già consegnati, indicare modifiche

5 finestre di consegna con deadline alla data dello scritto
consegna moodle file e relazione
aggiunta di file esempio salvataggio
rispettare i vincoli per avere un voto sufficiente
rispettare distinzione ereditarietà e distinzione
usare make clean prima di mandare il progetto