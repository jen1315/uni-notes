# Numeri binari

$\begin{align*}[\ 100\ |\ 101\ |\ 110\ ]_{2} &= [\ 4\ |\ 5\ |\ 6\ ]_{8} &\text{ottale}\\ [\ 0001\ |\ 0010\ |\ 1110\ ]_{2} &= [\ 1\ |\ 2\ |\ E\ ]_{16} &\text{esadecimale}\end{align*}$

$302_{10} = 100101110_{2} = 456_{8} = 12E_{16}$

*Complemento a due*
- numeri positivi, numeri binari preceduti da 0, $3=011$
- numeri negativi, $-3=-(011)=\overline{011}+1=101$

*Floating point*
$-/+ 1.\text{mantissa}\cdot2^{\text{ esponente}}$
$\text{esponente} = eq-(2^{\text{bit esp}-1}-1)$

IEEE 754
- singolo: 32bit, 8bit esponente
- double: 64bit, 11bit esponente

$2^{\text{bit esp}-1}-1=2^{8-1}-1=127$
$-3.5=-(11.1)=1\ 1.11000...\cdot2^{128-127}=1\ 10000000\ 11000000000000000000000$
# Cache

*Associazione completa*
Non ha line \[ tag | word ]

*Associazione diretta*
$\begin{rcases}ILS=\text{Indirizzo Livello Superiore }\\ ILI=\text{Indirizzo Livello Inferiore }\end{rcases}\ ILS = ILI\mod B$
indirizzo \[ tag | line | word ]

*Associazione k-way*
$C$ dimensione cache
$P$ dimensione parola
$B$ dimensione blocco
$k$-vie associazione

> Trova indirizzo binario

indirizzo \[ tag | set | word ]
tag = indirizzo-set-word 
set = $\log_{2}\ [(C/B)/k]$
word = $\log_2(C/P)$
# Codice Hamming

> Scrivi codice Hamming di 11001010.

| 12   | 11   | 10   | 9    | *8*    | 7    | 6    | 5    | *4*    | 3    | *2*    | *1*    |
| ---- | ---- | ---- | ---- | ------ | ---- | ---- | ---- | ------ | ---- | ------ | ------ |
| 1100 | 1011 | 1010 | 1001 | *1000* | 0111 | 0110 | 0101 | *0100* | 0011 | *0010* | *0001* |
| 1    | 1    | 0    | 0    | *0*    | 1    | 0    | 1    | *1*    | 0    | *0*    | *1*    |
Nelle posizioni di potenza di 2, ci sono i bit di controllo.
I bit di controllo si calcolano facendo l'XOR dei bit dati la quale posizione in binario ha i bit di controllo.

$\begin{align*}p1&=p3\oplus p5\oplus p7\oplus p9\oplus p11&=0\oplus1\oplus1\oplus0\oplus1=1\\ p2&=p3\oplus p6\oplus p7\oplus p10\oplus p11&=0\oplus0\oplus1\oplus0\oplus1=0\\ p4&=p5\oplus p6\oplus p7\oplus p12&=1\oplus0\oplus1\oplus1=1\\ p8&=p9\oplus p10\oplus p11\oplus p12&=0\oplus0\oplus1\oplus1=0\end{align*}$
# Dischi magnetici

$T=T_S+T_L+T_T$
$T_S=$ tempo di seek
$T_L=$ tempo di latenza (rotazione) 
$T_T=$ tempo di trasferimento dati
$$T_L=\frac{1}{2r}\cdot1000
\qquad T_T=\frac{b}{rN}\cdot1000$$
$b=$ n# byte da trasferire
$N=$ n# byte per traccia
$r=$ velocità di rotazione al secondo

$\displaystyle N=\frac{\text{capacità disco}}{facce}\backslash\text{tracce per faccia}$

# Pipeline

| 1   | 2   | 3   | 4   | 5   |
| --- | --- | --- | --- | --- |
| IF  | ID  | EX  | MEM | WB  |

*Data forwarding*
EX/MEM.AluOutput
MEM/WB.AluOutput e MEM/WB.LMD
-> ID/EX.TopAluInput o ID/EX.BottomAluInput

