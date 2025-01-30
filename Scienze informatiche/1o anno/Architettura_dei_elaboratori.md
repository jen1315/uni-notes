Computer Organisation And Architecture, 10th ed.

- [[#1. Concetti base|1. Concetti base]]
- [[#2. Notazioni in diverse basi|2. Notazioni in diverse basi]]
- [[#3. Componenti e connessioni|3. Componenti e connessioni]]
	- [[#3. Componenti e connessioni#3.1 Architettura Von Neumann|3.1 Architettura Von Neumann]]
	- [[#3. Componenti e connessioni#3.2 Ciclo FETCH, DECODE, EXECUTE|3.2 Ciclo FETCH, DECODE, EXECUTE]]
	- [[#3. Componenti e connessioni#3.3 Connessioni BUS|3.3 Connessioni BUS]]
	- [[#3. Componenti e connessioni#3.4 POINT-TO-POINT interconnect|3.4 POINT-TO-POINT interconnect]]
- [[#4. Memoria|4. Memoria]]
	- [[#5. Memorie interne|5. Memorie interne]]
	- [[#5. Memorie interne#6. Memoria Esterna|6. Memoria Esterna]]
- [[#7. Input e Output|7. Input e Output]]
- [[#8. Aritmetica dei calcolatori|8. Aritmetica dei calcolatori]]
		- [[#Numeri naturali con segno|Numeri naturali con segno]]
		- [[#Numero reali|Numero reali]]
	- [[#8. Aritmetica dei calcolatori#Linguaggio macchina|Linguaggio macchina]]
		- [[#Dati x86|Dati x86]]
	- [[#8. Aritmetica dei calcolatori#Pipeline|Pipeline]]
	- [[#8. Aritmetica dei calcolatori#Filosofia RISC|Filosofia RISC]]
		- [[#MIPS (32bit)|MIPS (32bit)]]
	- [[#8. Aritmetica dei calcolatori#Multicore|Multicore]]

## 1. Concetti base

- **Architettura**: caratteristiche visibili al programmatore (Instruction Set Architecture), tecniche di indirizzamento della memoria
- **Organizzazione**: unità operative e loro connessioni hardware, serve per implementare l'architettura

Programmi scritti per una specifica architettura funziona in tutte le organizzazioni che usano l’architettura.

**Struttura**: il modo in cui i componenti si relazionano
**Funzione**: le operazioni che dei individuali componenti

Si segue una struttura **TOP-DOWN** 
ovvero, partendo dalle istruzioni, determiniamo i componenti maggiori e la loro struttura e funzione per poi costruire i componenti ai più bassi livelli.

Struttura calcolatore
- Elaborazione dati (CPU)
- Memorizzazione dati
- Trasmissione dati
- Controllo delle funzioni precedenti

CPU (Central Processing Unit)
- ALU (Arithmetic Logical Unit)
- Registri
- Interconnessioni
- Unità di controllo
E così via ricorsivamente.. 

Tipologia architettura : CISC(Complex Instruction Set Computer) vs RISC(Reduction Instruction Set Computer); x86 vs ARM

ARM è predominante nei sistemi embedded
## 2. Notazioni in diverse basi
$$\sum_{k=n,n-1}d_k2^k$$Notazione binaria $\mathbb{N}$
Come si calcola: dividi per 2 la $x$ a base decimale, e prendi i resti
Numero massimo in $n$ bit: $2^n-1$

Byte: 8bit
Misure multipli di 2

Notazione esadecimale $\mathbb{N}$
- sedici simboli: 0,1,2,…,10,A,B,…,F
- un simbolo per rappresentare ogni gruppo di 4 cifre binarie

| 1011 | 0101 | 0011 | $_2$    |
| ---- | ---- | ---- | ------- |
| B    | 5    | 3    | $_{16}$ |

Algebra di Boole
- variabili binarie (vero o falso)

| A   | B   | AND ($A*B$) | OR ($A+B$) | XOR ($A\oplus B$) |
| --- | --- | ----------- | ---------- | --------------- |
| 0   | 0   | 0           | 0          | 0               |
| 0   | 1   | 0           | 1          | 1               |
| 1   | 0   | 0           | 1          | 1               |
| 1   | 1   | 1           | 1          | 0               |
NAND = NOT(A\*B) = ($\bar{A*B}$)$\quad$NOR = NOT(OR) = ($\bar{A+B}$)

## 3. Componenti e connessioni

Calcolatore non generico
- Esegue un programma prestabilito nella sua costruzione
- Si chiama programma “cablato”, ed era il solo sistema esistente pre-Von Neumann
### 3.1 Architettura Von Neumann

Esecutore generico
- Dati e istruzioni in memoria accessibile sia in lettura che scrittura
- Memoria accessibile per indirizzo
- Esecuzione sequenziale delle istruzioni

Un programma è una sequenza di istruzioni di cui ognuno è una operazione logica o aritmetica. Per ogni operazione, un diverso insieme di segnali di controllo.

![[Pasted image 20240125233443.png]]

**Top-view components**
CPU
MEMORIA
INPUT/OUTPUT

![[IMG_7641.jpg]]

CPU = interprete delle istruzioni + generico modulo per operazioni aritmetico-logiche + vari registri
- PC : Puntatore, contiene l’indirizzo dell’istruzione successiva
- IR : Registro contenente istruzione da eseguire
- MAR : Registro con indirizzo memoria dove si vuole scrivere o leggere
- MBR : Registro che contiene il dato da scrivere o quello letto da memoria
- I/O AR : Registro con porta I/O dove si vuole scrivere o leggere
- I/O BR : Registro che contiene il dato scritto o da mostrare in I/O
MAR e MBR sono gli unici collegati alla memoria.

Memoria centrale (RAM)
- Possibilità di fare salti di locazione
- Tempo di accesso sono stesse
- Operazioni richiedono accesso a più dati in memoria
- Immagazzinare temporaneamente sia istruzioni che dati

Buffer I/O : ricezione input, visualizzazione output etc.
### 3.2 Ciclo Fetch, Decode, Execute (FDE)

![[Pasted image 20240127195616.png]]
1. Istruction Fetch
   Preleva l'istruzione dall'indirizzo indicato dal Program Counter e salvalo nell'Instruction Register.
2. Instruction Operation Decoding
3. Operand Address Calculation
4. Operand Fetch
   Preleva l'operando dall'indirizzo calcolato, ritorna a 3. per multipli operandi.
5. Data Operation
6. Operand Address Calculation
7. Operand Store
   Salva il risultato all'indirizzo calcolato, ritorna a 6. per multipli risultati.
8. Interrupt Check
	81. Interrupt
	Ritorna a 3. se l'istruzione prevedeva array o stringa.
9. Instruction address calculator
   Calcola l'indirizzo dell'istruzione successiva e lo salva nel PC. Ritorna a 1.

Interruzione: meccanismo con la quale altri moduli posso interrompere la normale sequenza di esecuzione.
Può attivarsi per Errore programma, Timer, I/O, Guasto hardware.

**Interrupt Handler**
Nel ciclo FDE, la CPU fa il controllo delle interruzioni dopo l’EXECUTE e, quando avvengono, ritorna a FETCH altre istruzioni.

È possibile disabilitare le interruzioni in esecuzioni importanti.

<u>Interruzioni multiple</u>
Opzione 1. Gli altri interrupt rimangono pendenti quando se ne gestisce uno.
Tuttavia è possibile che gli interrupt abbiano priorità differenti.
Opzione 2. Interruzioni annidate
Gestire un primo interrupt finché il controllo di interrupt ne intercetta un altro di cui, se di priorità maggiore, iniziare a gestirlo. Questo avviene ricorsivamente.

### 3.3 Connessioni BUS
Operazioni di 4 tipi
- Processo memoria (CPU a M)
- Processo I/O (CPU a I/O)
- Elaborazione dati (operazioni logico-aritmetiche)
- Controllo (alterare la sequenza delle istruzioni)

Moduli sono connessi e comunicano tramite il BUS.
Il segnale trasmesso da uno dei moduli è disponibile a tutti gli altri collegati allo stesso bus, ma solo uno può trasmette alla volta.
C'è un BUS dati, uno indirizzi e uno di controllo.

Opzione 1. C’è una entità che fa da instradatore.
Opzione 2. All’interno di ogni componente c’è una logica che permette la coordinazione.

Vediamo opzione 1.
La comunicazione con l’arbitro avviene tramite le linee di controllo.
L’ampiezza delle linee del BUS determina la massima quantità di M indirizzabili.

Segnali di controllo
- M write
- M read
- Richiesta BUS, un modulo vuole il controllo del BUS
- BUS grant, il controllo è concesso a un modulo
- Interrupt request, interruzione pendente
- Clock, per sincronizzare le operazioni con cicli 1-0

Problema: Ritardi per ottenere l’uso del bus.
Soluzione 1. Usare più BUS
![[IMG_7653.jpg]]
La cache è trasparente alla CPU. Il Local I/O controller controlla se il dato dell’indirizzo alla memoria richiesto dalla CPU è presente nella cache, altrimenti manda la richiesta alla memoria.

### 3.4 POINT-TO-POINT interconnect
Con l‘avanzamento tecnologico, le CPU diventano sempre più veloci e complesse per cui il BUS diventa il collo di bottiglia.

**QuickPoint Interconnect**
CPU con più core, 
Trasferimento pacchetti
Coordinatore nei core

| Livelli QPI |               |            |
| ----------- | ------------- | ---------- |
| Protocollo  | < Pacchetti > | Protocollo |
| Routing     |               | Routing           |
| Link        | < Flits >     | Link       |
| Fisico      | < Phits >     | Fisico     |
Phits = unità di trasferimento a 20bit
Flits = unità di controllo del flusso a 80bit
Pacchetti = è composto da un numero intero di Flits

Livello fisico
Trasmessi a Round Robin

Livello link
- controllo dell’errore: 8bit sono usati per rilevare errori di trasmissione sui 72 bit di pacchetti
- controllo di flusso: per evitare di mandare più richieste di quanto quelle che un modulo riesce a gestire (sistema a crediti, di numero dipendente alla dimensione di buffer del ricevente)

Livello routing
Tabelle di instradamento
- definito dal firmware, software direttamente definito dal componente elettronico
- descrive i possibili percorsi che un pacchetto può seguire

Livello protocollo
Il pacchetto è definito in modo comprensibile dalle diverse componenti.
Supporta il protocollo di coerenza della cache, in modo che non esistano informazioni contrastanti fra i contenuti delle cache e la memoria principale.

## 4. Memoria
- **Locazione:** processore, interna(principale), esterna(secondaria)
- **Capacità:** dimensione parola, numero di parole
- **Unità di trasferimento:** parola, indirizzamento, blocco
- **Metodo di accesso:** sequenziale, diretto(nella zona interessata ma poi sequenziale), casuale(diretto, tempo accesso non dipende), associativo
- **Prestazioni:** tempo di accesso, tempo di ciclo, velocità di trasferimento
- **Caratteristiche fisiche:** volatile o no, riscrivibile o no
- **Modello fisico:** semiconduttore, magnetico, ottico

Gerarchie di memoria
- Registro
- Cache (SRAM)
- Memoria centrale (DRAM)
- Disco
- CD/DVD-ROM
- Nastro

Si assumono le seguenti proprietà dei programmi
- Linearità dei riferimenti, ovvero l’accesso di indirizzi consecutivi
- Località dei riferimenti:
	- Spaziale, accessi ad indirizzi contigui sono più probabili
	- Temporale, la zona recente è quella di permanenza più probabile

La gestione di edge cases 10%, impiega il 90% del tempo d’esecuzione del programma.

La CPU si interfaccia con i livelli alti. Dati dai livelli più bassi viene copiato ai livelli più alti.

La cache è trasparente alla CPU, la CPU fa richieste ad indirizzi RAM e la cache da solo deve fare la gestione 
Connessione tra CPU e cache è molto veloce mentre quello tra cache e memoria è lenta.

La memoria centrale è suddivisa in blocchi. La cache si copia tutto il blocco in cui l’indirizzo richiesto ricade. 

| tag              | blocco |
| ---------------- | ------ |
| 0000000000000000 | 20 BA EE ...$\qquad\qquad\qquad\qquad\qquad\qquad$       |
| 0000000000000001 | 17 EA ...       |
| …                |        |
| 1111111111111111 |        |
[a] Cache

| address | RAM |
| ---- | ---- |
| 0000000000000000[00] | 20$\qquad\qquad\qquad\qquad\qquad\qquad$ |
| 0000000000000000[01] | B4 |
| 0000000000000000[10] | EE |
| … |  |
| 0000000000000001[00] | 17 |
| 0000000000000001[01] | EA |
| ... |  |
[b] Memoria centrale

Hit e miss
Un dato richiesto dalla CPU può essere presente in cache (hit) oppure mancante (miss)
- hit deve essere molto probabile perché il sistema sia efficiente
- miss, almeno uno è inevitabile (miss di primo accesso)
$T_a=T_h*P_h+T_m*(1-P_h)$

Gestione cache
- Tecniche allocazione
- Individuazione hit o miss
- Rimpiazzo blocchi
- Congruenza

**Direct mapping**
- ogni blocco del livello inferiore (ILI) può essere allocato in una sola specifica posizione del livello superiore (ILS)
$$ILS = ILI\mod N$$
M insiemi da N blocchi

Problema: se il mio programma richiede istruzione e dati appartenenti nello stesso blocco, non riesce a usare altri blocchi cache

| Tag                  | Line  (ILS)                           | Word |
| -------------------- | -------------------------------- | ---- |
| $\qquad\qquad$ | $\qquad\qquad\qquad\qquad\qquad$ |      |
| 8bit                 | 14bit                            | 2bit |
Indirizzo memoria centrale

**Fully associative**
- ogni blocco del livello inferiore può essere posto in qualunque posizione del livello superiore
Problema: si devono fare tanti controlli quanti N blocchi, impiega un maggiore tempo per rilevare hit.

| Tag                                                | Word |
| -------------------------------------------------- | ---- |
| $\quad\qquad\qquad\qquad\qquad\qquad\qquad\qquad$ |      |
| 22bit                                              | 2bit |
Indirizzo memoria centrale

**K-way set associative**
- ogni blocco di uno specifico insieme di blocchi del livello inferiore può essere allocato liberamente in uno specificato gruppo di blocchi del livello superiore
Fa k confronti per controllo tag

| Tag            | Set                      | Word |
| -------------- | -------------------------------- | ---- |
| $\qquad\qquad$ | $\qquad\qquad\qquad\qquad\qquad$ |      |
| 9bit           | 13bit                            | 2bit |
Indirizzo memoria centrale

**Politiche di rimpiazzo cache**
- Casuale, statisticamente mette al riparo dei casi peggiori ma anche migliori;
- First In First Out (FIFO), sostituire il blocco rimasto più a lungo;
- Least Frequently Used (LFU), sostituire il blocco con meno accessi;
- Least Recently Used (LRU), sostituire il blocco meno accesso recentemente. 

**Problema di scrittura**
Come risolvere l’incoerenza tra il blocco in cache e quello nei livelli inferiori.
- ‘Write through’
	La scrittura è contemporanea nel livello di memoria inferiore.
	C’è un aumento di traffico ed è lenta.
- ‘Write back’
	La scrittura in memoria inferiore viene effettuata quando il blocco di cache corrispondente deve essere rimpiazzata.
	Si deve ricordare l’avvenuta della scrittura nel blocco
		- Dirty bit per ogni linea di cache
		- Scrittura di tutto il blocco in memoria inferiore
	Memoria centrale non è più coerente con la cache.

Problema: abbiamo più CPU, ognuna con la propria cache
Soluzioni:
- monitoraggio del bus con write through
- hardware aggiuntivo per trasparenza
- memoria noncacheable

Cache logiche e fisica
MMU = Memory Management Unit
Mapping tra indirizzi fisici e virtuale

I problemi di ’miss’
- Miss di primo accesso
- Miss di capacità insufficiente
- Miss per conflitto, più blocchi mappati sullo stesso gruppo
### 5. Memorie interne
| Tipo   | Categoria   | Cancellabile       | Scrittura | Volatilità |
| ------ | ----------- | ------------------ | --------- | ---------- |
| RAM    | Read-Write  | Electricity, byte  |           | X          |
| ROM    | Read only   | NO                 | Masks     |            |
| PROM   | Read only   | NO                 |           |            |
| EPROM  | Mostly read | UV light, chip     |           |            |
| EEPROM | Mostly read | Electricity, byte  |           |            |
| Flash  | Mostly read | Electricity, block |           |            |

RAM: Random Access Memory
RAM Dinamiche (memoria centrale)
- Condensatore per bit che decade col tempo
- Ha bisogno di un circuito di refresh per essere ricaricata nel tempo e dopo lettura
RAM Statiche (cache)
- Digitale, più complessa
- Solo transistors

Read Only Memory, Programmable Read Only Memory
Erasable PROM, Electrically Erasable PROM

**Codice rilevazione e correzione errori (Hamming)**
Errori possono avvenire per hard failure o soft error
1. Prendo il dato da salvare e lo passo per una funzione che da un codice di controllo unico
2. Li salvo entrambi in memoria
3. Quando richiedo dati dalla memoria, prendo il dato e lo passo per la stessa funzione
4. Comparo i due codici di controllo

Single error correction
Calcoliamo la parità (XOR)
$A=\{1,1,1\},\ B=\{1,1,0\}, C=\{1,1,0\}$
$k_A=1,\ k_B=0,\ k_C=0$
$A=\{0,1,1\},\ B=\{1,1,0\}, C=\{0,1,0\}$

Quanti bit di controllo servono? $2^k-1\geq M+k$
Bit di controllo sono in posizioni a potenza di 2

### 6. Memoria Esterna
**Dischi magnetici HHD**
- Disco rivestito con materiale magnetizzabile 
- Lettura e scrittura delle informazioni tramite bobina/e (head)
- Gli impulsi lettrici passano per la bobina; 0 e 1 memorizzati sotto forma di polarità
- Lettura tradizionale avviene come scrittura
- Lettura moderna realizzata con un sensore MR che rileva le variazioni della corrente che passa dalla testina read
- Testina distanza minima e fissa, Aerodinamica Winchester
- Dischi su più livelli ognuno con bobina
- Suddivisa in tracce(anelli) a sua volta divisa in settori separate da gap (spazi non magnetizzati)
- Blocco solitamente usa tutto il cilindro
Problema: bit vicino al centro sono più valori da quelli in periferia
Soluzione: aumentare gap tra bit in tracce differenti

Processo
- Disco gira finchè bobina arriva a gap
- Legge bit successivi fino a un synch byte
- 
- Gap separa i diversi dati

<u>Tempo per uso</u>
$\text{| Wait for device | Wait for channel |}{T_S\atop\text{ Seek |}} {T_L\atop\text{ Rotational delay }}{T_T\atop\text{| Data transfer |}}$
Seek: spostamento della testina sulla traccia giusta
Rotational delay (latency): rotazione verso settore giusto
Data transfer: $T_T=\frac{b}{rN}$
(b=byte da traferire, N=byte per traccia, r=velocità rotazione)

**RAID**
- Redundant Array of Indipendent Disks
- Tanti dischi, logicamente visti come un solo disco
- Possono memorizzare con ridondanza su diversi disk per backup

RAID0
- Dati di un settore suddivisi in strip memorizzati parallelamente sui dischi

RAID1: RAID0 e il suo specchiato
RAID2: dati salvati in byte/word, Hamming salvato in dischi nelle posizioni corrispondenti
RAID3: Hamming a livello di byte paralleli, salvati in un solo disco
RAID4: dati salvati in blocchi, Hamming a livello di blocchi paralleli
RAID5: Hamming su ogni disco, allocazione a round-robin
RAID6: Hamming e un altro rilevatore a round-robin

**Dischi SSD (Solid State Drive)**
Un transistor con floating gate
Floating gate
- Non attivo, non interagisce con il control gate, bit a 1
- Attivo, oltre una soglia di voltaggio, intrappola elettroni, bit a 0
Gli elettroni nel floating gate, rimangono anche in assenza di corrente.

Memoria flash di tipo NAND
- bit line va a 0 quando tutti i transistor della parola sono attivi (a 1)
- Lettura e scrittura coinvolgono l'intera parola

Necessitano un driver specifico che si interfaccia con l’hardware

Problema: Performance decadono con l’uso
I file sono memorizzate in pagine non contigue raggruppate in blocchi.
La scrittura e la cancellazione avviene a livello di blocco.
Con l’uso i file si frammentano.
Soluzione: Lasciare un buffer libero nei blocchi, cancella dati temp, distribuzione delle scritture, RAID

**Dischi ottici**
- Lettura tramite laser
- Data memorizzata come pit
- Densità di memorizzazione costante
- Velocità lineare costante
- Dischi di policarbonato rivestiti di un materiare riflettente

CD-ROM: sola lettura (650 Mb)
CD_R: scritto una sola volta e poi sola lettura
CD_RW: cancellabile, la scrittura avviene su tutta la traccia

| 00 \| FF...FF \| 00 | MIN \| SEC \| Sector \| Mode |    Data    | Layered ECC |
|:-------------------:|:----------------------------:|:----------:|:-----------:|
|      12 bytes       |           4 bytes            | 2048 bytes |  288 bytes  |
|        SYNC         |              ID              |    Data    |    L-ECC    |

DVD (Digital Video/Versatile Disk): costruzione differente con 2 strati 
che diminuiscono il raggio del laser, usabile in 2 facce (17 Gb).

**Nastro magnetico**
Accesso seriale, utilizzato per backup
## 7. Input e Output

- tendenzialmente sono lenti
- c’è un’interfaccia (modulo I/O) che li gestisce
- hanno un modulo di logica di controllo che comunica con il modulo I/O
- hanno un buffer dati che salva comunicazioni con la CPU

![[IMG_7685.jpg]]

Modulo I/O
La CPU rilega le comunicazioni con i dispositivi al modulo I/O
- ha un buffer delle istruzioni
- data registers tengono dati di lettura e di scrittura
- registri di controllo e status
![[IMG_7686.jpg]]

La logica dell’accesso alla I/O è simile a quello della memoria.

**I/O memory-mapped**
- dispositivi e memoria condividono lo stesso spazio e di indirizzamento
- Problema: non si presta all’uso di cache e non è compatibile con bus multipli
**I/O isolated**
- indirizzamento separato
- commandi speciali I/O

**Gestione I/O**
CPU invia il commando al modulo
- *Programmed I/O*
	CPU controlla un bit di stato che indica il completamento I/O
- *Interrupt driven I/O*
	modulo I/O manda un interrupt alla CPU quando completa
- *Direct memory access (DMA)*
	Il DMA salva i dati direttamente nella memoria centrale. Il controllore DMA manda un interrupt alla CPU quando termina

DMA accede al bus della memoria:
- una parola la volta (cycle stealing)
- per blocchi (burst mode)
In entrambi i casi si blocca l’accesso alla CPU.

Configurazione bus DMA:
- bus singolo, controllore DMA isolato
  bus usato 2 volte: da I/O a DMA, da DMA alla memoria
- bus singolo, DMA integrato con uno o più I/O
- I/O bus separato collegato dal DMA al system bus
## 8. Aritmetica dei calcolatori
ALU = Arithmetic Logic Unit
#### 8.1 Numeri naturali con segno
Uso il bit più a sinistra per il segno (0 positivo, 1 negativo)
Problemi: due rappresentazioni per lo 0, per operazioni tenere conto sia dei moduli che i segni

**\[ Complemento a due \]**
Positivi: da 0 a $2^{n-1}-1$
Negativi: bit più a sinistra a 1, i restanti vanno da -1 a $-2^{n-1}$
Per passare alla sua inversa complementare tutto e sommare 1

Somma e sottrazione normali e sono la stessa operazione (sottrazione è somma dell’inversa). Si devono gestire gli overflow.

Moltiplicazione
Calcolare il prodotto parziale di ogni cifra e sommarli.  
Ciò non funziona se il moltiplicatore è negativo. 
Possibile soluzione: convertire i fattori negativi in positivi, fare la moltiplicazione e poi convertirli al segno dovuto.
Soluzione usata: algoritmo di Booth.

Divisione
Utilizza traslazioni, somme e sottrazioni ripetute.
#### 8.2 Numero reali
Virgola mobile (floating point), specificare dove si trova la virgola
**\[ Floating point \]**
Notazione scientifica
$\pm\text{mantissa}\cdot\text{base}^{\pm\text{esponente}}$
es: $0,000000457=4,57\cdot10^{-7}$

in binario $$\pm1,\text{mantissa}\cdot2^{\text{ esponente polarizzato}}$$esponente polarizzato = esponente $-(2^{k-1}-1)$

|                    | sign | biased exponent | significand |
| ------------------ | ---- | --------------- | ----------- |
|                    | 1bit | 8bit            | 23bit       |
| 4,57 | 0    | 01111000        | 1110010010000000000000 |
bias $=2^{8-1}-1=127$
-7+127=120=01111000

Meno bit vengono usati per l’esponente, meno è la precisione man mano che ci si allontana dallo 0.

*Standard IEEE 754*
- singolo: formato 32bit, 8bit esponente
- double: formato 64bit, 11bit esponente

Binary32 (singolo)
- esponente 0, mantissa 0; 0
- esponente 1, mantissa 0; overflow
- esponente 0, mantissa $\neq0$; numero denormalizzato
- esponente 1, mantissa $\neq0$; Not A Number

*Somma e sottrazione*
1. Controllo dello zero
2. Allineamento delle mantisse (mettiamo esponenti uguali)
3. Somma e sottrazione delle mantisse
4. Normalizzazione del risultato (traslare a sinistra finché cifra è 1)

*Moltiplicazione e divisione*
1. Controllo dello zero
2. Moltiplicazione > Somma degli esponenti meno bias
	Divisione > Sottrazione degli esponenti più bias
1. Moltiplicazione operandi
2. Normalizzazione
3. Arrotondamento

## 9. Linguaggio macchina
Istruzioni che CPU riesce a eseguire
Ne conseguono l’organizzazione della CPU e del sistema

CISC: CPU complessa che snella le istruzioni
RISC: CPU semplice che fa più parallelizzazioni

| Codice operativo | Riferimento operando | Rif operatore | Rif Istruzione successiva |     |
| ---------------- | -------------------- | ------------- | ------------------------- | --- |
| ADD              | A                    | B             | -                         |     |

Istruzioni = sequenza di bit divisa in campi
Rappresentati da simboli (ADD, SUB, LOAD, …, A, B)
- Elaborazione dati: aritmetiche e logiche nei registri CPU
- Trasferimento dati
- Controllo del flusso: ciclo, condizione

Possibile usare
1 indirizzo > accumulatore
0 indirizzi > pila

Meno indirizzi > istruzioni più elementari, CPU più semplice > Più istruzioni
Più indirizzi > istruzioni più complesse > Meno istruzioni

Decimali impaccati usati in I/O
Cifre decimali in 4bit (0=0000, …, 9=1001)
es: 246 = 0010 0100 0110

Codice ASCII (8bit)
7bit carattere e 1bit di parità
ora UTF8

Dati logici: n bit invece di singolo dato, per manipolare bit separatamente
##### Dati x86
Indirizzamento per unità di 8bit
Non necessario allineamento di indirizzi
Memoria divisa in segmenti (seg per dati, seg per operandi)

| Tipo di dato |                              |
| ------------ | ---------------------------- |
| Near pointer | Indirizza dentro ai segmenti |
| Far pointer  | Indirizza il segmento        |

Operazioni logiche
AND utile per maschere con cui puoi selezionare solo i bit interessati
Shift 
Salto condizionato (branch)
Salto incondizionato (skip)
- ISZ (Increment and Skip If Zero), utile per cicli

Procedura: pezzo di programma con un nome che può essere chiamato
Salvo l’indirizzo di RETURN in
- un registro
- inizio della procedura chiamata
Entrambe queste opzioni non permettono la ricorsione
- cima di una pila

*Modi di indirizzamento*
- **Immediato**, l’operando è parte dell’istruzione
	\[Cod Op\]\[Operando\]
	Pro: nessun accesso alla memoria
	Contro: limitato dalla dimensione del campo operando
- **Diretto**, indirizzo dell’operando in memoria
	\[Cod Op\]\[indirizzoOp\]
	Contro: limitato dalla dimensione del campo indirizzo
- **Indiretto**, indirizzo al puntatore dell’operando in memoria
	\[Cod Op\]\[puntatoreOp\]
	Contro: due accessi alla memoria
- **Registro**, indirizzo dell’operando in registro
	\[Cod Op\]\[registroOp\]
	Contro: limitati operandi nei pochi registri
- **Registro indiretto**, indirizzo al puntatore in registro dell’operando in memoria
	\[Cod Op\]\[regisPuntatoreOp\]
- **Spiazzamento**, indirizzo relativo a uno di base
	\[Cod Op\]\[regisPuntatoreOp\]\[indirizzoAdd\]
	Nei salti si aggiunge indirizzoAdd al program counter.
	- **Indicizzazione**, indirizzo incrementale da uno di base
	- **Pila**, indirizzo alla cima della pila
	Usa segmenti

Lunghezza istruzioni dipende da
- Dimensione della memoria
- Organizzazione della memoria
- Struttura del bus
- Complessità CPU
- Velocità CPU

| Opcode | Direct/Indirect | Zero/Current | Displacement |
| ------ | --------------- | ------------ | ------------ |
| 0-2    | 3               | 4            | 5-11         |

| 1 1 0 | Device | I/O command |
| ----- | ------ | ----------- |
| 0-2   | 3-8    | 9-11            |
1110
PDP-8 Instruction

| Opcode | Register | D/I | Index Register | Memory address |
| ------ | -------- | --- | -------------- | -------------- |
| 0-8    | 9-12     | 13  | 14-17          | 18-35          | 
PDP-10 Instruction

PDP-11
- 8 registri da 16bit, di cui 1 come stack pointer e 1 come PC
- 13 formati, inclusi operazioni con 0,1 e 2 operatori
- Opcode a lunghezza variabile
- Riferimenti a registri di 6bit
- Set di istruzioni complesso (CISC)

x86

**Registri utente** visibili in linguaggio macchina, usati dal ”programmatore”
- Uso generale
- Specifici
È possibile usare due registri come uno solo (“double”)

**Registri di controllo e di stato** usati dalla CPU, generalmente non visibili
- Program Counter (PC)
- Instruction Register (IR)
- Memory Address Register (MAR)
- Memory Buffer Register (MBR)
- Altri..

### Pipeline
Predecessore **Prefetch**
$\text{Fetch istruzione dalla memoria}\begin{aligned} &> \text{Execute nei registri}\\ &> \text{Fetch dell’istruzione successiva}\end{aligned}$
Servono registri aggiuntivi
Non raddoppia le prestazioni: 
- il fetch è più breve dell’ execute, 
- non tiene in conto le istruzioni di salto e branch

**Parallelismo**
Con multipli core

|       | T1  | T2  | T3   |
| ----- | --- | --- | ---- |
| Core1 | La  | vo  | ro 1 |
| Core2 | La  | vo  | ro 2 |
| Core3 | La  | vo  | ro 3 | 
Parallelismo totale
ma se c’è dipendenza funzionale tra un lavoro e il suo successivo?

|       | T1      | T2      | T3      | T4      | T5      |
| ----- | ------- | ------- | ------- | ------- | ------- |
| Core1 | *1-fase1* | *1-fase2* | *1-fase3* |         |         |
| Core2 |         | **2-fase1** | **2-fase2** | **2-fase3** |         |
| Core3 |         |         | <u>3-fase1</u> | <u>3-fase2</u> | <u>3-fase3</u> | 
Dipendenza funzionale con esecutori generici
- ogni esecutore ha le risorse per eseguire ogni fase: **ridondante**

|       | T1      | T2      | T3      | T4      |         |
| ----- | ------- | ------- | ------- | ------- | ------- |
| Core1 | *1-fase1* | **2-fase1** | <u>3-fase1</u> |         |         |
| Core2 |         | *1-fase2* | **2-fase2** | <u>3-fase2</u> |         |
| Core3 |         |         | *1-fase3* | **2-fase3** | <u>3-fase3</u> | 
Dipendenza funzionale con esecutori specializzati
- ogni esecutore ha solo le risorse per eseguire quella fase

Fetch >r1> Decode >r2> Data >r3> Execute >r4> Write
Tra fase ci sono buffer (registri) che salvano dati utili per la face successiva

Pipeline
- fetch (FI)
- decodifica (DI)
- calcolo operandi (CO)
- fetch operandi (FO)
- esecuzione (EI)
- scrittura (WO)

|        | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   |
| ------ | --- | --- | --- | --- | --- | --- | --- | --- |
| Instr1 | FI  | DI  | CO  | FO  | EI  | WO  |     |     |
| Instr2 |     | FI  | DI  | CO  | FO  | EI  | WO  |     |
| Instr3 |     |     | FI  | DI  | CO  | FO  | EI  | WO  | 

$$\tau=\max_i[\tau_i]+d=\tau_m+d\qquad1\leq i\leq k$$$\tau$ è il tempo massimo di ciclo per avanzare di una fase/stadio
$\tau_m=\max_i[\tau_i]$ è il massimo ritardo di stadio 
$d$ è il ritardo di commutazione di registro
$$T_k=[k+(n-1)]\tau$$$T_k$ è tempo totale richiesto da una pipeline con $k$ stadi per $n$ istruzioni

**Speedup** (fattore di velocizzazione)$$S_k=\frac{T_l}{T_k}=\frac{nkt}{[k+(n-1)]t}=\frac{nk}{[k+(n-1)]}$$dove $T_l$ è il tempo totale con $n$ istruzioni senza pipeline

*Pipeline hazards*
- **Sbilanciamento delle fasi**, 
	Le <u>fasi hanno durate diverse</u> e si deve attendere la fine delle fasi precedenti per accedere o passare i registri.
	Soluzioni: decomporre le fasi più lunghe, duplicare gli esecutori delle fasi pesanti e farli operare in parallelo.
- **Structural hazards**
	Delle fasi dello stesso ciclo devono <u>accedere a una stessa risorsa</u>.
	Soluzioni:
	- Introdurre di fasi non operative
	- Suddividere le memorie permettendo accessi paralleli
- **Data hazards**
	Un’istruzione ha bisogno di <u>dati che dipendono da istruzioni</u> precedenti.
	Soluzioni: 
	- Introdurre fasi non operative finché i dati sono disponibili
	- Usare circuiti di data forwarding per propagare in avanti l’ output
	- Riordino delle istruzioni dal compilatore e/o CPU
- **Control hazards (Delayed Branch)**
	Ci sono istruzioni che <u>alterano la sequenzialità</u> (salti, chiamate, ritorni, interruzioni).
	Soluzioni:
	 - Fasi non operative, semplice ma inefficiente
	 - Apposita logica di controllo, complica il compilatore e hardware
	Soluzione salti condizionati:
	- Flussi multipli (multiple streams)
		Replica la prima parte della pipeline per entrambi i rami possibili 
	- Prefetch dell’istruzione target
		Anticipa l’istruzione target del salto, scarto se non preso
	- Buffer circolare (loop buffer)
		una piccola memoria che mantiene le ultime n istruzioni prelevate, utile nel caso di loop
	- Predizione salti
		2bit di predizione, predice il salto fino a 2 errori dopo di che predice che non avviene
		$\begin{align}&\text{predict taken }[11]\xtofrom[\text{not taken}]{\enspace\text{taken}}&\text{predict taken }[10]\\&\uparrow{\text{taken}}&\downarrow\text{not taken}\\&\text{predict not taken }[01]\xtofrom[\text{taken}]{\text{not taken}}&\text{predict not taken }[00]\end{align}$		

### Filosofia RISC 
Per semplificare l’implementazione hardware di operazioni, variabili e flusso.

Le operazioni più usate in frequente sono
ASSIGN, LOOP, CALL, IF, OTHER
Dove OTHER comprende le operazioni complesse (CISC)

Le variabili più usate sono
Costanti intere, Variabili scalari, Array/Strutture
Dove Array/Structure sono quelli meno usati

Chiamate di procedura sono complessi da gestire, si deve gestire gli argomenti e tenere conto del livello di annidamento.
Possibile salvare i dati nei in una finestra (gruppo) di registri.

| Parameter registers                                                                               | Local registers  | Temporary registers                                               |
| ------------------------------------------------------------------------------------------------- | ---------------- | ----------------------------------------------------------------- |
| parametri passati all’invocazione della procedura corrente e il valore da restituire al chiamante | variabili locali | per scambio di parametri e valore di ritorno con procedura nested |

![[IMG_7709.jpg]]
e così via, per tutti i livelli di annidamento.

I registri sono limitati
- si salvano solo i dati più recenti
- la procedura meno recente va salvata in memoria quando la finestra di registri nuova vi ci sovrappone
questa organizzazione è detta a **buffer circolare**.

Le variabili globali possono essere salvate in un gruppo di registri ad hoc disponibili a tutte le procedure.

I registri simbolici (infiniti) non corrispondono 1 a 1 con i registri locali (finiti). Usa teoria dei grafi per approssimare una disposizione efficiente.
##### MIPS (32bit)
Una particolare architettura RISC
- Tutte le istruzioni a 32bit
- Tutte le operazioni sui dati sono da registro a registro
- Le operazioni sulla memoria sono solo load e store (tra memoria e registro)

3 formati per istruzioni
`             6bit   5b  5b  5b  5bit   6bit`
**R** (register)     `[codop][rs][rt][rd][shamt][funct]`
**I**  (immediate) `[codop][rs][rt][ address/const  ]`
**J** (jump)          `[codop][target address          ]`

rs = register source
rt = register target
rd = register destination
shamt = shift amount
funct = tipo di variabile

1. **IF**: Instruction Fetch
2. **ID**: Instruction Decode
	- formato R `A <- Reg[rs], B <- Reg[rt]`
	- formato I   `A <- Reg[rs], Imm`
	- formato J `Imm <- campo immediato di IR`
3. **EX**: Execution / Address calculation
4. **MEM**: Memory access / Branch completion
5. **WB**: Write back

Banchi di registri tra una fase all’altra per la pipeline
1. IF/ID
	- `.IR <- Mem[PC]`
	- `.NPC <- if((EX/MEM.IR==branch) && EX/MEM.Cond) then (EX/MEM.Target) else (PC+4)` 
2. ID/EX
	- `.IR <- IF/ID.IR`
	- `.NPC <- IF/ID.IR`
	- `.TopAluOutput <- Reg[IF/ID.IR[rs]]`,
	  `.BottonAluOutput <- Reg[IF/ID.IR[rt]]`
	- `.Imm <- sign-extend (IF/ID.IR[Immediate field])`
3. EX/MEM
	- `.IR <- ID/EX.IR`
	Istruzione aritmetico-logica
	- `.ALUOutput <- ID/EX.A op ID/EX.B (oppure ID/EX.Imm)`
	Istruzione load/store
	- .`Target <- ID/EX.A + ID/EX.Imm`
	- `.B <- ID/EX.B`
	Istruzione salto
	- `.Cond <- `
5. MEM/WB
	-  `.IR <- EX/MEM.IR`
	- `.ALUOutput <- EX/MEM.ALUOuput`
	- `.LMD <- `

**Dipendenze Read After Write**
```
LW $1, 45($2)    ; [IF][ID][EX][MEM][WB]
ADD $5, $6, $7   ;     [IF][ID]nop [EX][MEM][WB]
SUB $8, $6, $7   ;         [IF]nop [ID][EX][MEM][WB]
OR $9, $6, $7    ;             nop [IF][ID][EX][MEM][WB]
```

| Linea codice     | Situazione                                 | Azione                                           |
| ---------------- | ------------------------------------------ | ------------------------------------------------ |
| `LW $1, 45($2)`  | Nessuna dipendenza                         | Non occorre fare nulla                           |
| `ADD $5, $6, $7` | Dipendenza che richiede stallo             | Rileva l’uso di `$1` ed evita il rilascio di ADD  | 
| `SUB $8, $6, $7` | Dipendenza risolvibile con data forwarding | Rileva l’uso di `$1` e propaga MEM/WB.LMD alla ALU |
| `OR $9, $6, $7`  | Con accessi in ordine                      | Non occorre fare nulla                           |

Controllo di hazard è obbligatorio.
Unità data forwarding può non esserci.

### Multicore
Una CPU può essere
- **Superscalare**
	CPU con 
- Multithreading
- **Multicore**
	Ogni core è una CPU con propria cache di primo livello e una cache condivisa di secondo livello. Le CPU possono essere super scalari o 

Un singolo core grande è più performante di multipli core di stessa grandezza sommata. 

Le architetture multicore possono essere organizzate in
- numero core
- grandezza logica di controllo
- grandezza cache