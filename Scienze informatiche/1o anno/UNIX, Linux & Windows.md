# Gestione memoria
### UNIX
`fork()` duplica l’intero processo
page daemon, verifica con periodo 1/4s che in RAM ci siano $\geq$ lotsframe
### GNU/Linux
Spazio suddiviso in regioni = conseguenze contigue di pagine
Ogni regione ha un descrittivo.

`fork()` replica l’intera lista di descrittori del padre
Le pagine del figlio vengono duplicate solo se modificate (copy on write)
Page daemon, ogni s cerca le pagine da spostare in disco
RAM dinamica e variabile
Algoritmo di allocazione buddy
## Windows
Un daemon di kernel ogni 1s  

# Gestione I/O
### UNIX
UNIX tratta i dispositivi I/O come file speciali
Il gestore **device driver** è unico per ogni dispositivo o famiglia di dispositivi dello stesso tipo

### GNU/Linux
GNU/LInux ha un caricamento dinamico dei dispositivi
1. Rilevazione dello spazio di indirizzamento
2. Allocazione delle risorse necessarie
3. Configurazione delle interruzioni
4. Inizializzazione del gestore

Connessione rete usa un file speciale (**socket**)
- Connessione affidabile flusso di caratteri (~TCP) o di pacchetti (TCP)
	Correzione errori ricade al gestore
- Trasmissione inaffidabile di pacchetti (UDP)
	Correzione errori ricade all’utente

# Android
2007
Architettura ARM, sistema Open Source
Usato per diversi dispositivi
- Grande importanza a reattività e interattività user
- Tiene conto del consumo della batteria dei processi
- Non ha spazio swap, usa _out-of-memory-killer_ per chiudere processi
- Sandbox di permessi
