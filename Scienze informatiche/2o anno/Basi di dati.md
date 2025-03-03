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
chiave esterna, vincoli tra relazioni

Ci sono due linguaggi
1. DDL (Data Definition Language), definizione dello schema
2. DML (Data Manipulation Language), interrogazione e aggiornamento

Operatori insiemistici
- *Unione $(\cup)$*
- *Intersezione $(\cap)$*
- *Differenza $(-)$*
devono avere lo stesso schema.

Altri operatori
*Ridenominazione (p)*,
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
   per risolvere il problema dei join non completi e la perdita di informazioni. Può  essere sinistro $(\bowtie_{\text{left}})$, destro $(\bowtie_{\text{right}})$ o completo $(\bowtie_{\text{full}})$ a seconda di quali tuple mantiene.
  
  Semi-join, restituisce le tuple che contribuiscono allo join
  Theta_join: $\sigma_{\text{condition}}(R_{1}\bowtie R_{2})\quad\Longleftrightarrow\quad R_{1}\bowtie_{\text{condition}}R_{2}$
  Equi-join è un theta-join con condizione di equivalenza