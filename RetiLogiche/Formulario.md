# Reti Logiche

## Formule algebriche

$xy+\overline{x}z+yz=xy+\overline{x}z$
$x+\overline{x}y=x+y$
$x+xy=x$
$x+x=x$

Note: Se si sostituisce \* con + e + con \* si ottengono teoremi e formule duali

## Costruzione reti tramite porte logiche NAND e NOR

Applicare con attenzione il teorema di De Morgan

## Porte Logiche

| Porta | #Gate | Mos |
| ----- | ----- | --- |
| Not   | 1     | 2   |
| NOR   | 2     | 4   |
| NAND  | 2     | 4   |
| AND   | 3     | 6   |
| OR    | 3     | 6   |

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

### Tabella di copertura

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

#### Tabella per minimizzare il costo degli implicanti

Ogni implicante **costa $1$ e il suo costo passa a $0$** una volta che viene usato

#### Tabella per minimizzare il costo dei letterali

Ogni implicante **costa $n$ e il suo costo passa a $1$** una volta che viene usato

#### Dominanza di riga

P1 domina P2 poichè ogni copertura di P2 è coperta anche da P1, in più P1 copre più mintermini

$$
\begin{array}{l|l|l|l}
Implicante & 1 & 2  \\
\hline
P1 & x & x&  \\
P2 & x & &  \\
\end{array}
$$

#### Dominanza di colonna

La colonna 2 domina la colonna 1, poichè, ogni implicante che copre 2 copre anche sicuramente anche 1, quindi, si elimina la colonna 1

$$
\begin{array}{l|l|l|l}
Implicante & 1 & 2  \\
\hline
P1 & x & x  \\
P2 & x &  \\
P3 & x&
\end{array}
$$

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

Per la sintesi delle funzioni a più uscita rimane tutto invariato, solo che si aggiunge una maschera di bit che indica a quale funzione fa riferimento
Es: Un mintermine condiviso da $f_1$ e $f_2$ ma non da $f_3$ avrà come maschera $110$
Quando si applica il metodo di Quine-McCluskey basterà fare la OR delle maschere degli n-cubi e applicare queste regole tenendo conto della maschera risultante:

- Segno tutti gli implicanti con maschera uguale a quella ottenuta
- Lascio non segnati (e quindi possibili primi) tutti gli implicanti con maschera diversa
- Non riporto nella nuova lista gli implicanti con maschera tutta a $0$

### Tabella di copertura

E' importante riporta nella tabella di copertura anche i pesi degli implicanti (numero letterali)

#### Dominanza di riga

Si fa tenendo conto di TUTTE le funzioni ed è applicabile SSE il costo è uguale o minore dell'implicante dominato

#### Dominanza di colonna

Applicabile solo all'interno della funzione

#### Essenzialità

Ogni implicante scelto viene rimosso solo per la singola funzione in cui è stato tolto, ma, il costo **per le altre passa da n a 1**

#### Metodo di Petrik multifunzione

Il metodo di petrik multifunzione si esegue ugualmente a quello singolo, solo che
$C(F)=\prod_{i} c(f_i)$

#### Calcolo dei letterali finale

Ogni implicante condiviso viene sostituito con una variabile, che si conta come singolo letterale.
Es:
$
p_1=3\ letterali \newline
p_2=2\ letterali \newline
p_3=2\ letterali \newline
f_1=p_1+p_2 \newline
f_2=p_1+p_3$
Diventa
$q_1=p_1 \newline
f_1=q_1+p_2 \ |letterali=1+2 \newline
f_2=q_1+p_3 \ |lettarali=1+2 \newline
letterali_{totali}=3+(1+2)+(1+2)
$

## Metodi euristici

Ne esistono di due tipi:

- Greedy o Gradient Descending: Trova un minimo locale
- Simulated Anneling: Accetta un leggero peggioramento sperando in un futuro miglioramento
  > do
  > $\Phi$=|F|
  > F=reduce(F) //Si riducono i cubi secondo un ranking di probabilità di futura aggregazione
  > F=expand(F) //Si espandono i cubi "migliori" (quelli che hanno il ranking minore rispetto alla probabilità di ridursi )
  > F=irredundant(F) //Copertura
  > while (|F|<$\Phi$)

#### Reduce

$\{A,B\}\ \rightarrow \{A,B,C,D\}$
$C=\overline{x}A$
$D=xA$

#### Expand

$reduce(xP,x)$ // Espansione nella direzione di x, diventa $P$

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

E' importante notare come la struttura del CS riceve sempre 3 input e ha 2 output, che possono a loro volta fare da input per un altro CS o RCA
$S=X+Y+Z+W$ (4bit)
<img src="img\cs-rca.png" height=150 />
$A_T=6 (porte per elemento)*4 (bit)*2(\#cs)+6(porte)*4(bit)(\#FA)$
$T_D=2(Tempo\ CS)*2(CS)+2(Tempo\ FA)*4(bit)$

### Moltiplicatore

Dati due numeri binari $X:[x_2,x_1,x_0]\ e\ Y:[y_2,y_1,y_0],$ $X*Y$ produce un risultato di $2*n-1$ bit

$$
\begin{array}{llllll}
          &           & x_2      & x_1      & x_0      & * \\
          &           & y_2      & y_1      & y_0      & = \\
          \hline
0         & 0         & x_2*y_0 & x_1*y_0 & x_0*y_0 &   \\
0         & x_2*y_1 & x_1*y_1 & x_0*y_1 & 0         &   \\
x_2*y_2 & x_1*y_2 & x_0*y_2 & 0         & 0         &   \\
\end{array}
$$

Tramite una rete ad 1 livello di porte AND è possibile generare ogni prodotto parziale
<img src="img\moltiplicatore.png" height=200>

=> Per generare tutti i termini da sommare servono $n^2$ porte + il relativo sommatore

## Bistabili

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

### Tabella di transizione di stato

Descrive $Q^*$ in funzione di $Q$ e $X$ (Solo Mealy)

### Tabella di eccitazione

Dato $Q, Q^*$ quali ingressi devo fornire al bistabile per ottenere quella transizione

### Come si usa?

Si costruisce una mappa di karnaugh dipendente da $Q,X$ che contiene al suo interno i valori del bistabile per ottenere la transizione da $Q$ a $Q^*$ dato $X$
Si sintetizzano i valori di ingresso-

## FSA

$\{X,Z,S,\sigma_0,\delta,\lambda\}$

### Costruzione FSA con bistabili

1. Specifica che definisce il comportamento di $X$ e $Z$
2. Costruzione Grafo
3. Scelta codifica $S$ e $\sigma_0$
4. Tabella transizione di stato simbolica
5. Tabella transizione codificata
6. Scelta Flip-Flop
7. Codifica funzioni di eccitazione dei bistabili

## Riduzione macchina completamente definita

### Similitudine

$\sigma_1 \sim \sigma_2\ sse\ \forall y\in X^* \lambda^*(\sigma_1,y)=\lambda^*(\sigma_2,y)$

Due stati sono uguali se per qualsiasi stringa di ingresso di $X^*$, hanno la stessa uscita ($\lambda$)

#### Proprietà

##### Transitiva

$\sigma_1 \sim \sigma_2 \land \sigma_2 \sim \sigma_3 \implies \sigma_1\sim\sigma_3$

##### Riflessiva

$\sigma_1 \sim \sigma_1$

##### Simmetrica

$\sigma_1 \sim \sigma_2 \land \sigma_2 \sim \sigma_1$

### Metodo di Paull-Hunger

Note: Si basa sul singolo ingresso

1. $\sigma_1 \not\sim \sigma_2$ se $\exists x\in X\ t.c.\ \lambda(\sigma_1,x)\ !=\lambda(\sigma_2,x)$

2. Se $\forall x \in X \lambda(\sigma_1,x)=\lambda(\sigma_2,x) $
2.1 Se $\exists x\ t.c.\ \delta(\sigma_1,x)\not\sim\delta(\sigma_2,x) \implies \sigma_1 \not\sim\sigma_2$
   2.2 Se $\forall x \delta(\sigma_1,x)\sim\delta(\sigma_2,x) \implies \sigma_1\sim\sigma_2$
   2.3 Anelli di dipendenza => Tutti simili

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

## Contatori

Macchine a stati cicliche e senza ingressi, rappresentabili quindi sotto forma di macchine di Moore

### Proprietà

- Modulo: Indica la lunghezza della sequenza di conteggio
- Sequenza
- No ingressi
- Sequenza periodica

### Progettazione comportamentale

La progettazione comportamentale consiste nel realizzare un FSA che indica la sequenza di conteggio (FSA ciclico e senza ingressi)

La tabella di transizione di stato non ha X

#### Progettazione comportamentale con ripetizione

- Disambiguazione: Si aggiungono dei bit per differenziare i vari stati, l'uscita è quindi presa direttamente dai Flip-Flop senza rete combinatoria
  Es: Due uscite $00$ diventano lo stato $000$ e $100$
- Aggiunta di rete di transcodifica che codifica lo stato nell'uscita corretta.

### Progettazione strutturale

La progettazione strutturale si basa sul notare che comportamenti abbia un contatore
$z(t+1)=z(t)+1$
<br/>
<img src="img\contatorestrutturale.png" height=150>

#### Progettazione strutturale con modulo $\ne\ 2^k$

<img src="img\contatorestrutturalereset.png" height=150>

#### Progettazione strutturale Up\Down

<img src="img\contatoreupdown.png" height=150>

### Contatori veloci

#### Johnson (Bistabile D)

<img src="img\contatoreJohnson.png">

Sequenza:
100
010
001

#### Moebius

<img src="img\contatoreMoebius.png">

Sequenza
000
100
110
111
011
001
