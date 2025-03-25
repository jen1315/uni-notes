*dato*: immediatamente presente alla conoscenza, prima di ogni elaborazione
*informazione*: notizia o elemento che consente di avere conoscenza di fatti, situazioni e modi di essere
I dati codificano le informazioni.

> Una base di dati è un insieme organizzato, persistente e condiviso di dati utilizzati per lo svolgimento delle attività <u>automatizzate</u> dell'organizzazione.

- grandi, il limite è quello fisico dei dispositivi
- persistente, indipendente dalle singole esecuzioni dei programmi
- condivise, diverse applicazioni e utenti accedono a una porzione (sovrapponibile) dei dati. 
	Può riportare alcuni problemi quali rindondanza, incoerenza (versioni non coincidono) e privacy (gestione accesso a dati autorizzati)
	Risolvibili con meccanismi di autorizzazione, controllo della concorrenza e uso di lock e semafori

I basi di dati sono gestiti da **DBMS (Data Management System)**
- privacy, si possono definire meccanismi di autorizzazione
- affidabilità, resistenza a malfulzionamenti hardware e software
	-> gestione delle *transazioni*, l'insieme di operazioni indivisibili e corretti anzhe in presenza di concorrenza  e effetti definitivi
- efficienza
- efficacia, rendere produttive le attività dei loro utilizzatori

## Modello Relazionale
Modello dei dati = insieme di construtti utilizzati per organizzare i dati e descriverne la dinamica
Usiamo il *modello relazionale*.

L'insieme $D_{1}\times...\times D_{n}$ è relazione matematica
$\begin{array}{ccccc}\text{Partite}\subseteq&\text{string}\times&\text{string}\times&\text{int}\times&\text{int}\\&\text{Juve}&\text{Lazio}&3&1\\&\text{Lazio}&\text{Milan}&2&0\end{array}$
1. nessun ordine delle n-uple
2. n-uple distinte
3. ogni n-upla è ordinata: l'i-esimo valore proviene dall'i-esimo dominio

La relazione in basi di dati è simile a quella matematica ma non è posizionale (3.); ogni dominio/colonna è associato a un nome unico (*attributo*)

I riferimenti fra dati in relazioni diverse sono per valore.
$R(A_{1},...A_{n})$ relazione R su attributi $A_{1},...,A_{n}$
$R=\{R_{1}(X_{1}),...,R_{k}(X_{k})\}$ schema di base di dati, ovvero insieme di relazioni

`null` per valore sconosciuto, inesistente o senza informazione

chiave primaria
chiave esterna, vincolo di integrità relazionale

Operatori insiemistici
- *Unione $(\cup)$*
- *Intersezione $(\cap)$*
- *Differenza $(-)$*
devono avere lo stesso schema.

Altri operatori
*Ridenominazione* (p),
  modifica lo schema lasciando inalterate le istanze

*Selezione $(\sigma)$*, 
  decomposizione orizzontale: ottengo un sottoinsieme delle tuple che soddisfano una condizione

*Proiezione $(\pi)$*, 
  decomposizione verticale: restituisce relazione con una parte di attributi
  sottoinsieme delle tuple (eliminazione duplicati)

*Join $(\bowtie)$*,
  prodotto cartesiano tra relazioni mantenendo quelli con valori uguali su attributi uguali. Può risultare completo, non completo, vuoto o nxm (prodotto cartesiano).
  In generale $0\leq|R_{1}\bowtie R_{2}|\leq|R_{1}|\times|R_{2}|$
  
  Join esterno,
   mette null in attributi quando non ha un relativo nell'altra tabella. Può essere sinistro $(\bowtie_{\text{left}})$, destro $(\bowtie_{\text{right}})$ o completo $(\bowtie_{\text{full}})$ a seconda di quali tuple mantiene. Risolve il problema dei join non completi e la perdita di informazioni.
  
  *Semi-join*, restituisce le tuple che contribuiscono allo join
  *Theta_join*: $\sigma_{\text{condition}}(R_{1}\bowtie R_{2})\quad\Longleftrightarrow\quad R_{1}\bowtie_{\text{condition}}R_{2}$
  Equi-join è un theta-join con condizione di equivalenza

In algebra relazione, due espressioni sono equivalenti se producono lo stesso risultato per qualunque istanza delle relazioni della base di dati. Il DBMS cerca sempre di eseguire espressioni equivalenti ma più efficienti.
1. $\sigma_{\text{C1 and C1}}(R)\equiv\sigma_{C1}\sigma_{C2}(R)$
2. $\pi_{X}(\pi_{XY}(R))\equiv\pi_{X}(R)$
3. $\sigma_{C1}(R_{1}\bowtie R_{2})\equiv R_{1}\bowtie\sigma_{C1}(R_{2})$
   se C1 condizione su $X_{2}$
4. $\pi_{X_{1}Y_{2}}(R_{1}\bowtie R_{2})\equiv\pi_{X_{1}Y_{2}}(R_{1}\bowtie\pi_{Y_{2}}(R_{2}))$
   se $X_{2}-Y_{2}$ non coinvolti dal join
5. $\sigma_{C}(R_{1}\bowtie R_{2})\equiv R_{1}\bowtie_{C}R_{2}$
6. $\sigma_C(R_{1}\cup R_{2})\equiv\sigma_{C}(R_{1})\cup\sigma_{C}(R_{2})$
7. $\sigma_{C}(R_{1}-R_{2})\equiv\sigma_{C}(R_{1})-\sigma_{C}(R_{2})$

**Viste (relazioni derivati)**
Rappresentazioni diverse per gli stessi dati. Non hanno contenuto autonomo ma si basano sulle relazioni di base. Vengono usati per mascherando informazioni in base ai diversi utenti o per semplificare la scrittura di interrogazioni complesse.

Possono essere di due tipi
- viste materializzate sono salvate su disco
  contro: rindondanti, da aggiornare se la relazione base è modificata, non sempre offerto
- relazioni virtuali sono salvate in cache
  una interrogazione su essa viene eseguita "ricalcolando" la vista
Non influenzano l'efficienza.

Si possono riversare i cambiamenti dalle viste alle relazioni base solo in caso di join completo.

### SQL
Ci sono due linguaggi
1. DDL (Data Definition Language), definizione dello schema
2. DML (Data Manipulation Language), interrogazione e aggiornamento

**DDL**
Definisce lo schema di relazione e crea un'istanza vuota. 
Specifica attributi, domini e vincoli.
``` sql
CREATE TABLE NomeTabella (
	Id VARCHAR(6) PRIMARY KEY,
	A CHAR(10),
	B NUMERIC(9) DEFAULT 0,
	Ref VARCHAR(6),
	UNIQUE(A,B),
	FOREIGN KEY(Ref) 
		REFERENCES Tab2(Id) ON DELETE CASCADE
)
```

*Politiche di reazione* su delete/update
- cascade, monodirezionale
- set null
- set default
- no action

Vincoli di CHECK(condizione)

**DML**
- modifica: INSERT, DELETE, UPDATE
- interrogazione: SELECT

``` sql
INSERT INTO NomeTabella(attr1,attr2,...)
	VALUES(val1,val2,...)

DELETE FROM NomeTabella
	WHERE condizione /* senza condizione, tutto viene cancellato */

UPDATE NomeTabella
	SET attributo = espressione
	WHERE condizione
```

Condizione LIKE
\_ qualsiasi carattere
% qualsiasi sequenza anche vuota

Operatori aggregati COUNT, MIN, MAX, AVG, SUM
spesso usati con GROUP BY

``` sql
CREATE VIEW NomeVista[(ListaAttributi)]
AS SELECT ... FROM ...
```
*Viste* che possono essere usate come tabelle. Vengono ricalcolate ogni volta.
Aggiornamenti sulle viste sono possibili se fanno riferimento a una sola relazione.

Controllo dell'accesso
Il creatore ha tutti i privilegi su di essa: INSERT, UPDATE, DELETE, SELECT, REFERENCES, USAGE

CREATE VIEW Stadi_Italia(NomeStadio, NumeroPartite) AS
SELECT NomeStadio, COUNT(\*)
FROM Incontro
WHERE Squadra1='Italia' OR Squadra2='Italia'
GROUP BY NomeStadio

SELECT Citta
FROM Stadi_Italia, Stadio
WHERE Nome=NomeStadio AND NumeroPartite = (SELECT MAX(NumeroPartite)
	FROM Stadi_Italia)

CREATE VIEW SpeseCitt(Cittadinanza, SpeseTotali) AS
SELECT Cittadinanza, SUM(Costo)
FROM Viaggio
JOIN (SELECT CodViaggio, Cittadinanza
	FROM Effettua
	JOIN Cliente ON Effettua.CF=Cliente.CF) AS a
ON Viaggio.CodViaggio=a.CodViaggio
GROUP BY Cittadinanza

SELECT Cittadinanza, MAX(SpeseTotali)
FROM SpeseCitt

CREATE VIEW Viaggi_G(CF, NViaggi) AS
SELECT CF, COUNT(\*)
FROM Viaggio, Effettua
WHERE Viaggio.CodViaggio=Effettua.CodViaggio AND Paese='Giappone'
GROUP BY CF

SELECT CF
FROM Viaggi_G
WHERE NViaggi = (SELECT MAX(NViaggi)
	FROM Viaggi_G)

CREATE VIEW X(Paese, Cittadinanza, CostoMedio) AS
SELECT Paese, Cittadinanza, AVG(Costo)
FROM Viaggio, Effettua, Cliente
WHERE Viaggio.CodViaggio=Effettua.CodViaggio AND Viaggio.CF=Cliente.CF
GROUP BY Paese, Cittadinanza

CREATE VIEW Y(Paese, CostoMedioMax) AS
SELECT Paese, MAX(CostoMedio)
FROM X
GROUP BY Paese

SELECT Paese, Cittadinanza
FROM X JOIN Y ON X.Paese=Y.Paese
WHERE CostoMedio = CostoMedioMax

## Metodologie e modelli per il progetto di una base di dati

Parte del ciclo di vita dei Sistemi Informativi
1. Studio di fattibilità
2. ==Raccolta e analisi dei requisiti==
3. ==Progettazione==
4. ==Realizzazione==
5. Validazione e collaudo
6. Funzionamento
Ad ogni passo è possibile tornare indietro

In questo corso ci soffermeremo nei punti 2. 3. 4. per una base di dati.
### Modello Entity-Relationship
Detto anche Entità-Relazione. E' il modello concettuale per base di dati più diffuso.

| Costrutti                                                                                 |                                              |
| ----------------------------------------------------------------------------------------- | -------------------------------------------- |
| Entità                                                                                    | ![](img/Pasted%20image%2020250324144615.png) |
| Attributo                                                                                 | ![](img/Pasted%20image%2020250324150551.png) |
| Relazione<br>sostantivi invece di verbi,<br>non hanno direzione                           | ![](img/Pasted%20image%2020250324144647.png) |
| Cardinalità<br>(min occorrenze, max occorrenze)<br>possibile associare anche ad attributi | ![](img/Pasted%20image%2020250324153331.png) |
| Identificatore<br>interno o esterno (cardinalità deve essere (1,1))                       | ![](img/Pasted%20image%2020250324154000.png)     |
| Generalizzazione                                                                          |                                              |

Nello schema concettuale rappresenriamo le entità e non le singole istanze.