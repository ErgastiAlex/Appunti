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

## Componenti

TODO
