# Reti Logiche

## Formule algebriche

$xy+\overline{x}z+yz=xy+\overline{x}z$
$x+\overline{x}y=x+y$
$x+xy=x$
$x+x=x$

Note: Se si sostituisce _ con + e + con _ si ottengono teoremi e formule duali

## Teorema di Bool-Shannon

$f(x_1,x_2,x_3,...x_n)=x_1*f(1,x_2,x_3,...,x_n)+\overline{x_1}*f(0,x_2,x_3,...,x_n)$

## 1° Forma canonica (SOP)

$\sum{P_i}=P_1+P_2+...+P_n$ dove $P_i$ è $\begin{cases}1\\Un\ letterale\\Prodotto\ di\ letterali \end{cases}$

Un termine prodotto viene detto **Implicante** e un termine prodotto con tutte le variabili viene detto **Mintermine**

## 2° Forma canonica (POS)

$\prod{S_i}=S_1*S_2*...*S_n$ dove $S_i$ è $\begin{cases}0\\Un\ letterale\\Somma\ di\ letterali\\ \end{cases}$

Un termine somma viene detto **Implicato** e un termine prodotto con tutte le variabili viene detto **Maxtermine**

## Mappe di Karnaugh

Una funzione è definita da 3 set (ne bastano due)
$\sum{(1,2...)}: On-Set$
$\Phi(3,4,...): Off-Set$
$\Delta(5,6,...): DC-Set$

Tabella e rappresentazione dei cubi:
<img src="img\Karnaugh.png" height=500>

### Costruzione implicante raggruppando gli 1

In un cubo si moltiplicano i letterali delle variabili che non cambiamo di valore all'interno del cubo prese così come sono se il loro valore è 1, prese negate se il valore è 0.

Note: Si prendono sempre i cubi + grandi possibili sfruttando i cubi
Note: Il numero di letterali di un mintermine è: $\#Variabili-DimensioneCubo$
Note: La dimensione del cubo parte da 0

### Costruzione forma SoP

Tutti gli implicanti vengono sommati tra di loro

### Costruzione implicato raggruppando gli 0

In un cubo si sommano i letterali delle variabili che non cambiano di valore, prese come non negate se il loro valore rimane 0, prese negate se il loro valore è 1

### Costruzione forma PoS

Si moltiplicano tutti gli implicanti ottenuti

## Quine-McCluskey

Passi:

1. Si codifica sia l'on-set e il dc-set
2. Si raggruppano per numero di 1 (gruppo con zero 1, gruppo con un 1,...)
3. Si crea una nuova lista confrontando gli elementi di ogni gruppo con i tutti gli elementi del gruppo successivo, se gli elementi hanno solo 1 bit che differisce, allora quel bit diventa - e tutti gli altri rimangono uguali es:(0:0000 e 1:0001 diventa 0,1:000-; 0,1:000- e 2,3;001- diventa 0,1,2,3:00--)
   3.1. Ogni elemento in grado di accoppiarsi viene segnato
   3.2. Si conclude la costruzione della lista quando non è più possibile accoppiare elementi
4. Tutti gli elementi non segnati sono implicanti primi (essenziali, ridondanti e ridondanti secondari)

### Metodo di Petrik

Si costruisca una tabella che ha come colonne tutti gli elementi dell'On-Set e come righe gli implicanti primi, si indichi con una x i valori coperti da un implicante. Es:

$$
\begin{array}{l|l|l|l}
Implicante & 1 & 2 & 3 \\
\hline
p1 & x & & x \\
p2 & x & x& x
\end{array}
$$

Un implicante è primo nella tabella di petrik se copre una colonna dove solo lui ha una X (es:p2)

Passi:

1. Si identificano gli implicanti primi, si mettono nella copertura $C(f)=\{p_i,p_j,...\}$
2. Si toglie dalla tabella di Petrik tutti i valori coperti dagli implicanti primi
3. Si risolvono eventuali dominanze di righe e colonna
4. Si identificano eventuali nuovi implicanti "primi" notati tramite dominanze e si risvolge il punto 2
5. Si ottiene la copertura totale (allora fine) oppure una tabella ciclica (No implicanti primi, ma solo ridondanti secondari)

#### Dominanza di riga

TODO

#### Dominanza di colonna

TODO

#### Risoluzione tabella ciclica

Si definisce funzione di copertura$C(f)=\prod{c(f_i)}$
Dove $c(f_i)$ sono tutti gli implicanti che coprono il corrispettivo valore dell'on-set
Per risolvere una tabella ciclica si fa quindi la produttoria di tutti gli implicanti che coprono un dato valore
Es:
Presa la seguente tabella ciclica

$$
\begin{array}{l|l|l|l}
Implicante & 1 & 2 & 3 \\
\hline
p1 & x & x&  \\
p2 & x & & x \\
p3 & & x & x
\end{array}
$$

=> La funzione di copertura diventa $c(f)=(p_1+p_2)(p_2+p_3)(p_1+p_3)$
=> $(p_1*p_2+p_1*p_3+p_2+p_2*p_3)(p_1+p_3)$
=> $(p_1*p_3+p_2)(p_1+p_3)$
=> $p_1*p_3+p_1*p_2+p_2*p_3$ Ognuno di queste coppie di implicanti copre perfettamente la funzione, ora, minimizzando il costo (come numero di letterali) della funzione si prenderà quella che ha meno implicanti

## Quine-McCluskey multifunzione

TODO

## Metodi euristici

TODO

## Componenti

### MUX

<img src="img\mux.png" height=100/>

#### Info

| $Z=A*\overline{S}+B*S$ | $T_D=2$ <br> $\#Porte=3*\#bit$ |
| ---------------------- | ------------------------------ |

Note: Richiede 3 porte per bit poichè ci sono 2 AND + 1 OR per scegliere tra il bit $a_i$ o $b_i$

### Decoder

TODO

### Half Adder

<span style="display:flex; flex-direction:row;">
<img src="img\halfadder.png"/>

$$
\begin{array}{ll|l|l}
x & y & S & C \\
\hline
0 & 0 & 0& 0 \\
0 & 1 & 1& 0 \\
1 & 0& 1 & 0 \\
1 & 1& 0 & 1
\end{array}
$$

</span>

#### Info

| $S=x\oplus y$ <br> $C=x*y$ | **$T_D=1$** //Formule ad 1 livello <br> **$\#Porte=2$** //1 per S e 1 per Cs |
| -------------------------- | ---------------------------------------------------------------------------- |

### Full Adder

<span style="display:flex; flex-direction:row;">
<img src="img\fulladder.png"/>

$$
\begin{array}{lll|l|l}
x & y & C_i & S_i & C_{i+1} \\
\hline
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 1 & 0 \\
0 & 1 & 0 & 1 & 0 \\
0 & 1 & 1 & 0 & 1 \\
1 & 0 & 0 & 1 & 0 \\
1 & 0 & 1 & 0 & 1 \\
1 & 1 & 0 & 0 & 1 \\
1 & 1 & 1 & 1 & 1
\end{array}
$$

</span>

#### Info

| $S=x\oplus y \oplus C_i$ <br> $C=xy+yc+xc$ | **$T_D=2$** //Formule ad 1 livello <br> **$\#Porte=6$** // (2 xor, 3 and, 1 or) |
| ------------------------------------------ | ------------------------------------------------------------------------------- |

### Sommatore RCA (Ripple-Carry-Save)

![img](img\rca.png)

#### Info

|                  |                                                                                                                       |
| ---------------- | --------------------------------------------------------------------------------------------------------------------- |
| $T_D=2*\#FA$     | Ritardo 2 a FA, sono messi in cascata (per produzione del riporto)                                                    |
| $\#Porte=6*\#FA$ | Ogni FA richiede 6 porte, il numero di FA dipende dal numero di bit degli operandi, gli operandi invece sono sempre 2 |

### Sommatore Carry Look-Ahead

Il problema dell'RCA è il ritardo che si ha nel calcolo del riporto, anticipando il calcolo è possibile migliorare le prestazioni.

#### Generazione e propagazione

$C_{i+1}=x_i*y_i+x_i+c_{i}*y_i+c_{i}*x_i$
$G_i=x_i*y_i$ Generazione: 1 AND
$P_i=x_i+y_i$ Propagazione: 1 OR
$C_{i+1}=G_i+P_i*C_i$
$A_{GP}=(1or+1and)*n bit=2nbit$

#### Carry Look-Ahead

Calcolo del riporto
$C_0=C_0$
$C_1=G_0+P_0*C_0$ //1 OR + 1 AND
$C_2=G_1+P_1*C_1=G_1+P_1*(G_0+P_0*C_0)=G_1+P_1*G_0+P_1*P_0*C_0$ //1 OR + 2 AND
=>C_k= 1 OR + K AND

$A_{CL}=\sum_{i=1}^{n}i=\frac{n*(n+1)}{2}$

#### Calcolo $S_i$

$S_i$ si calcola quindi facilmente sommando $x_i$, $y_i$ e $C_i$ che arriva dal carry look-ahead tramite dei FA

<img src="img\carrylookahead.png" heigth=200\>

#### Info

|                            |                                                                                                                                                        |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| $T_D=1+2+2$                | La fase di generazione e propagazione richiede 1, quella del calcolo del riporto 2 e la somma con gli FA richiede 2                                    |
| $\#Porte=\frac{n^2+9n}{2}$ | 2n porte dalla fase di generazione e propagazione, $\frac{n(n+1)}{2}$ della fase di Carry Look-Ahead e 2 porte\*# bit (FA richiede solo XOR per $S_i$) |

### Sottrattore

Per eseguire la sottrazione basta considerare uno dei due operandi in XOR con il la sequenza composta da tutti 1, si ottiene cosi la forma C1.
![img](img\sottrattore.png)

$\begin{cases}
\overline{add}/sub=0 \rightarrow\ Y \oplus 0 = Y \rightarrow X+Y+0=X+Y \\
\overline{add}/sub=\ \rightarrow Y \oplus \ = Y_{C1} \rightarrow X+Y_{C1}+1=X+Y{C2}=X-Y
\end{cases}$

### Operator Sharing

L'operatore sharing permette, in caso di somma con operatori variabili, di eseguire prima la scelta degli operatori e poi eseguire la somma, senza quindi eseguire prima 2 somme e poi scegliere il risultato (soluzione equivalente in termini di tempo, non in termini di area)

```Python
if S==0:
  Z=A+B
elif
  Z=C+D
```

<img src="img\operatorsharing.png" height=250 />

#### Info

Realizzando il sommatore con un RCA saranno necessarie allora 6 Porte * n bit con un ritardo di 2*n bit.
I due multiplexer invece richiederanno ciascuno 3 porte \* n bit con un ritardo di 2.

### Sommatori Carry-Save (Per somma di + di 2 operandi)

<img src="img\carrysave.png" height=200/>

#### Info

<img src="img\precarrysave.png" height=150 />

Invertendo $z_0$ con $c_{i,0}$ si ottiene che $x_0+y_0+z_0=(t_0,c_{1,0})$, per ottenere $s_i$ basterà quindi fare $s_i=c_{i,1}+c_{i,0}+t_i$
| | |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
|$T_D=2+2*nbit$| Il carry save ci mette un tempo pari a 2, la restante parte è realizzata tramite RCA => $T_D=2*nbit$|
|$\#Porte=6Porte*\#Cs*nbit + RCA||

#### Extra struttura

TODO

## Riduzione macchina completamente definita

TODO

### Similitudine

TODO

## FSA

TODO

### Macchine di Mealy

$Z=\lambda(Q,X)$
$Q^*=\delta(Q,X)$

### Macchine di Moore

$Z=\lambda(Q)$ -> L'uscita dipende solo dallo stato
$Q^*=\delta(Q,X)$

## Riduzione macchina non definita

### Compatibilità tra stati

Due stati sono compatibili se:

- Hanno la **stessa uscita** e **almeno uno stato di arrivo -(DC)**
  Es:$A \lor B$

$$
\begin{array}{|l|l|l|}
& 1 & 2\\
\hline
A & B/0 & -/1 \\
B & -/0 & C/1\\
\end{array}
$$

- Hanno **almeno una uscita -(DC)** e **stesso stato di arrivo**
  Es:$A \lor B$

$$
\begin{array}{|l|l|l|}
& 1 & 2\\
\hline
A & B/- & C/1 \\
B & B/0 & C/-\\
\end{array}
$$

- Hanno **uscita uguale o almeno una -(DC)** e **almeno uno stato -(DC)**
  Es:$A \lor B$
  $$
  \begin{array}{|l|l|l|}
  & 1 & 2\\
  \hline
  A & B/- & -/- \\
  B & -/0 & C/1\\
  \end{array}
  $$

Es di compatibilità condizionata $A \lor B\ se\ C \lor D$

$$
\begin{array}{|l|l|l|}
& 1 & 2\\
\hline
A & C/- & -/1 \\
B & D/0 & C/1\\
\end{array}
$$

### Classi prime

$C_i$ non è prima se $\exists C_j\ t.c.\ S_i\subseteq{S_j}\ \land V_j\subseteq{V_i}$

## Creazione circuiti sequenziali

Passi:

1. Trovo le funzioni di stato prossimo $q_i^*$
2. Scrivo la tabella di transizione di stato prossimo
3. Trovo eventuali stati non raggiungibili
4. Minimizzo
5. Scrivo le nuove funzioni di stato prossimo con gli stati minimizzati
6. Scrivo le funzioni di eccitazioni in base al bistabile scelto (es: Per JK trovo i valori di J e K dato $q_i$ e $x_i$)
7. Disegno lo schema

#### Funzioni di stato prossimo

Ricavate tramite la tabella di eccitazione, con un abuso di notazione, considerando e calcolando gli implicanti per valori di stato prossimo ad 1 e moltiplicando gli implicanti che portano in una variazione di $Q$ ($Q$ o $\overline{Q}$) per quella variazione (Vedere T)

**Bistabile D**

$$
\begin{array}{|l|l|}
D & Q^*\\
\hline
0 & 0 \\
1 & 1\\
\end{array}
\newline
Q^*=D
$$

**Bistabile T**

$$
\begin{array}{|l|l|}
T & Q^*\\
\hline
0 & Q \\
1 & \overline{Q}\\
\end{array}
\newline[0.1in]
q^*=\overline{T}*Q+T*\overline{Q}
\newline[0.1in]
q^*=T \oplus q
$$

**Bistabile JK**

$$
\begin{array}{|l|l|l|}
J&K & Q^*\\
\hline
0&0 & Q \\
0&1 & 0\\
1&0 & 1\\
1&1 & \overline{Q}\\
\end{array}
\newline[0.1in]
q^*=\overline{j}*\overline{k}*Q+j*\overline{k}+j*k*\overline{Q}
\newline[0.1in]
q^*=\overline{j}*\overline{k}*Q+j*\overline{k}+j*k*\overline{Q}
$$
