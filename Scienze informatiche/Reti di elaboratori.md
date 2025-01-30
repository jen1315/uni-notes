“Computer Networks”, Andrew Tanenbaum, 2017

Rete: ogni qual volta che c’è un grafo sottostante

Classificazione di reti
- tipo, il loro uso
- tipo di trasmissione
- mezzo di trasmissione
- taglia
- topologia

**Client-Server Applications**
Molteplici clienti si connettono a un server

**Peer-to-Peer (P2P)**
Dispositivi si connettono tra di loro

Grandezza reti (taglia)
… > WAN (Wide Area Network) > 
MAN (Metropolitan Area Network) > 
LAN (Local Area Network) > 
PAN (Personal Area Network) > …

7 forme della rete
- point-to-point
- star
- ring
- mesh
- tree
- ibrida / gerarchica

Virtualizzazione:
la macchina virtuale non conosce gli altri livelli (non può quindi comunicarvi)

Standard Internet sono formulati da
RFC(Request For Comments), 
IETF(Internet Engineering Task Force)

Un protocollo rete simula quello umano.

Strati di sistemi di rete
Addressing
Error Control
Flow Control
Multiplexing, multitasking ovvero più comunicazioni simultanee
Routing, decidere strada migliore

```
*——————-*                  *——————-*
| Layer | <- protocollo -> | Layer |
*——————-*                  *——————-*
   |                           |
servizio                   servizio
   |                           |
*——————-*                  *——————-*
| Layer | <- protocollo -> | Layer |
*——————-*                  *——————-*
   |                           |
 . . .                       . . .
   |                           |
 *————————————————————————-——————-*
 |          Strato Fisico         |
 *———————————————————————————-————*
```

### OSI e TCP/IP
**OSI**
(Open Systems Interconnection)
Prodotto dall’ISO (International Standards Organisation)

1. *Physical*
2. *Data link*, incapsula le unità di informazione da trasmettere. Trova gli errori di trasmissione.
3. *Network*, consegna dei pacchetti, routing
4. *Transport*
5. *Session*
6. *Presentation*, visualizzazione dati
7. *Application*

**TCP / IP**
Retroattivamente vedendo cosa c’è già in internet

| OSI          | TCP / IP        | Modello ibrido |
| ------------ | --------------- | -------------- |
| Application  | Application     | Application    |
| Presentation | X               | X              |
| Session      | X               | X              |
| Transport    | Transport       | Transport      |
| Network      | Internet        | Internet       |
| Data link    | Host-to-network | Data link      |
| Physical     |                 | Physical       |

OSI era troppo complesso (7 livelli) e non ha preso piede. Ora il modello usato è quello ibrido.

## Strato Fisico

Tipo di trasmissione
### Connessione cablata
**coppia annodata**
I cavi sono intrecciati per limitare l’interferenza reciproca da campo magnetico (nell’incrocio le due correnti + e - parzialmente si annullano)
UTP (Unshielded Twisted Pair)

**cavo coassiale**
Il cavo è schermato, insulato e con conduttore a terra. Il filo è più grosso e la banda è più grande dell’UTP.

**fibra ottica**
Invece dell’elettricità passa la luce. C’è vetro inclinato che riflette la luce. Ci sono diversi tipi di luci e non esiste una migliore.

| Proprieties             | LED       | Laser               |
| ----------------------- | --------- | ------------------- |
| Data rate               | Low       | High                |
| Fibre type              | Multimode | Multi or singlemode |
| Distance                | Short     | Long                |
| Lifetime                | Long      | Short               |
| Temperature sensitivity | Minor     | Substantial         |
| Cost                    | Low       | Expensive           |
Contro: 
Ha difficoltà a passare per angoli, ad collegarsi con altri tipi di cavi ed è costosa.
Pro: 
Il filo è più piccolo e la banda è molto più grande degli altri tipi di fili. È da difficile da intercettare (“tap”). Per mantenere la luce si deve usare corrente elettrica. Unire o separare luci diverse è facile.

### Wireless
**Spettro elettromagnetico**

![[1.webp]]

Come vengono assegnate le frequenze?
- “Beauty contest” per chi fa del meglio
- Lotteria/asta per chi fa l’offerta migliore

Chi vince? Come facciamo a fare in modo che ci siano risorse per chi ne ha bisogno?
**Banda ISM** (Industrial, Scientific, Medical)
	è libera e distribuita lungo tutto lo spettro.

Esempi: Bluetooth, telecomando, forni a microonde, telefoni senza filo, reti 802.11

*Trasmissioni radio*
Omnidirezionale, non servono allineamenti tra il trasmettitore e il ricevente.
Sono a bassa frequenza e passano tutti gli ostacoli ma si dispergono per la lunga distanza.

Le trasmissioni sonar e pager sono a Hz inferiori di quelle radio.

Le frequenze richiedono il cambio di stato energetico alle cose che incontrano per procedere; quindi quelli da Hz bassi incontrano meno resistenza di quelli alti.

![[images.jpg]]
Tipi di frequenze radio
- AM, passano gli ostacoli, ma si dispergono più in fretta
	segue la superficie terrestre
- FM, non passano bene gli ostacoli, assorbite dalla pioggia
	rimbalzano dall'atmosfera terrestre

*Trasmissioni microonde*
Onde viaggiano quasi a linea retta e possono essere focalizzate per viaggiare distanze più lunghe. Rimbalzano su metalli e acqua, economiche.

Usata dal sistema telefonico e televisivo americano per comunicazioni a lunga distanza (grandi spazi vuoti). MCI (Microwave Communications Inc.)

*Trasmissioni infrarossi e millimetriche*
Direzionali e non passano oggetti solidi. Richiedono poca energia, economiche e sicure (porte infrarossi).

*Trasmissioni luminose*
Uso delle luci visibili. Ritornate in uso con i laser, ma vengono rovinate dalla pioggia e anche dal semplice vapore.

### Satelliti

| Satelliti            | Latenza | N coprire Terra |
| -------------------- | ------- | --------------- |
| GEO                  |         | 3               |
| upper Van Allen Belt | -       | -               |
| MEO                  |         | 10              |
| lower Van Allen Belt | -       | -               |
| LEO                  |         | 40+             |
![[Orbits.gif]]
Van Allen raggruppa l'energia dal sole che raggiunge la Terra.

Più basso è il satellite, più satelliti servono.
I tempi di latenza diminuiscono
La potenza richiesta richiesta diminuisce del quadrato e il loro lancio.

#### MEO
Satelliti in orbita media.
Il primo satellite, lo Sputnik (4 ottobre 1957) è una palla che ruota e ha lunghe antenne. Usa frequenze radio per mandare un audio in loop. Questo audio cambia per effetto Doppler.

- GPS (30 satelliti), tecnologia militare di NAVSTAR
	Non c'erano modi di navigazione tranne la bussola che sballa per cambi elettromagnetici. Per queste variazioni l'aereo civile call 007 dall'USA per la Corea segue una rotta diversa da quella pianificata e viene intercettata dai russi. Pressione pubblica rende il GPS pubblico.

I satelliti MEO si muovono, per usarli si deve capire dove si trovano (tempo di fix) e poi triangolare la posizione. 

A-GPS, viene istituito cosicchè un gestore telefonico tenga la posizione dei satelliti. Viene elimitano il tempo di fix.

#### GEO
Satelliti geostazionari in orbita alta.

![[download.jpg]]
max 180 satelliti, perché?
- interferenze dei coni di trasmissione
- problema di raggiungimento posizione orbita
Idea di Arthur Clarke nel 1945 (scrittore di fantascienza)

- Satelli spia
- Meteo
- Direct broadcast satellitare (televisione analogica e digitale)
	Banda Ku ad alta potenza
	Solo sopra l'equatore, mira il cono di trasmissione

#### LEO
Satelliti in orbita bassa.
IRIDIUM (77 pianificati, 66 effettivi)
- ogni satellite ha 48 celle mobili che coprono la terra
- telefono satellitare, mandano e ricevono dai satelliti
- banda di 2200 a 3800 (4kb)
Non ha successo (durato per 9 mesi), costi troppo alti, mercato troppo ampio, telefono troppo grosso.
Ora usato per Tsunami warning system.

Globastar (52 satelliti)
Satelliti ripetitori che mandano a stazione a terra. 
Economici ma poco duraturi. 
Nessuno li toglie: space debris (rottami spaziali)

![[Debris-LEO1280.jpg]]
(11 gennaio 2007) viene lanciato arma anti-satellite, 
satellite distrutto diventa
tanti frammenti (40 milioni) ad alta velocità 
-> la loro energia $E=mv^{2}$, ogniuna è piccola bomba

PROBLEMA: 
- satelliti in orbita sono in pericolo
- diventa difficile andare in spazio
- ci stiamo avvicinando al sindrome di Kessler (reazione a catena)

Cosa possiamo fare? Rottamare “ecologicamente”
- deviare l’orbita e farlo entrare all’atmosfera (si brucia)
	PERICOLOSO
- allontanati nell’**orbita graveyard**

Frammenti già presenti?
Detriti (>=10cm) devono essere tracciati ma, sono tantissimi e difficili da misurare
Ogni satellite viene allarmato di possibili collisioni; sono troppe.
Le si ignorano se si ritengono poco possibili.

Nel passato i satelliti erano una promessa del futuro perché la telecomunicazione terrestre era in mano ai monopoli.
1984, **Revised Telecommunication Act** dagli USA
Fibra+Wireless vince sui satelliti.

Satellite ancora usato per zone senza campo, per la tv e GPS.
Satellite funziona molto bene per il broadcasting, ovvero mono-direzionali.

SpaceX Starlink (2019)
Orbita LEO bassa.
Tantissimi satelliti a basso costo (6426 satelliti, 55 non funzionanti)
46% della popolazione non è collegata ad internet, Starlink aiuta

#### Molniya e Tundra
Orbita ellittica con la Terra in uno dei suoi fuochi.
![](img/Pasted%20image%2020250131002745.png)
### Segnale
La potenzia del segnale è la velocità di oscillazione.
Misura fisica: **bandwidth**, capacità delle frequenze trasmissibili
Misura informatica: **data rate** (bit rate, baud rate, etc)

La potenza per creare frequenze cresce al quadrato.
C’è un limite di banda (limite della potenza) -> bandwidth

Per fare telecomunicazioni si deve simulare la realtà, *FOURIER*
Oscillazioni di energia a cerchio che si sommano
![[centered.jpeg]]
Solo l'onda sinusoidale esiste in natura.
Fourier ha una classifica di frequenze più importanti delle altre.

Problemi: un impulso energetico trasmesso da un mezzo subisce 
- attenuazione di potenza
- dispersione, cambia la forma delle armoniche
#### Attenuazione di potenza
es. attenuazione in decibel: $10\log_{10}(\text{PotenzaTrasmessa/PotenzaRicevuta})$
Il nostro udito attenua logaritmicamente.

L' attenuazione accade indipendentemente tra le diverse frequenza.

**Teorema di Nyquist**
Il data-rate massimo è $$2B\log_2L$$ - B è la grandezza di banda
- L sono i livelli del segnale usato
Nyquist non tiene conto del *rumore* di fondo.

**Teorema di Shannon (-Hartley)**
In cui si tiene conto del rumore.
$B\log_{2}(1+S/N)$

#### Dispersione della potenza
La dispersione cambia la forma delle armoniche.

Cosa possiamo fare?
limitiamo la grandezza della rete e usiamo ripetitori :(
-> *SOLITONI*
- "Wave of Traslation", 1834
- onda non soggetta di attenuazione e dispersione
- bidirezionale, quando due onde si scontrano, non accade nulla e continuano per la loro strada
- funzionano nelle fibre ottiche
10000km senza dispersione

da fare nella piscina: solitoni di Falaco con i buchi neri di Snells
### La Rete Mondiale

2 CAVI TRANS-ATLANTICI
Data-rate: 8 parole al minuto
Per evitare il caso di "Madman Whitehouse", vengono aggiunti ripetitori.
30 anni dopo, tutto il mondo viene collegato.
1892, Thomas Edison inventa il "duplex telegraph", connessione a due vie contemporanee
54 anni dopo, viene installato il TAT-1, primo cavo telefonico transatlantico
32 anni dopo, viene installato TAT-8, fibra ottica transatlantica con ripetitori ottici SHR (Self Healing Ring)
![[Untitled.png]]
#### La Seconda Grande Rete
Il telefono è inventato da Antonio Meucci (1849)
ottiene caveat perché brevetto costa troppo. American District Telegraph Co. gli ruba il caveat. Bell plagia il brevetto di Gray

Telefono
1. point-to-point, coppie di telefoni collegati
2. switching center, i centralini dove manualmente si devono collegare i fili
3. 
Il *Revised Telecommunication Act* distrugge il monopolio AT&T in 23 diverse compagnie in competizione l'una con l'altra.
Ogni nuova start-up ha diritto di essere inserito, ovvero gli è concesso l'utilizzo di una parte della rete esistente.

Il telefono è attualmente, tutto digitale tranne l'UTP all'ultimo miglio
Il modem serve per collegare il segnale digitale a quello analogico.

Le onde digitali hanno problemi di attenuazione e dispersione.
Possono essere create usando
- **DC** corrente continua, funziona bene a piccole distanze, es. batterie (Edison)
- **AC** corrente alternata, si trasporta bene per le lunghe distanze (Tesla)
AC prevale.

Come codifichiamo il segnale digitale?
- modulando in *ampliezza*
- modulando in *frequenza*
	detta frequency shift keying
- modulando in *fase*
	detta phase shift keying

**QPSK** (Quadrature Phase Shift Keying)
alfabeto di 4 simboli usando 4 sfasamenti tipicamente angoli simmetrici
bitrare è doppio del baudrate

Si potrebbero aumentare il numero di simboli ma così facendo, diventano poco distinguibili.
Allora combiniamo due tipi di modulazione: fase e ampliezza.
Vediamo il loro costellation diagram
![[3-s2.0-B9780323919234000045-f07-05-9780323919234.jpg]]
QAM-16: bitrate quadupro del baud (16)

In teoria i QAM ottimali sono quelli circolari, con massima distanza tra i simboli. Questi non si usano perché sono più difficili da generare e decodificare.
![[The-best-constellation-diagram-for-8-QAM-signal.png]]

>Il limite fisico (di Shannon) della linea telefonica è di 36000bps
>-> il meglio che il modem moderno può ottenere è 35kbps al secondo!!
>
>Questa banda è troppo bassa, come siamo riusciti ad aumentarla?

Filtramo il segnale togliendo i rumori inutili. Con la linea telefonica ci sono alcuni limiti di filtraggio, il limite è

Nel caso di un servizio digitale il limite fisico raddoppia (70kbps)
è possibile usare 64kbps! 
Ma lo standard è di 56kbps perché gli USA usano solo 7bit su 8.

Lo standard è asimmetrico.
V.90 (1998) 56k in download e 33.6k in upload

Il fax è utile per le immagini, ma non molto per il testo. In occidente non è quindi riuscito a prendere piede inizialmente.
In giappone con i loro ideogrammi però, il fax è perfetto per comunicazione testuale e grazie a questo riesce a prendere popolarità nel mondo.

Gruppo 3 impiega 6-15
- Standard: 200x100 dpi
- Fine: 200x200 dpi
- Superfine: 200x400 dpi
- Massima del gruppo 3: 400x400 dpi
V.27 (1998): 4800bps, PSK
V.29 (1988) QAM
V.17 (1991) TCM
V.34 (1994) si ritorna a QAM e linea telefonica e fax si unificano

> Se questi sono i limiti di tramissione come riusciamo ad arrivare ai MB?

La tv via cavo coassiale arrivava già a 10Mbps.
Il satellite poteva servire 50Mbps!
Le compagnie telefoniche devono pensare veloce per non perdere alla competizione.

Il vero problema ricade nell'ultimo miglio dove possiamo cambiare il tipo di cavo, ma il costo è ENORME
### xDSL
Rimuoviamo il filtraggio > nel DSL (Digital Subscriber Line) da 4000Hz si arriva a 1100000Hz!
Il filtro però è necessario per non distruggerci le orecchie:
-> si aggiunge uno *splitter* direttamente dentro il modem di casa.

Ogni splitter genere interferenze sulla linea. Limitiamo a un solo splitter

Però xDSL spesso continua ad essere lenta. Perché?
![[unnamed.gif]]

Frequency Division Multiplexing (FDM) per trasmettere dati a diverse abitazioni.

**ADSL (Asymmetric DSL)**
Da più spazio a downstream all'upstream.
![[Division-of-ADSL-bandwidth.png]]
Ma in un cavo UTP, due canali sono ingestibili: interferenza in una di questi, fa crollare metà la linea.
Si usano 246 canali, 1 per voce, 5 vuoti, 32 upstream e il resto downstream.
I 5 canali vuoti sono necessari per proteggere la telefonata dai rumori.

![[VDSL2_frequencies.png]]
Usiamo V.34

ADSL2+ usano banda doppia (2.2Mhz invece di 1.1Mhz) ma queste frequenze sono molto fragili, non ci sono molti vantaggi.
Ci sono varianti "all-digital" dove viene tolta la banda telefonica e i vuoti.

**VDSL**
Come l’ADSL, usando frequenze più alte.

VDSL (2001) QAM, 55Mb download, 3Mb upload
VDSL2 (2006) FDM, 200Mb download, 100Mb upload
VDSL (2011) FDM, 300Mb download, 100Mb upload

Nota: dipende sempre da quanto cavo UTP3 c’è. Con 3600m di cavo, VDSL diventa uguale a ADSL2

Che standard usiamo?
 Non facciamo una scelta -> *band plans*
![[Pasted image 20241030151120.png]]

Sbarazziamoci dell’ultimo miglio. Portiamo la fibra a casa.
Da FTTC (Fiber to the Cabinet) a FTTB (Fiber to the Basement), dentro a casa continua ad essere retro-compatibile.

FTTH (Fiber to the House), fibra arriva fino al tuo modem
GPON: 2.5Gb download, 1.2Gb upload
XG-PON: 10Gb download, 2.5Gb upload
(totali !! dipende da quanti la usano)

Il multiplexing con divisione di frequenza FDM è usata anche da telefono. 
esempio. 3 livelli
- group, 12 canali voce
- supergroup, x5
- mastergroup, x10
	può tenere 600 conversazioni!

Nella fibra, la FDM si chiama **WDM (Wavelength Division Multiplexing)**.
Gli encoder e decoder possono essere costruiti senza corrente (tecnologia passiva) e sono molto duraturi.

Un altro multiplexing è **TDM**, multiplexing **temporale**.
Trasmissione Round-Robin di tot. tempo per ogni canale.
Con il FDM si deve tenere conto del bandwidth, nel TDM si può procedere per sempre.

Satellite: ha problemi di potenza e interferenze
Usa QPSK.

Digitale terrestre usa QAM.
Ma il terreno provoca echi! I problemi di distorsione dipende dalla frequenza, usiamo FDM nello stesso modo dell’ADSL (un canale è composto da tantissimi sottocanali diversi)
Compressione MPEG2

Quando una rete si allarga, si aggiungono livelli (come i livelli della linea telefonica). Si usa lo **switching**.
*Circuit switching*, un collegamento fisico tra due dispositivi che si comunicano
delay iniziale

*Message switching*, lanciamo direttamente un messaggio finché non trova lo switch e poi si costruisce il percorso
store and

*Packet switching*, si divide il messaggio in multipli pacchetti di lunghezza massima prefissata. Vengono permesse trasmissioni delle parti in parallelo; pacchetti possono non arrivare in ordine o alcuni possono perdersi.

### Telefonia mobile
Europa (e Italia) sono alla meglio dell'USA!!

*Standardizzazione*: l'Europa stabilisce standard unico.
Gli USA con eccesso di liberalismo, hanno lasciato che ci fossero standard multipli, creando reti incompatibili.

Principio della *conoscenza tariffaria*
In Europa, i numeri mobili sono diversi da quelli fissi, sono calcolabili prima.
Negli USA non c'è distinzione -> il surplus è pagato dal possessore dal cellulare

In USA la telefonia fissa ha tariffe molto basse quindi la telefonia mobile ha difficoltà ad entrare in mercato. 
In Europa il contrario: monopoli in telefonia fissa con prezzi alti, telefonia mobile tariffe convenienti.

Tutta la telefonia mobile si basa sulla l'infrastruttura fissa del territorio (switching center).
0G, 1G, 2G, 3G, 4G

**0G: Analogica (1950 circa)**
- deriva dalle trasmissioni radio e si sono evolute in sistemi *Push To Talk* (walkie-talkie)
- un solo canale per ricevere e trasmettere, *half-duplex*
il sistema IMTS (1960)
- Improved Mobile Telephone System
- 2 frequenze
- aumenta il livello di privacy: non si sentono le comunicazioni degli altri
- super-trasmettitori ad alta potenza
  "celle" di centinaia di chilometri
- ma massimo di 23 canali nella banda 150-450Mhz, pochi utenti

**1G: Analogica (1982)**
- AMPS (Advanced Mobile Phone System) conosciuto in Italia come TACS (Total Access Communication System)
- le celle sono più piccole, 10-20km
- capacità più grande, più utenti
- diminuisce la potenza richiesta dai telefoni (meno batteria)
- celle creano molte interferenze tra loro
  -> separazione per frequenza -> MA capacità diminuisce! 

Francis Guthrie, coloratore di mappe politiche propone che tutte le mappe si possono colorare con 4 colori (1852).
*Teorema dei quattro colori* (1976), primo teorema dimostrato dal computer.
In 500 pagine dice che ogni mappa al mondo può essere suddivisa in 1936 casi e tutte queste possono essere colorate in 4 colori.

Abbandoniamo 3/4 della banda per risolvere la separazione in frequenza?
No, le città sono molto angolari quindi celle quadrate non funzionano.
Celle esagonali, 3 colori?
-> quando vanno in overload creano microcelle, si arrivano fino a 7 colori

Ogni cella ha uno switching center a cui il cellulare rimane collegato finché non ci si sposta in un'altra (*handoff*).
Uno switching center chiede alle celle vicine quanta potenza ricevono dal cellulare; alla cella con la potenza più grande viene assegnato il cellulare.
- hard handoff, la vecchia stazione "disconnette" il cellulare e la nuova la "riconnette".
	c'è lag, richiede 0.3ms
- soft handoff, la nuova stazione acquisisce il cellulare prima che la vecchia la lasci.
	il cellulare deve potersi collegare a due frequenze contemporaneamente, aumentano i costi e la potenza (1G e 2G non la gestiscono)
Tutto è centralizzato nello switching center; è collo di bottiglia.

**Proprietà tecniche 1G**
Ogni cella gestisce più utenti.
Abbiamo bisogno di multiplexing: si usa FDM per gestire 832 canali
Ogni canale è full-duplex
Molti canali sono usati per la gestione
-> solo 45 canali usabili per cella!

Ogni 15 minuti il cellulare manda di broadcast manda 32bit di numero seriale e 34bit di numero telefonico per registrarsi alla cella più vicina.
Quando si chiama c'è un canale unico condiviso per attivare la richiesta.
Quando si riceve una telefonata c'è un canale di paging condiviso al quale i cellulari controllano se 

#### 2G: Digitale
Standard: D-AMPS, GMS, CDMA
##### D-AMPS
(America) e PDC (Giappone) usano la stessa tecnologia 
- sono retrocompatibili con 1G
- 850Mhz bande AMPS in digitale a cui se ne aggiungono altre da 1850-1990Mhz
- date le frequenze più alte, le onde sono più strette e l'antenna diventa più piccola!
	L'antenna cieca registra un cambio di energia (frequenza), se l'antenna è troppo piccola, la variazione di energia non viene propriamente registrata
- Con il digitale ci sono tecniche di compressione del flusso. es da 56kbps a 8/4kbps!
	Sei volte gli utenti dell'AMPS
L'algoritmo nei dispositivi mobili si basano sull'efficienza energetica.
es. delta modulation, 1 quando l'onda sale e 0 quando scende
  si perde molta informazione (lossy)
La qualità del suono è peggiorata dal 2G.

**MAHO (Mobile Assisted HandOff)**
I cellulari stessi gestiscono l'handoff.
- i cellulari sono associati ad una cella e periodicamente monitora la qualità del rapporto
  Si sfruttano i "tempi morti" dovuti ai tempi morti per misurare la potenza del segnale
- ogni switch center ha una potenza fissata, al cellulare basta misurare la potenza in base a quella (tacche di segnale)
- quando il segnale è basso, il cellulare "protesta" con la base che lo "disconnette"
- il cellulare rimasto solo, si guarda in giro e riacquisisce il segnale più potente 
##### GSM
Global System for Mobile communication (Europa e Italia)
Introdotto dalla Finlandia.
- usa FDM e TDM
- i canali del GSM sono molto più ampli (200kHz rispetto ai 30kHz del D-AMPS)
- tengono più utenti e hanno un data-rate per utente più alto
- ogni canale gestisce 270833bps -> diviso in 8 utenti: 33.854kbps
  dopo correzione degli errori: 13kbps finali (meglio del D-AMPS di 8/4kbps)
- qualità voce molto migliore, così come trasmissione modem più decente
- esistono tipi di celle: macro, micro, pico e umbrella
  macro: le più grandi, sopraelevate rispetto ai edifici
  micro: medie sul tetto di un edificio
  pico: aree molto dense e indoor
  umbrella: per coprire i buchi delle altre celle

**SIM (Subscriber Identity Module)**
- taglie varie 4Kb a >512Kb
- contiene varie informazioni, in particolare
  *IMSI* (International Mobile Subscriber Identity) e 
  *Ki*, chiave di sicurezza usata nell'autenticazione crittografica a chiave condivisa
*Collegamento crypto GSM*
1. il cellulare manda l'IMSI della SIM all'operatore
2. l'operatore genera un numero casuale e lo manda al cellulare
3. il cellulare firma il numero con la Ki e lo manda all'operatore
4. l'operatore ha nel suo db l'IMSI e la Ki associata: firma anche lui il numero casuale con la Ki e controlla che il numero sia lo stesso che ha ricevuto
##### CDMA
Code Division Multiple Access
Ognuno parla conteporaneamente anche nella stessa frequenza (no FDM o TDM)
- si modella in base a "parole" di diverse "lingue"
  come distinguere in che lingua sono le parole?
  si usa la coordinata dimensionale nello spazio multidimensionale
- ogni asse (perpendicolari tra loro) è una lingua
  quando si parla contemporaneamente, le parole si sommano
- una singola parola non basta, consideriamo la sua positiva e la sua negativa

però come le rappresentiamo nelle onde?
Fourier a cui associamo 1 ai picchi alti e -1 ai picchi bassi
assi ruotati di 45 rispetto a 1 e 0
per estrarre la componente che ci interessa, facciamo la proiezione del vettore sull'asse (prodotto scalare)

**Creazione delle assi**
matrici di Hadamard, matrici di 1 e -1
$H_{1}=[1]\qquad H_{2}=\left[\begin{matrix}1&1\\ 1&-1\end{matrix}\right]$
Il metodo inventato da Sylvester nel 1867 per creare matrici di Hadamard di $2^{n}$.
$\left[\begin{matrix}H&H\\ H&-H\end{matrix}\right]$

esempio.
$A=\left\{\begin{matrix}a_{1}=&1&1&1&1\\ a_{2}=&-1&-1&-1&-1\end{matrix}\right\}\qquad B=\left\{\begin{matrix}b_{1}=&1&-1&1&-1\\ b_{2}=&-1&1&-1&1\end{matrix}\right\}$

$C=\left\{\begin{matrix}c_{1}=&1&1&-1&-1\\ c_{2}=&-1&-1&1&1\end{matrix}\right\}\qquad D=\left\{\begin{matrix}d_{1}=&-1&1&1&-1\\ d_{2}=&1&-1&-1&1\end{matrix}\right\}$

A manda $a_{1}$, B manda $b_{2}$ e D $d_{2}$:

CDMA è abbastanza recente, perché?
- per funzionare, tutti devono parlare allo stesso "volume"
- soluzione: faccio sì che ogni cellulare parli "più o meno forte" a seconda di quanto è distante alla cella
rispetto a D-AMPS e GSM: la gestione delle celle NON SPRECA BANDA!!

Sfrutta al meglio le intermittenze della comunicazione vocale
##### Tra 2G a 3G
**GPRS**
(General Packet Radio Service)
- classificato come 2.5G
- è un overlay del 2G che permette la gestione del traffico a pacchetti in multiplex
- non si spreca banda, non serve un canale dedicato, si può calcolare il traffico (tariffe a traffico)
- supporta IP e PPP
- alloca dinamicamente i canali "internet" e voce

*Tipi di cellulari GPRS*
Classe C: si possono connettere come GSM o GPRS da settare manualmente
Classe B: si possono connettere come GSM o GPRS automaticamente
Pseudo Classe A: si può usare contemporaneamente GSM e GPRS usando una sola frequenza (dual transfer mode DTM)
Classe A: si può usare contemporaneamente GSM e GPRS

**EDGE**
(Enhanced Data rates for GSM Evolution)
- classificato come 2.75G
- usa più modulazioni di fase, backward compatibilità con GSM e GPRS
- velocità variabile tra 64kbps a 236kbps che dipende dalla qualità del servizio
#### 3G
Volta per videochiamate.
- più data rate e più utenti supportati
- bande di frequenza più larghe rispetto al 2G
- standard: W-CDMA e CDMA2000

*W-CDMA (Wideband CDMA)*
anche chiamato UMTS (Universal Mobile Telecommunications Systems)
- banda di 5Mhz
- data rate da 384kbit/s

*CDMA2000*
Usato dall'USA.
- data rate da 144kbit/s per avere più utenti per banda
- banda da 1.25Mhz
##### Tra 3G a 4G
**HSDPA**
(High-Speed Downlink Packet Access)
- considerato 3.5G
- retrocompatibile e usa CDMA e QAM
- varianti: 1.8, 3.6, 7.2 e 14.4Mbit/s
- upload da 384Kbit/s a 2Mbit/s
- in Italia usiamo variante 7.2Mbis/s

**HSUPA**
(High-Speed Uplink Packet Access)
- considerato 3.75G
- massimo 5.6Mbps e 11.5Mbps
  Meno performante del 3.5G versione 14.4Mbps???
  a quei tempi il 3.5G era 3.6Mbps
- alla fine 3.5G ha superato il 3.75G
- Evolved HSPA (HSPA+ o Internet HSPA)
- download 28Mbps e 11Mbps upload
- velocità massima: 42Mbps e 22Mbps
#### 4G
**HSOPA**
(High-Speed OFDM Packet Access)
- detto anche LTE o Super 3G
- bande variabili da 1.25MHz a 20MHz
- download da 1.2Gbps e upload da 600Mbps
- le prime versioni (2009) in Svezia e Finlandia: 
  down 50Mbps e up da 5.3Mbps

*Versioni (CATegory)*
CAT3: 100Mb download / 50Mb upload
CAT4: 150Mb download / 50Mb upload
CAT5: 300Mb download / 75Mb upload
CAT6: 300Mb download / 50Mb upload (CAT6 < CAT5, per problemi di upload)
CAT7: 300Mb download / 100Mb upload
CAT8: 3000Mb download / 1500Mb upload, per collegare celle in modo wireless
CAT9: 450Mb download / 50Mb upload (CAT9 < CAT7 per upload )
CAT10: 450Mb download / 100Mb upload
CAT11: 600Mb download / 50Mb upload
CAT12: 600Mb download / 100Mb upload
CAT13: 400Mb download / 150Mb upload
CAT14: 400Mb download / 100Mb upload
CAT15: 4000Mb download / 1500Mb upload, sempre per celle

Problema: la banda 4G LTE interferisce con la banda del digitale terrestre!!
#### 5G
In piena evoluzione attualmente.
Cambiamo direzione:
- efficienza energetica
- data rate variabile
- connessione a bassa velocità (Internet of Things)

Prendiamo più banda dalle tv, nuovo standard **DVB-T2**
Come facciamo in modo che gli utenti cambino la loro tv? Risoluzione 8k
Compressione da MPEG4 a H.265
Transizione lenta... (costi alti etc.)

2017: Qualcomm presenta Snapdragon X50 per il 5G (1Gb trasmissione)
Prende le bande necessarie da frequenze *microonde e infrarossi*.
2020: uguale alle specifiche precedenti ma con AI (marketing)
2021: 
2024

Microonde -> micro-antenne
Ma possono essere bloccate da una singola mano; multiple antenne lungo tutto il cellulare.

Per espandere hanno bisogno di altre frequenze: dalla spiaggia libera
### Stereo
Usato nella trasmission radio, retrocompatibile con mono.
- radio mono in 30Hz-15kHz
- canale speciale che indica se c'è la versione stereo in 19kHz
- la media dell'audio sinistro S e destro D è quello mandato a mono $M=(S+D)/2$
- il segnale $E=(S-D)/2$ è trasmesso a 23-53kHz
Per riottenere una versione stereo dell'audio, si ricalcolano l'audio sinistro S=M+E e destro D=M-E.
Da notare che queste operazioni peggiorano i rumori quindi l'audio mono può risultare di migliore qualità.

Esistono radio digitali 
Ma non hanno avuto successo
- costo
	Nel segnale tv, l'antenna è esterna quindi basta un apparecchio middleman. Nella radio si deve smontare l'intera autoradio.
- interferenze
	L'antenna tv è lontana dalle interferenze domestiche. L'antenna radio e interna e subisce molte interferenze che nel digitale modifica dati.
- qualità
	In un canale audio-visivo, la compressione audio non è tanto notabile quando in uno solo audio.
## Strato Data Link
Si occupa di
- codifica e decodifica il flusso dati, interfaccia per il network layer
- error control
- flow control
Può essere di varie tipologie con combinazione di
- acknowledgement, ricevuta di ritorno
- connection, istanzia un canale unico
(unacknowledged connectionless) utile per streaming media o quando il canale è molto affidabile.

I pacchetti dati sono definiti in **frame**. 
Come stabilire l'inizio e la fine del frame?
(1) sincronizzazione orologi
	oneroso, usato nella telefonia mobile (raggio delle celle limitato)
(2) character count, nel header è il numero di caratteri del payload
	ma, quando se viene modificato da un errore, sballa tutto il flusso di frame

(3) flag bytes, un byte speciale che indica l'inizio e la fine del frame
![Pasted image 20241114130018](img/Pasted%20image%2020241114130018.png)
C'è bisogno di un simbolo di escape per poter usare il byte speciale come dato (*byte stuffing*)
Ma con tanti caratteri speciali -> tanti escape

*bit stuffing*, risolve il problema di escaping
flag 01111110
e successivamente per ogni cinque 1 si mette 0 preventivamente.
Il ricevente rimuove ogni 0 dopo cinque 1.
### Error control
Composta da due strategie
- error detection
	se trova errore, ritrasmette il messaggio. 
	Basta solo con dati non critici.
- error correction
	la ritrasmissione di messaggi è onerosa, preferibile poterli correggere

*distanza Hamming*, n bit di differenza tra messaggi.
![|400](img/Hamming_distance_3_bit_binary.svg.png)

**parity bit**, bit pari (0) o dispari(1) che conta il numero di 1 nel messaggio
ha una potenza 1, ovvero la distanza minima di Hamming è 2
per ogni m+1 -> error rate di 1/(m+1)
il codice funziona meglio con m=1, identifica il 50% degli errori
molta rindondanza
il data rate effettivo risulta 1-1/(m+1)=m/(m+1)
nel caso migliore (m=1) si perde 1/2 del data-rate

Error correction funziona quando la potenza k è minore della metà della distanza tra messaggi validi.

**repetition code**, ogni bit si ripete N volte
- error detection: potenza $n-1$
- error correction: potenza $(n-1)/2$
il data-rate diventa 1/N

*Build-in error detection*
**codice di Luhn**, usato nelle carte di credito
1. duplica tutte le cifre in posizione dispari
2. somma tutte le cifre
3. sottrai da 10 la somma delle cifre, la soluzione è il numero di Luhn
4. aggiungi questo numero alla fine della sequenza di numeri 
usato anche nei cellulari al numero `*#06#` (IMEI, International Mobile Equipment Identity).
usato per gli ISBN10, sequenza sommatoria cifre, la somma delle ultime due somme deve essere multiplo di 11
codici a barre (UPC, Universal Product Code), somma cifre dispari x3+ somma cifre pari== multiplo 10
#### Codici di Hamming (X,Y)
Sono detti codici lineare, usano solo somme e moltiplicazioni.
Codifica Y bit di dati usando X in totale. X-Y sono i bit "extra".
Scritti anche come Hamming (X,Y,Z), dove Z è la distanza minima di Hamming.

<u>Teorema del peso minimo</u>:
conto gli 1 per ogni riga della matrice generatrice X per Y, il minimo è d, distanza minima di Hamming.

- error detecting: potenza $d-1$
- error correcting: potenza $(d-1)/2$
- data-rate $Y/X$

**Hamming (7,4)**
$2^{4}=16$ codici iniziali, $2^{7}=128$ codici possibili
![](img/Hamming(7,4).svg.png)
L'encoding usa la matrice generatrice $G=\left[\begin{array}{cccc|ccc}1&0&0&0&0&1&1\\0&1&0&0&1&0&1\\0&0&1&0&1&1&0\\0&0&0&1&1&1&1\end{array}\right]$

$\underbrace{(m_{1}\quad m_{2}\quad m_{3}\quad m_{4})}_{\text{messaggio di 4bit}}\cdot\left[\begin{array}{cccc|ccc}1&0&0&0&0&1&1\\0&1&0&0&1&0&1\\0&0&1&0&1&1&0\\0&0&0&1&1&1&1\end{array}\right]=(m_{1}\quad m_{2}\quad m_{3}\quad m_{4}\ |\ p_{1}\quad p_{2}\quad p_{3})$

Ha distanza minima di Hamming Z è 3. Hamming(7,4,3)
- error detecting: potenza 2
- error correcting: potenza 1
- data-rate 0.57

Per trovare e corregge gli errori usiamo
Matrice di parità $H=\left[\begin{array}{cccc|ccc}1&1&0&1&1&0&0\\1&0&1&1&0&1&0\\0&1&1&1&0&0&1\end{array}\right]$
$\underbrace{(p_{1}\quad p_{2}\quad p_{3})}_{\text{messaggio di 4bit}}\cdot H$

**Hamming (8,4)**
Hamming superiore: Hamming ibridi
$G=\left[\begin{array}{cccc|cccc}1&0&0&0&0&1&1&1\\0&1&0&0&1&0&1&1\\0&0&1&0&1&1&0&1\\0&0&0&1&1&1&1&1\end{array}\right]$
$\cdot\underbrace{(m_{1}\quad m_{2}\quad m_{3}\quad m_{4})}_{\text{messaggio di 4bit}}$

E' un Hamming (8,4,4)
- error detecting: potenza 3
- error correcting: potenza 1
- data-rate 0.5

**Hamming (11.7)**
E' Hamming (11,7,5)
- error detecting: potenza 4
- error correcting: potenza 2
- data-rate 7/11 = 0.637 (!! migliore delle precedenti)

Ripensandoci, le strategie di error control prima di Hamming
- parity bit è Hamming (4,3)
- repetition bit è Hamming (3,1) per ogni bit del messaggio

Gli errori in natura accadono a *burst* (esplosione ravvicinata). 
Questo è un problema per ogni codice di error correcting. 
Per risolverlo, sfruttiamo questa loro natura -> **Metodo della matrice invertita (interleaving)**
![](img/Pasted%20image%2020241121134800.png)
Cambiamo l'ordine di trasmissione: invece di mandare l'intero messaggio, mandiamo tutti i n bit dei messaggi (verticale).

Nelle micro-componenti, anche se molto sicure, ovvero con tasso di errore molto basso, ci sono molti errori perché sono velocissime (alta frequenza di dati).
ECC RAM (Error CorreCtion) usa Hamming (72, 64) ha data-rate 89%.
Non tutte le schede madri supportano la correzione errore degli ECC RAM
-> deve supportare SECDED (Single Error Correction Double Error Detection)

Paradossalmente le schede di fascia alte, non si interessano della correzione, solo delle performance (velocità).

Nelle macro-componenti, prendiamo come esempio i viaggi Voyager.
Questi satelliti mandati da ormai 50 anni, sono tutt'ora operativi e alcuni sono andati fuori dall'influenza del sole.
Arthur C. Clarke pone il problema di mancanza di protocollo condiviso.
Le foto dai satelliti arrivano alla Terra dopo innumerevoli errori di trasmissione. Per rendere le immagini più chiare si fa uso di codici di error correction Reed-Solomon.
#### Reed-Solomon RS(X,Y)
Usa aritmetica polinomiale, usiamo i resti dei polinomi come bit di parità. Sempre codici lineari.
- error correction: potenza $(X-Y)/2$

Altri tipi di errori: *erasures* (cancellazione dato)
- data recovery: potenza $X-Y$

Perché gli erasures sono più facili da correggere degli errori normali?
Con gli erasures abbiamo molte più informazione in confronto agli errori di cambio bit 

Se abbiamo entrambi i tipi di errori contemporaneamente, esso funziona se
$2\cdot\text{errors}+\text{erasures}<X-Y$

*error-rate vs data-rate*
Finora abbiamo visto che all'aumento di potenza di data correction, diminuisce il data-rate.
Shannon prova che questo non è affatto vero!!

LDPC (Low D)
ma perdiamo in tempo, decoding esponenziale

Una tecnica simile a Reed-Solomon ma più semplice e senza error correction è il CRC. Guardiamo questa per capire Reed-Solomon.
##### CRC (Cyclic Redundancy Check)
Basato sull'aritmetica polinomiale di base 2.
Ogni numero binario visti come il corrispondente polinomio, ogni bit come coefficiente di potenze sempre crescenti da destra a sinistra.

$1011\rightarrow x^{3}+x+1$
$11010\rightarrow x^{4}+x^{3}+x$
L'addizione e la sottrazione sono xor e sono equivalenti.

Il controllo di parità è il resto R(x) dalla divisione M(x) per G(x).
M(x) polinomio messaggio
G(x) polinomio generatore, scelto e concordato tra il mittente e destinatario

Problema: scegliendo un G(x) qualsiasi, potrebbe capitare che M(x) sia "minore" di G(x) e 

Allora moltiplichiamo M(x) per x^(grado(G(x)))
NB. una moltiplicazione per x^r in un polinomio è uno shift a sinistra di r posizioni

Encoding
1. Dividiamo x^r * M(x) per G(x)
2. Calcoliamo il resto R(x)
3. Trasmettiamo M(x) seguito da R(x), ovvero x^r * M(x)+R(x)
Decoding
- facciamo shift destra rimuovendo la parte aggiunta, ovvero dividiamo per x^r 

Error detection
1 errore: E(x)=x^i 
-> basta che G(x) abbia 2 o più termini
2 errori: E(x)=x^i + x^j 
-> basta che G(x) non sia una potenza di x e che non divida x^k+1 per ogni k fino al massimo valore di i-j

Quindi non riusciamo a trovare l'errore quando E(x)=G(x)* ...
Errori burst: E(x)=x^i(x^j+...+1) è errore burst di lunghezza j+1
-> basta che G abbia grado >j e termini con +1

All'aumentare il grado di G(x), aumenta la potenza 0.5^grado(G(x))
ESPONENZIALE!

CRC-1 x+1 è codice parity bit 1
CRC-32 è usato in bluetooth, ethernet, png, .zip
Reed-Solomon RS(255,233) su GF(255) è lo standard usato da NASA (data-rate 91.4%)
qr-codes usano GF(255) con livello di error-correction fino al 30%

### Flow control
Dobbiamo far comunicare chi manda i dati con il ricevente.

**Stop-and-Wait**
manda, aspetta un acknowledgement e manda ancora
- Vantaggi: basta un canale half-duplex, non ci sono comunicazioni contemporanei
- Svantaggi: non molto efficiente
Usiamo questo protocollo insieme ai controllo degli errori.

1) Cosa facciamo se abbiamo un errore e continuiamo ad aspettare l'acknowledgement? Introduciamo il *timeout*.
2) Ma se è l'acknowledgement ad essere corrotto, potremmo mandare un pacchetto più volte. Dobbiamo correggere il flusso stesso.
   - Numeriamo i frame.
     Problema: quanti bit usiamo per i numeri? se è troppo piccolo non possiamo trasmettere un flusso dati grande.
   - Singolo bit alternante
     Il problema avviene solo a pacchetti consecutivi, bastano due simboli *0 e 1 alternanti*
  
Questo è un protocollo simplex. Nel caso generale full-duplex possiamo usare il protocollo simplex sulle due vie del canale.
Problema: c'è un grande overhead

*Piggybacking*, aggiungiamo l'acknowledgement ai dati che dobbiamo mandare
Ma il flusso dati può essere sbilanciato:
- A manda frame a B
- B aspetta un frame da mandare per fare piggybacking
- ad A scade il timeout e manda nuovamente
Ci vuole un corretto bilanciamento dei flussi o un giusto calcolo del timeout

Se ci impegnamo sul timeout, potremmo rimanere bloccati per moltissimo tempo
bandwisth * round-trip delay
Questo protocollo funziona male perché siamo sottoutilizzando il canale 
Se un canale ha capacità C (bit/s)
la taglia del frame è S (bit) 
e il tempo di round-trip è R
Possiamo calcolare l'utilizzo della linea con $S/(S+C*R)$
Se S< CR abbiamo un'efficienza minore del 50%

Dobbiamo modificare il protocollo stop and wait
-> continuiamo a mandare frame anche se non abbiamo ancora ricevuto l'acknowledgement

> *Tecnica delle sliding windows*
> - definiamo una taglia n basandosi sull'urgenza dell'ack
> - può essere visto come una finestra circolare diviso in n spicchi
> Allora il bit singolo alternato non funziona più, dobbiamo avere tanti bit di controllo quanto i n bit paralleli

Il protocollo Stop and Wait è sliding window di taglia 1.

**Go Back N**
![go_back_n|300](img/go_back_n.gif)
manda in parallelo e riceve in sequenziale
dobbiamo avere un buffer di taglia n frames insieme a un n_timer per l'eventuale ritrasmissione

**Selective_Repeat**
manda e riceve in parallelo

Intuitivamente ci verrebbe voglia di aumentare la taglia il più possibile.
Ma i bit di controllo possono non bastare
-> la taglia della finestra è al massimo la metà dei bit di controllo

Considerazioni: Murphy (errori) è quantificabile!
Ma a causa della velocità delle reti, accadeìono spesso.

Soluzione 1: un timer anche dalla parte degli riceventi
però dobbiamo stare attenti ad avere un timer proporzionale

Soluzione 2: aggiungiamo un NAK, è un avviso per cui non è stato ricevuto un pacchetto; il mittende rimanda immediamente dopo aver ricevuto un NAK

#### HDLC
(High-level Data Link Control)
Creato da IBM. Si usa ancora nei modem mobili, nei fax e nel bancomat.

| bit |    8     |    8    |    8    |   >0    |    16    |    8     |
| ---:|:--------:|:-------:|:-------:|:-------:|:--------:|:--------:|
|     |   Flag   | Address | Control |  Data   | Checksum |   Flag   |
|     | 01111110 |         |         | payload |   CRC    | 01111110 |

Frame di controllo possono essere di 3 tipi:

|             | 1bit | 1bit  | 2bit | 1bit | 3bit     |
| ----------- | ---- | ----- | ---- | ---- | -------- |
| Information | 0    | ---Se | q--- | P/F  | Next     |
| Supervisory | 1    | 0     | Type | P/F  | Next     |
| Unnumbered  | 1    | 1     | Type | P/F  | Modifier |

*Frame Information*


*Frame Supervisory*
Selective Reject, è il NAK
Type può essere
1. REJECT, NAK generalizzato che segnala che vanno ritrasmessi tutti i frame
   qui il next indica il primo frame
2. RECEIVE NOT READY, segnala che ci sono problemi di congestione nel ricevente e quindi richiede di bloccare tutto

*Frame Unnumbered*
Commandi di Unnumbered
- DISC (DISConnect), segnala che una macchina sta uscendo dalla rete definitivamente
- SNRM (Set Normal Response Mode), commando duale che segnala che una nuova macchina è entrata nella rete
- SABM (Set Asynchronous Balanced Mode), commando che crea una connessione bilanciata dove chi entrava ha gli stessi diritti degli altri
- FRMR (FRaMe Reject), rifiuto il frame perché ha una sequenza di controllo sconosciuta/non corretta

#### PPP
Internet usa un sistema Point-to-Point con protocollo PPP
che a sua volta tra data-link a network è LCP e tra network a network NCL

Molto simile al HDLC
PPP usa il byte stuffing invece del bit stuffing perché è più veloce da implementare
gestisce frame a lunghezza variabile

| Bytes |    1     |      1      |      1      |    1 o 2    | Variable |  2 or 4  |    1     |
| ----: | :------: | :---------: | :---------: | :---------: | :------: | :------: | :------: |
|       |   Flag   |   Address   |   Control   |  Protocol   | Payload  | Checksum |   Flag   |
|       | 01111110 |  11111111   |  00000011   |             |          |          | 01111110 |
|       |          | non si usa! | non si usa! | parametrico |          |   CRC    |          |
Hanno nel campo protocollo uno dei due tipi di protocolli
- negoziazione tra data-link e network layer
- di livello più altro (network layer)
C'è l'opzione di rimuovere i campi Address e Control, rimasti solo per retrocompatibilità, ma deve essere specificato nel protocollo.

LCP usa 11 tipi di frame
- Configure-request, propone configurazioni del canale
  Sender -> Receiver
- Configure-ack
  Sender <- Receiver
- Configure-nak, segnalo che alcune opzioni non vanno bene
  Sender <- Receiver
- Configure-reject, connessione non possibile

- Terminate-requenst, richiedo termine della comunicazione
  Sender -> Receiver
- Terminate-ack, comunicazione conclusa
  Sender <- Receiver

- Code-reject, richiesta sconosciuta, non compresa
  Sender <- Receiver
- Protocol-reject, protocollo sconosciuto, errore o non supportato
  Sender <- Receiver

- Echo-request, rimandami il frame indietro
  Sender -> Receiver
- Echo-reply, ecco il frame duplicato
  Receiver <- Sender
Servono per controllare/misurare la qualità del canale.

- Discard-request, ignora il frame
  Sender -> Receiver
  Usato per fare controllo preliminare della linea e aspettando niente, se arriva qualcosa allora ho trovato loop!

Visto come PPP permette frame variabile, ha una taglia massima MTU (Maximum Trasmission Unit, massimo payload)
MTU grande -> pacchetti più grandi -> meno overhead -> più banda
Ma se ci sono errori, l'intero frame può risultare corrotta

PPP si usa in due varianti primarie
- PPPoE (PPP over Ethernet)
- PPPoA (PPP over ATM)

PPP -> PPPoE/PPPoA -> Ethernet/ATM
Flusso 1: dal computer al router 
Flusso 2: del router al modem
Flusso 3: dal model al primo DSLAM (Digital Subscriber Line Access Multiplexer), gestisce connessione dell'intero vicinato
Flusso 4: DSLAM al punto del provider
Flusso 5: finalmente ad Internet
Se c'è di mezzo l'internet wireless, si complica la situazione.

Il primo tratto è ATM e verso la fine è Ethernet
ATM (Asynchronous Transfer Mode), usa TDM ed è analogo a HDLC ma per telefonia/bancomat.
Anche ATM, come PPP, può essere incapsulato dentro il multiplexer (LLC/VC-MUX)

MTU di PPP interagisce con tutti gli altri protocolli in tutti i flussi.
Consideriamo se il MTU è troppo grande e non riesce rientrare nel pacchetto del flusso successivo, deve essere spezzato e rincapsulato.
Notiamo anche che siamo solo dentro data-link, interagendo con gli altri livelli, complica la situazione.

#### Protocolli multiaccesso
Il modello Point-to-Point non funziona quando molti dispositivi vogliono accedere a una stessa risorsa.
Questi sistemi si chiamano *Contention Systems*
- Station Model: sono le entità che trasmettono. Iniziata la trasmissione di frame, non fa altro finché non ha finito di trasmettere
- Single channel
- Collision, se due frame si sovrappongono, c'è collisione e sono inutilizzabili
- Tempo continuo (senza sincronizzazione) o slotted (a intervalli)
- Carrier Sense, una stazione può vedere se il canale è in uso
  No Carrier Sense, una stazione non può analizzare il canale finché non lo usa

##### Protocollo Aloha 
(Norman Abramson)
tutte le stazioni mandano quando vogliono e, in caso di collisioni, lanciano un dado (il caso) per decidere quando ritrasmettere
-> disincronizzazione

Funziona? Calcoliamone la probabilità
La probabilità che k frames siano generati durante un certo intervallo di tempo, se non ci sono sbilanciamenti, è data dalla **distribuzione di Poisson**. E' praticalmente l'opposto della media.$$P(k)=(m^{k}\cdot e^{-m})/k!\qquad m=\text{media}$$E' quindi possibile scegliere prima la media basato sul data-rate della rete.

Una collisione avviene quando un pacchetto viene mandato poco prima del nostro o durante la nostra trasmissione. Questo periodo critico dura quindi 2 pacchetti.
La probabilità di una sola trasmissione (Pr(1)) in un tempo doppio dell'unità 
-> media del periodo è 2m
-> probabilità è $2m\cdot e^{m}$

Troviamo m migliore per avere il massimo di $m\cdot e^{-2m}$
-> $m=0.5$
18.4% non sembra tanto ma dobbiamo tenere conto che queste performance NON DIPENDE dal NUMERO DI STAZIONI che trasmettono
E' incredibilmente scalabile!

Possiamo migliorarla?
1. lunghezza frame variabile -> peggiora le probabilità, rompe la simmetria di trasmissione
2. **Slotted Aloha**
   una stazione principale manda un segnale di sincronizzazione
   e le stazioni mandano in una singola unità di tempo
   -> probabilità $m\cdot e^{m}$ con m migliore m=1
   -> $1/e=36.8\%\quad$ doppio di Aloha!
   Tuttavia ha quindi bisogno di un orologio sincronizzato che abbiamo visto precedentemente sia difficile da mantenere all'aumentare dei sender. Disegnando la distribuzione della media dei Aloha, vediamo che il protocollo è stabile perché a variazioni del pacchetto, il cambiamento delle performance sono lente.
1. **1-persistent CSMA** (Carrier Sense Multiple Access)
   prima di trasmettere, controlla che non ci sia già una trasmissione.
   Possono ancora accadere collisioni nel caso più stazioni vogliono entrare nello stesso tempo, in tal caso, si riaspetta un tempo casuale poi si riprova.
   -> Performance: più del 50%
   Problema: se molte stazioni aspettano di entrare, appena si libera, tutti cercano di trasmettere e avviene collisione
   -> trasmettiamo con una percentuale di trasmissione p scelta (**p-persistent CSMA**)
   -> Performance: possiamo arrivare al 100% al diminuire di p
4. **Nonpersistent CSMA**
   nel caso un canale è occupato, aspetta un tempo casuale e riprova
   -> Performance: arriva fino al 90%
   Da notare che questo protocollo non richiede la definizione di parametri ed è incredibilmente scalabile dato che all'aumentare di pacchetti, migliora la distribuzione di performance

![](img/z9uJA.png)

5. **CSMA/CD** (CSMA with Collision Detection)
   non controlliamo solo quando vogliamo spedire ma anche durante la trasmissione; alla presenza di una collisione, ritrasmette dopo un tempo casuale sprecando così meno banda
   I protocolli Aloha hanno generalmente periodi di
	   - trasmission
	   - contention
	   - idle
   Nel CSMA/CD nel periodo di contention si mandano i pacchetti e uno tra di loro riesce a occupare la linea, poi nella trasmission ha tutta la linea per sé mentre gli altri sono in idle.
   Il tempo da allocare deve contenere due volte il tempo di trasmissione tra le due stazioni più lontane (tempo di roundtrip). La durata della contention è tipicamente il *tempo massimo di roundtrip*, nella quale si usano tecniche di protocollo multiaccesso per contendere la linea.
6. **CSMA/CA** (CSMA with Collision Avoidance)
   Simile al CSMA/CD ma senza collisioni durante il periodo di contention.
   Dividiamo la contention in intervalli uguale per ogni stazione dove possono segnalare se vogliono trasmettere (prenotazione, *reservation protocol*). Per questo basta un bit quindi abbiamo un bitmap.
   -> per taglia del frame d, l'efficienza è d/(d+1)
   Problema: il bitmap aumenta con l'aumentare delle stazioni quindi dobbiamo riservare un periodo abbastanza lungo -> non è efficiente se poche stazioni trasmettono
Osservazione: con poche stazioni CSMA/CA è il protocollo migliore, con tante stazioni 

##### Internet wireless
La topologia di rete non è fissa ma cambia dinamicamente.
Problema: non c'è più un singolo canale ma varie zone spaziali dove alcune stazioni interagiscono
-> da globale diventa *locale*

Problemi
1) A trasmette a B
   C, fuori dal raggio d'azione di A, non sente quindi pensa di poter trasmettere a B
   *hidden station problem*
1) B trasmette ad A
   C sente e conclude che non può trasmettere a D
   *exposed station problem*

**MACA** (Multiple Access with Collision Avoidance)
fornisce informazioni dell'ambiente di communicazione
Ha due commandi:
- RTS (Request To Send) che rende la volontà di inviare messaggi a una stazione
- CTS (Clear To Send) è l'acknowledgement della stazione richiesta
Quelli attorno aspettano che le stazioni parlano e usano Aloha non persistente.

##### Protocollo 802.3 (Ethernet)
Viene in vari tipi con nome identificativo *X base Y*
- X è la banda in Mbps
- "base" indica che è una connessione baseband (a frequenza unica)
- Y è il tipo di cavo
Le interferenze del cavo rendono necessari ripetutori dopo una certa lunghezza. i vari tipi di Ethernet differiscono a seconda della lunghezza massima di ogni tratto.

Bob Metcalfe, studenti del MIT che idea la rete locale e scrive un saggio
AT&T lo contatta per mostrare una demo ma crasha; AT&T non è convinto dell'Arpanet
Passa a fare il dottorato ad Harvard, dove comincia a sviluppare. La tesi viene bocciata e deve rifare l'anno.
Passa a una azienda privata XEROX per sviluppare l'Alto Aloha Network (Alto è il pc fornito da XEROX). Viene poi chiamato l'Ethernet (Ether-net) che viene però giudicato come un progetto senza successo.
Lascia XEROX e fonda 3Com e vende il chip ad IBM per i loro computer. E il resto è storia...

10base5: cavo coassiale (500 metri max) e 100 stazioni
10base2: cavo coassiale fine (200 max) e 30 stazioni
10baseT: cavo twisted pair (100 max) e 1024 stazioni (!!!)
-> non si punta alla grandezza ma densità
10baseF: fibra ottica (2km max)

**Codifica fisica in Ethernet**
Idea: picchi alti di frequenza 1 e quelli bassi 0
all'aumentare della velocità è difficile contare quanti 1 o 0 consecutivi
-> ci sono problemi di sincronizzazione

*Mancherster encoding*
vede le transizioni: da transizione alto a basso è 1, con transizione da basso ad alto è 0
- autosincronizzante, ha un clock built-in
- MA usa il doppio della banda (50% meno efficiente)
Ciononostante è usato da Ethernet perché la sua affidibilità ha reso possibile incrementare la banda!

**Frame di Ethernet**
![](img/Pasted%20image%2020250130205507.png)
1. il preambolo (8 bytes) serve per la sincronizzazione ed è 101010...
2. nell'indirizzo di destinazione (6 bytes)
	- se il primo bit è 1, è una connessione multicast
	  se tutti i bit sono 1, è una connessione broadcast
	- il secondo bit distingue indirizzi locali e globali
	- spazio rimanente è 48-2=46bit per *indirizzi MAC* 
		MAC (Media Access Control) sono gestiti dall'IEEE
		- primi 3 byte per produttore, OUI (Organizationally Unique Identifier)
		- secondi 3 per il loro spazio di indirizzi
3. il tipo indica il protocollo o l'uso del frame, analogo a PPP
4. il campo dati ha al massimo 1500 bytes
5. il campo pad di lunghezza variabile, serve per assicurare che il frame sia almeno il tempo di roundtrip (lunghezza minima)
   -> rende efficiente la collision detection
8. checksum CRC-32 per error detection

Nel caso avvenga comunque collision, 
usiamo Aloha in una versione dinamica: aumenta esponenzialmente il tempo di attesa massimo e ritrasmette a caso finché non funziona (*binary exponential backoff*)
per non rischiare, dopo 10 collisioni poniamo un intervallo massimo a 1023 slots per altre 10 collisioni e poi si rinuncia (*binary exponential truncated backoff*)

**Efficienza di Ethernet** T( T+2* roundtrip / alpha)
dove T è il tempo medio di trasmissione di un frame, T= lunghezza frame / bandwidth
e alpha è la probabilità di trasmissione nel canale
L'efficienza è inversamente proporzionale a bandwidth * lunghezza.
Bandwidth è importante, limitiamo la lunghezza massima della rete.
### Dispositivi di rete
Le reti locali tengono a diventare piccole. Come componiamo reti più grandi?

| strato      | dispositivo         |
| ----------- | ------------------- |
| application | application gateway |
| transport   | transport gateway   |
| network     | router              |
| data-link   | bridge / switch     |
| fisico      | repeater / hub      |

**repeater/hub**, ripete il segnale fisico
hub propaga il segnale da una porta alle altre

**bridge/switch**
eliminano i limiti di grandezza della reta che hanno domini di collisione diversi
learning: impara la configurazione di rete, controlla mittente e destinatario (MAC address)
  usa backward learning per costruire le hash tables. 
  (1 fase) riceve un messaggio da mandare
  (2 fase) non conoscendo niente, fa *broadcast*
  (3 fase) riceve risposte dalle stazioni e li segna nel hash tables
  (4 fase) conoscendo la rete del mittente e del destinatario, fa passare i messaggi solo tra questi
Problema: la rete può cambiare. usiamo un timeout di *fading* per quanto non si riceve da una stazione

**router**
abbiamo bisogno del concetto di distanza: contiamo il numero di *hops*, ovvero di stazioni incontrate nel cammino
queste distanze possono essere pesate per tempo
*flooding*, il pacchetto viene ritrasmesso a tutte le linee (tranne quello da cui è arrivato)
Problema: la rete viene sommersa
- <u>hop counting</u>, associamo un numero massimo di hop ad ogni pacchetto, dopo il quale muore
- <u>tracking</u>, teniamo traccia del pacchetto già trasmetto per non ritrasmetterlo
  si tiene un contatore speciale per la lista dei pacchetti 0-N ricevuti, tuttavia tiene conto solo di pacchetti consecutive
Anche con queste tecniche si genera una quantità enorme di pacchetti. Quali sono allora i vantaggi?
- il flooding sceglie sempre la via migliore
- il più robusto rispetto i cambiamenti di rete
Utilissimo quindi per casi in cui il carico di rete non è alto, la topologia di rete è molto variabile o i messaggi devono arrivare il più presto possibile.

Tutte le altre tecniche si basano sulla raccolta dell'informazione globale, sommando le informazioni locali di ogni router.

*Distance vector routing*, usato nella prima versione dell'Internet (ARPANET)
ogni router chiede ai router vicini la loro tabella di routing, usa queste e il tempo che c'è voluto ad ottenere risposta a costruire i percorsi migliori (somma questi tempi alle tabelle dei rispettivi router)
Vantaggi: è veloce a recepire la decongestione di pezzi di rete
Problema: problema del count-to-infinity, un pezzo di rete può essere congestionato ma ciò non viene rispecchiato subito nelle tabelle distanti più di un passo

*Link state routing*, 1979
ogni nodo trova i suoi vicini (manda "hello") e costruisce i passi e i loro tempi. Questo viene mandato in broadcast da ogni router e ognuno riesce a costruirsi la mappa.
Il broadcast avviene con il flooding ogni tot refresh
-> risolve il problema precedente della località della propagazione delle informazioni

### Quality of Service (QoS)
è una serie di parametri che dettano la qualità del servizio offerto. Nelle reti ce ne sono 4:
- Reliability (affidabilità)
- Bandwidth (banda)
- Delay (ritardo di trasmissione)
- Jitter, "secondo ordine" del delay, misura il grado di variazione (deviazione standard) nei tempi di arrivo dei pacchetti
E' importante definire il QoS per le varie applicazioni, influenza la loro costruzione.

| Applicazione    | Reliability | Delay  | Jitter | Bandwidth |
| --------------- | ----------- | ------ | ------ | --------- |
| e-mail          | high        | low    | low    | low       |
| web access      | high        | medium | low    | medium    |
| video on demand | low         | low    | high   | high      |

Riguardo reliability, abbiamo già visto error control e correction.
Le altre misure derivano dalla congestione, quando la capacità della linea o qualche stazione si satura.
#### Congestion control
*Paradosso di Braess*: aggiungere la capacità ad una rete può portare a una diminuizione della performance (!!!)
-> MA allora rimuovere capacità può migliorarla!

Il router si accorge che una stazione sta sovraccaricando la rete, manda un **choke packet** che richiede la riduzione del data-rate del 50%.
- Come si esce? fading
- Come si entra? i router che si accorgono del sovraccaricamento e mandano ogniuno un choke packet, la stazione riduce eccessivamente il suo data-rate
  *fading alla rovescia* (di entrata), dopo che riceve un choke, ignora per un certo periodo di tempo altre richieste di choke

Se una rete è grande, una richiesta di choke può metterci troppo tempo
-> variante del choke: **hop-by-hop**
tutte le stazioni di passaggio dal router alla stazione colpevole, riducono anch'esse il loro data-rate

Tecniche preventive
buckets sono una specie di filtri che garantiscono il QoS
- *leaky buckets* è un tipo di filtro che garantisce un data-rate massimo costante (evita i burst che sovraccaricano la rete)
  pro/contro: data-rate non del tutto sfruttato
- *token bucket*, genera un numero fisso di token dopo un certo intervallo di tempo, i pacchetti in arrivo possono uscire solo se "bruciano" un token
  Se ci sono meno pacchetti dei token forniti, quelli non bruciati rimangono pronti a sostenere un possibile burst. Questo rende la media del data-rate costante.

## Internet Protocol (IP)
1969: ARPANET usava il Network Control Protocol (NCP) -> inadatto
1974: arriva il Trasmission Control Protocol (TCP)
1978: avviene la scissione TCP e IP

![](img/IPv4_Packet-en.svg)

- Version, versione del protocollo IP
- IHL (Internet Header Length), lunghezza dell'header
- Type of service, utile per QoS ma opzionale (quindi non usata)
- Total length, lunghezza totale del datagramma

+ Identification, identifica il pacchetto se è frammentato
+ "Evil bit" (IETF RFC3514)
+ DF (Don't Fragment) impone la non frammentazione dei dati
+ MF (More Fragment) segna l'ultimo frammento
+ Fragment offset, il numero d'ordine del frammento

* TTL, l'eta massima del pacchetto
* Protocol, protocollo di livello più altro che usa IP
* Header checksum, banale calcolo delle somme a complemento a due

Povero e con poche funzionalità, perché?
1969: NCP era già affidabile con controllo di flusso

Il TCP/IP è inizialmente commissionato da DoD (USA Department of Defense)
- no overload
- robustezza
  perdere pacchetti non è un problema, 
- modello closed world (MILNET), gli attacchi vengono da fuori
  reso open world quando è passato al pubblico

### Limiti (fissi) di IP
TTL: 255 hops massimi può diventare un problema con una rete molto grande
-> la rete è gerarchica e il router può riaumentare il TTL

Indirizzi: 32bits è un grande problema
c'è una autorità centralizzata che li assegna a blocchi (ingestibile uno a uno)
all'inizio di internet si avevano diverse classi di blocchi assegnabili a seconda della grandezza della rete richiesta, **classful addressing**
- classe A (7+24)
  128 reti possibili, con indirizzi di 24bits (16.7 milioni)
- classe B (14+16)
  16384 reti possibili, con indirizzi di 16bits (65536)
- classe C (21+8)
  circa 2 milioni di reti, con indirizzi di 8bits (256)
Manca una taglia media nel migliaio -> la gente comune si ritrovava attratta alle reti di classe B
Anche Ethernet di Metcalfe usa una sola taglia di rete (3+3 bytes)

Soluzione? **(CIDR) Classless InterDomain Routing**
ora i blocchi sono di lunghezza variabile
c'è il rischio che tabelle di routing esplodano in grandezza
-> usiamo *aggregate entries*, se varie classi di indirizzi vengono indirizzati in uno stesso router, sono combinati in un'unica entrata se hanno prefisso comune
Cosa succede se un'altra organizzazione ha lo stesso prefisso e deve essere mandata in un altro router? Usiamo la regola di *longest matching*, cioè l'entrata con il prefisso di rete più lungo ha priorità

NAT

### Sottoprotocolli di IP
protocolli incapsulati in IP, ovvero i loro pacchetti sono pacchetti IP con Protocol settato con il loro identificativo

**ICMP (Internet Control Message Protocol)**
usato per il controllo
- choke packet
- destination unreachable, informa il mittente di non riuscire a raggiungere il destinatario
- time exceeded, informa il mittente del pacchetto distrutto
  può mappare la rete da come è percorsa

Siamo nello strato network per mandare un pacchetto IP e l'indirizzo destinatario è IP. Tuttavia è lo strato data-link che gestisce il percorso.

Da MAC a IP
**DHCP (Dynamic Host Configuration Protocol)**
Quando una macchina vuole sapere il suo IP, manda un pacchetto DHCP di tipo DISCOVERY.
Il gestore DHCP della rete (*centralizzato*) risponde con l'indirizzo corrispondente.

Da IP a MAC
potremo usare una struttura simile a quella di DHCP, ma è pesante (centralizzazione). 

Gli indirizzi MAC sono già assegnati da costruzione
-> gestione distribuita, broadcast (in LAN è simile al point-to-point)
**ARP (Address Resolution Protocol)**
Ogni macchina ha una tabella locale IP->data-link.
Quando si vuole mandare un messaggio a una macchina con indirizzo IP X, manda un messaggio ARP (broadcast) chiedendo chi ha l'indirizzo IP X. Solo la macchina che lo ha risponde con un messaggio ARP di ACK, includendo il suo indirizzo data-layer.
Ottimizzazione
1. ogni pacchetto ARP ha un piggyback con l'IP
2. dato che i messaggi sono broadcast, le altre macchine possono salvarsi le informazioni IP->data-layer
3. quando una macchina entra nella rete, invia un pacchetto ARP chiedendo il suo stesso indirizzo IP che non viene risposta da nessuno
   se qualcuno risponde allora c'è un errore di configurazione di rete
Se c'è una nuova informazione di assegnazione, prendo quella più nuova come buona ("milk style")

#### Oltre IP? IPv6
Rimane il problema di scarsità di indirizzi dello spazio IP -> IPv6
Sebbene abbia un nome simile, è una nuova versione di internet ed non è retrocompatibile (difficoltà di passaggio, costoso)
Gli indirizzi sono ora 16bytes, ancora limite fisso ma è grandissimo

IPv6 non ha più il campo checksum -> protocollo totalmente unreliable
l'idea è il protocollo deve essere velocissimo

## Strato di trasporto
Lo stato di trasporto è differente da quello di network perché è a un livello di astrazione più alta: fa multiplexing delle singole risorse network tramite **porte** (ports)
IP+port=*socket*, cioè la divisione in "rete logica" di una singola entità a livello di transport
### UDP (User Datagram Protocol)

![](img/ptiIA.jpg)
UDP è un protocollo *connection-less* e si usa per inviare messaggi brevi e senza bisogno del controllo di dati
-> usato nel **DNS (Domain Name System)**

DNS è un sistema che associa i nomi agli indirizzi IP. Funziona gerarchicamente 
### TCP (Transmission Control Protocol)
TCP ha controllo di errore e prevede una connessione duplex point-to-point.

![](img/image27.png)
- source e destination
- TCP header length
- 6 flags
  1. ACK, acknowledgement della ricevuta del messaggio
  2. RST, reset della communicazione
  3. SYN, per aprire la connessione
  4. FIN, chiusura connessione che richiede handshaking con ACK (anche in piggyback). Termina in un solo dei canali
  5. URG e PSH, urgenza e priorità del pacchetto (URG > PSH)
- urgent pointer indica l'ultimo byte urgente
- window size che indica la taglia di sliding window. Il metodo di default è go back n
- checksum, controllo di errore semplice con somme

Usa 3-way handshake A<->B
1. richiesta apertura connessione da A
2. richiesta apertura connessione da B con ACK in piggyback
3. ACK da A

Ora possiamo spiegare come funziona NAT.
Usa le porte per aumentare il numero di IP usabili. 
Da notare: opera nello strato network ma usa un protocolli dello strato di transporto!! E' una pezza per risolvere retroattivamente un problema.
Ma questo provoca anche dei problemi: il sistema diventa connection-oriented quindi quando il NAT box crasha, tutte le connessioni cadono.

Di chi è INTERNET?
dei governi e dei privati. Non è integrata né democratica.
C'è un altro livello, quello degli AS (Autonomous System) i cui ognuni hanno le proprie politiche di routing.

BGP (Border Gateway Protocol)
BGP è il protocollo che gestisce le frontiere tra AS.

La velocità richiesta per la trasmissione dei dati dal router è di tempo inferiore a quella richiesta all'accesso della RAM.
Si usa SRAM e l'algoritmo di lookup "Lulea scheme"

## Cryptosecurity
P(E(plaintext)) = plaintext

**Principio di Kerckhoff** (1883)
Il sistema della segretezza non dovrebbe richiedere 
La parte segreta è relegata da chiavi (keys).

Il suo opposto è la *security by obscurity* che però non offre nessun livello di sicurezza.

Cypher: trasformazione carattere per carattere o bit per bit.
Code: trasformazione parole per parole.

Choctaws (1a guerra mondiale), Comanche (2a guerra mondiale)
entrambe sono tribù americane impiegati a codificare messaggi di guerra nella loro lingua nativa.+

**Cifrario di Ceaser**: sposto il messaggio per un numero di posizioni nell'alfabeto

Questi sono tutti metodi che usano il principio di obscurity.

Livello superiore di quello di Ceaser è una permutazione delle posizioni per ogni carattere
-> molto difficile da decriptare con forza bruta

Ma! Possiamo usare altri metodi di decrypting come l'analisi della frequenza dei caratteri più usati (etaoin), bigrammi (th-he-in-er-an...) o trigrammi

**One-Time Pad** è un sistema crittograficamente sicuro
1. si usa una chiave grande quanto il messaggio
2. facciamo lo XOR tra messaggio e chiave

Problemi
- La sequenza deve essere scelta bene!
  Se usiamo un libro esistente, c'è ordine!! Nella 
- "One-Time": se riusiamo la chiave, basta fare lo XOR dei due messaggi criptati per ricavare quelli in chiaro (senza conoscere la chiave!!)
### Block Cipher
agisce su blocchi di bit per tradurli in blocchi criptati
Operazioni
- P-Box (Permutation Box), faccio permutazione di blocchi di bit
- S-Box (Substitution Box), sostituiscono alcuni bit con altri
in entrambe le operazioni, aggiungo del salt

E(D(P))=P proprietà delle funzioni intercambiabili

**DES (Data Encryption Standard)**
Creato di IBM (Lucifer) ha una chiave da 128bit.
Viene usato come standard dal NSA (National Security Agency) MA tagliano la chiave a 56bits.
Con il tempo 56bits sono troppo pochi è possono venire crackati.

**Triple-DES**
usa tre volte DES in sequenza con 2 chiavi (112bit)
$E(P)_{k_{1}}\rightarrow D(P)_{k_{2}}\rightarrow E(P)_{k_{1}}\quad$ algoritmo encryption
$D(P)_{k_{1}}\rightarrow E(P)_{k_{2}}\rightarrow D(P)_{k_{1}}\quad$ algoritmo decryption
Perché facciamo decryption come secondo passaggio invece di fare sempre encryption? Retrocompatibile col DES (singola chiave)

Per trovare il successore del DES, aprono un bando internazione.

**AES (Advanced Encryption Standard)**
Rijndael (1998) di Vincent Rijmen e Joan Daemen (Belgio)
flessibile con la scelta di chiavi a blocchi di 128bits a 256bits

Tutti i sistemi visti finora, usano una parte di informazione segreta che viene condivisa (chiave) ma questo implica che prima dobbiamo trovare un modo per scambiare questa informazione.
- Canali esterni e sicuri? Complicato.
- Come scambiare la chiave segreta usando un mezzo insicuro senza avere un segreto condiviso precedente?
(1976) Diffie e Hellman scoprono un nuovo *sistema a chiave pubblica* (public key) dove non devono essere scambiati informazioni segrete

**RSA (Rivest Shamir Adleman)**
1. A sceglie 2 grandi primi p e q
2. A manda $p*q$ a B
3. B usa $p*q$ per codificare il messaggio e lo manda ad A
4. A usa p e q per decodificare il messaggio
-> per chi attacca, il problema è trovare *i fattori primi di un numero*, non risolvibile tuttora

#### Attacchi Cybersecurity
Block Cypher ha la caratteristica di un *ECB (Electronic Code Book)*. Anche senza essere decryptato, l'attaccante può comunque sfruttare la forma del messaggio scambiando l'ordine dei blocchi (ECB attack).

Per proteggere la struttura del messaggio usiamo *cypher modes* che crea dipendenza tra i diversi blocchi.
Es. **Stream Cipher Mode**
- One-Time Pad con chiave piccola e un Initialitation Vector (IV)
- che viene cryptato consecutivamente

IV deve essere cambiato ogni volta; se non viene cambiato è possibile fare *Keystream reuse attack*
(P1 xor K) xor (P2 xor K) = P1 xor P2
fa sparire la parte crypto e sono rimasti i due testi in chiaro

*Replay attack*: rimandare lo stesso messaggio

*Man in the middle (MTM)*: creare una connessione MTM (anche sicura) con cui far connettere il cliente al server e salvare le informazioni ricevute.

Servono i certificati di sicurezza fornite da entità centrali superiori. Come mandano le chiavi segrete che certificano la loro autorità? Canale esterno: già implementati nella macchina al momento dell'acquisto.

##### DoS (Denial of Service) attack
*Smurf attack (ping of death)*: richiesta ICMP di echo più volte

*DDos*: attacco DoS da molteplici macchine contemporaneamente (Distribuited DoS)
Attacco reverse: *IP spoofing attack*
- L'IP non ha alcuna sicurezza. 
- L'attaccante scrive messaggi a diversi siti cambiando mittente in quello che vuole attaccare. 
- La vittima riceve risposte da tutti i diversi siti -> DDoS

Usiamo un IP sicuro: IPSec
Con autenticazione HMAC (Hashed Message Authentication Code)
HMAC = Hash(messaggio, chiave)
In transport mode si inserisce l'informazione dopo l'header ip
In tunnel mode è incapsulato 
![](img/ipsec-ESP-tunnel.png)

I sistemi DNS non hanno sicurezza
*DNS amplification*: DDoS chiedendo il DNS protocol di un sito a diversi server DNS
DDoS contro il server DNS (es. usando l'attacco reverse DDoS)

*DNS spoofing*: 
soluzione definitiva: DNSSec
ogni record DNS ha due campi in più
- KEY, chiave pubblica
- SIG, firma crittografica
Vengono propagate le informazioni sicure.
Root servers sono i server DNS centrali. Sono 13 principali (distribuiti in 1300+)

Ma se qualcuno riesce a crackarli? 
- usiamo chiavi grandi 
- chiavi pubbliche di grandezza normale ma cambiate spesso
  chi avvia la richiesta di cambio? uno possiede una chiave grande *KSK (Key Signing Key)* da 1024bits (ora passata a 2048) 
  abbiamo bisogno di rindondanza perché alla sua perdita nessuno riesce a richiedere il cambio.
  la KSK è divisa in pezzi nel 2010 e ogniuna delle 7 entità ne possiede una parte. A cui bastano 5 dei 7 per ricostruire la chiave (error correction)

WEP (Wired Equivalent Privacy)
Usa lo Stream Cipher
WEP-40 da 40bit
IV ha 24bit ancora debole al Keystream stream attack

Brute force attack non è da sottovalutare -> supercomputer ora più accessibili con schede grafiche

Siamo protetti se non siamo collegati a rete? Attacchi allo strato fisico

da vedere: Matrix, Inception, Frankestein junior, Full metal jacket