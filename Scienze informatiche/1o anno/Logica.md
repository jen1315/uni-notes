In questo corso impariamo la logica di Aristotele

_Vedi diapositiva 5/09_
linguaggio formale <=> linguaggio di programmazione
derivazione formale <=> programma

In logica una affermazione si distingue in 
- Vera (=tautologia),
- Paradosso (=contraddizione),
- Opinione

La negazione del Paradosso è Verità.

Procedure automatiche, non hanno bisogno di input umano
Procedure semi-automatiche

Verità si distingue in
- logica
- teorica
TEORIA = LOGICA + assiomi

_Vedi diapositiva 9/09_
linguaggio formale SINTASSI
linguaggio naturale SEMANTICA

Comporre proposizioni con parole e segni
Variabili proposizioni $A,B,C,…,Z$

| Negazione | Implicazione  | Congiunzione | Disgiunzione | Equivalenza |
| --------- | ------------- | ------------ | ------------ | ----------- |
| $\neg$    | $\rightarrow$ | $\&$         | $\vee$       | $\leftrightarrow$            |

Ogni variabile proposizionale è ATOMICA
$\neg(F)$ che sta per _NON si dà il caso che $F$_
$(\neg(F))\rightarrow(W)$ che sta per _se NON si dà il caso $F$ allora $W$_

| simboli       | Per CONVENZIONE                                                                               |
| ------------- | --------------------------------------------------------------------------------------------- |
| $A,B,…,Z$     | Possiamo togliere le parentesi a tutte le proposizioni atomiche.                              |
| $\neg$        | senza parentesi si lega a una proposizione atomica o negata $\neg$ e ha la priorità più alta. |
| $\vee,\&$     | senza parentesi si legano a proposizioni atomiche o negate $\neg$ e hanno stessa priorità.    |
| $\rightarrow$ | si lega tutto il resto e ha la priorità più bassa.                                            |

_Vedi diapositiva 12/10_
“Se parli parli altrimenti non parli”. Tautologia(sempre vera)?
1. $(P\rightarrow P)\vee\neg P$
2. $P\rightarrow P\vee\neg P$

| $P$ | $P\rightarrow P$ | $\neg P$ | $(P\rightarrow P)\vee\neg P$ | $P\rightarrow P\vee\neg P$ |
| --- | ---------------- | -------- | ---------------------------- | -------------------------- |
| 0   | 1                | 1        | 1                            | 1                          |
| 1   | 1                | 0        | 1                            | 1                           |

Tabella di verità di una proposizione
$\text{Tab}_{\text{conn}(V_1,…,V_n)}:\{0,1\}^n\rightarrow\{0,1\}$

$A\oplus B\equiv(A\vee B)\&\neg(A\& B)$

| $A$ | $B$ | $A\rightarrow B$ |
| --- | --- | ---------------- |
| 0   | 0   | 1                |
| 0   | 1   | 1                |
| 1   | 0   | 0                |
| 1   | 1   | 1                | 
Implicazione

$(A\rightarrow B)\equiv\neg A\vee B$

$A\leftrightarrow B$ = proposizioni $A$ e $B$ la stessa tabella di verità.

Classificazione in logica classica delle proposizioni pr
- pr TAUTOLOGIA: tutte le uscite 1
- pr OPINIONE: almeno una uscita 1 e almeno una 0
- pr PARADOSSO: tutte le uscite 0

Strategie per classificare pr
1. Tabella di verità, fai tabelle di verità di $pr$
2. Matematica, riduci $pr$ tramite equivalenze note a tautologia classica
3. Sequenti, deriva $pr$ come sequenti

Calcolo dei sequenti
= costruire gli alberi di derivazione con sequenti come nodi

costante falso $\bot=0$
costante vero $tt=1$

Sequenti $LC_p$: nel linguaggio delle proposizioni formali, è la scrittura che può essere
1. $pr_1,pr_2,…,pr_n\vdash cl_1,cl_2,…,cl_m$
	è equivalente a $(pr_1\ \&\ pr_2)…\&\ pr_n\rightarrow(cl_1\vee cl_2) …\vee cl_m$
2. $\vdash cl_1,cl_2,…,cl_m$
	è equivalente a $tt\rightarrow(cl_1\vee cl_2)…\vee cl_m$
3. $pr_1,pr_2,…,pr_n\vdash$
	è equivalente a 
4. $\bot$

Albero: foglie sono assiomi, implica

Albero di derivazione:

### Validità e Sicurezza di una Regola
_dispositiva 26/10_
$$\frac{\Gamma_1\vdash\Delta_1}{\Gamma_2\vdash\Delta_2}$$
Una regola si dice **valida** quando la premessa è falsa o è vera e l’implicazione è vera.
La sbarra è una implicazione.

| $\Gamma_1^\&\rightarrow\Delta_1^\vee$ | $\Gamma_2^\&$ | $\Delta_2^\vee$ | $(\Gamma_1\rightarrow\Delta_1)\rightarrow(\Gamma_2\rightarrow\Delta_2)$ |
|:--------------------------------:|:-------------:|:---------------:|:-----------------------------------------------------------------------:|
|                0                 |       -       |        -        |                                    1                                    |
|                -                 |       0       |        -        |                                    1                                    |
|                1                 |       1       |        1        |                                    1                                    |
|                1                 |       1       |        0        |                                    0                                    | 

È importante trovare la riga falsaria se esiste.
L’unico caso da controllare è la conclusione della conclusione quando tutti gli altri vanno a 1

Una regola si dice **sicura** quando lei e le sue inverse sono valide.
L’inversa di una regola
$$\text{reg}=\frac{\Gamma\vdash\Delta}{\Gamma’\vdash\Delta’}\qquad\text{inv(reg)}=\frac{\Gamma’\vdash\Delta’}{\Gamma\vdash\Delta}$$$$\text{reg}=\frac{\Gamma_1\vdash\Delta_1\qquad\Gamma_2\vdash\Delta_2}{\Gamma’\vdash\Delta’}\qquad\text{inv(reg)}=\frac{\Gamma’\vdash\Delta’}{\Gamma_1\vdash\Delta_1},\quad\frac{\Gamma’\vdash\Delta’}{\Gamma_2\vdash\Delta_2}$$
#### Teoria scientifica
$\begin{aligned}\text{Teoria proposizionale} &=\text{calcolo logico per }LC_p\\&+\text{assiomi}\\&+\text{regola di composizione}\\&\frac{\vdash fr\quad\Gamma,fr,\Gamma’\vdash\nabla}{\Gamma,\Gamma’\vdash\nabla}comp\end{aligned}$ 

Una formula $fr$ è detta teorema di una teoria $T$ se il sequente $\vdash fr$ è derivabile in $T$.
Le tautologie classiche sono nella base di ogni teoria.

Il calcolo $LC_p$ NON è contraddittorio perché $\vdash\bot\ (tt\rightarrow\bot)$ NON è derivabile e NON è tautologia.

Usare $comp$ (composizione) per derivare $fr$:
- assiomi
- componi con teoremi già noti
$$\frac{\vdash Ax\quad Ax\vdash fr}{\vdash fr}comp\qquad\frac{\vdash T\quad T\vdash fr}{\vdash fr}comp$$
#### Predicati
_diapositiva 31/10_
Sillogismo = tautologia
$$\begin{aligned}F(x):&\text{nomi di enti}&\rightarrow\qquad&\text{proposizioni}\\&s&\rightarrow\qquad&F(x)\end{aligned}$$
$F(x)$ che a ogni $x$ associa una proposizione $F$ 
ove $x$ è una variabile per enti

Quantificatore universale $\forall$
$$\underbrace{\forall x\ P(x)}_{\text{per ogni x vale P(x)}}$$
Quantificatore esistenziale $\exists$
$$\underbrace{\exists x\ P(x)}_{\text{esiste x per cui vale P(x)}}$$

| simboli     | usati per         |
| ----------- | ----------------- |
| $a,b,…,h$   | costanti          |
| $A(x),C(x_1,…x_n),M(x_1,…,x_m)$ | predicati atomici |
| $w,x,y,z;\ x_1,…,x_n$   | variabile         | 

Priorità delle parentesi
$$\neg,\forall,\quad\text{ lega più di }\quad\vee,\&\quad\text{ lega più di }\quad\rightarrow$$
**Variabili vincolate**
$x$ si dice libera in $t_{ter}$ se $x\in VL(fr)$

##### Linguaggio predicativo di $\mathcal{L}_{\text{PA}}$
Aritmetica di Peano

**Costante**
- $0=$ “numero zero”

**Funzioni**
- $s(x)=$ “successivo x+1 di x”
- $x+y=$ “somma di x con y”
- $x\cdot y=$ “moltiplicazione x con y”

**Assiomi**
- $Ax1.\vdash\forall x\ s(x)\neq0$
	“ogni numero successore è diverso da zero”
- $Ax2.\vdash\forall x\forall y(s(x)=s(y))\rightarrow x=y)$
	“ogni numero successore è iniettiva”
- $Ax3.\vdash\forall x\ x+0=x$
	“lo zero è elemento neutro della somma”
- $Ax4.\vdash\forall x\forall y\ x+s(y)=s(x+y)$
	”definizione di somma”
- $Ax5.\vdash x\ x\cdot0=0$
	“zero è annullatore del prodotto”
- $Ax6.\vdash\forall x\forall y\ x\cdot s(y)=x\cdot y+x$
- $Ax7.\vdash fr[x/0]\&\forall x(fr\)$
