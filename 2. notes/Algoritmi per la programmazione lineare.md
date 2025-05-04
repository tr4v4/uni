---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 21-04-2025 18:43:16
links:
  - "[[Lecture 09042025091244]]"
  - "[[Lecture 14042025091835]]"
  - "[[Lecture 16042025091309]]"
---
# Algoritmi per la programmazione lineare
---
## Introduzione
Dato un problema di [[Programmazione lineare|programmazione lineare]], si vuole trovare un _algoritmo che dalla funzione obiettivo e dai vincoli, scritti in forma matriciale, trovi la soluzione_, la sua mancanza (problema vuoto) o la sua illimitatezza (problema illimitato).

Chiaramente, non si puo' fare ricerca esaustica! Se consideriamo problemi di programmazione lineare non-intera, in particolare, l'insieme delle soluzioni possibili e' non [[Numerabilità|numerabile]] --> l'algoritmo non terminerebbe mai.

### Intuizione
Prendiamo il seguente problema:
- funzione obiettivo --> $\max x+y$;
- vincoli --> $\begin{cases} x \geq 0 \\ x \leq 3 \\ x + 2y \geq 2 \\ y \leq 2 \\ y \geq 0 \end{cases}$

Notiamo, come le variabili in gioco $x, y$ costituiscano al loro variare il piano cartesiano, composto dalle [[Coppia ordinata|coppie]] di valori $(x, y)$ del [[Prodotto cartesiano|prodotto cartesiano]] $\mathbb{R}^{2}$.

Ogni vincolo, in particolare, costituisce un'area dello spazio cartesiano in cui sono ammissibili i valori della soluzione. Se si intersecano i singoli vincoli, si ottiene uno spazio chiuso della forma
![[algoritmi-programmazione-lineare-1.png]]

La funzione obiettivo stessa, inoltre, costituisce nella sua forma $x+y$ un piano nella terza dimensione $z$ ($z = x+y$), che proiettato nel piano cartesiano costituisce una retta della forma $y = -x$.
![[algoritmi-programmazione-lineare-2.png]]
![[algoritmi-programmazione-lineare-3.png]]

Quindi, **si vuole cercare geometricamente il punto $(x, y)$ che massimizzi $z$ all'interno dell'area grigia determinata dai vincoli**!
In questo caso, tale punto coincide con $(3, 2)$:
![[algoritmi-programmazione-lineare-4.png]]

Intuitivamente, possiamo pensare di restringere lo spazio di ricerca della soluzione ottima ad un insieme finito di punti della regione di spazio: i **vertici** del poliedro. Ma questo e' vero in ogni caso? E soprattutto, quest'intuizione vale per problemi a $n>2$ variabili?

## Nozioni preliminari
### Iperpiano
> E' l'insieme $\{x \in \mathbb{R}^{n} | ax=b\}$ delle soluzioni dell'equazione lineare $ax = b$. In altri termini e' la generalizzazione del concetto di retta.

### Semispazio
> E' l'insieme $\{x \in \mathbb{R}^{n} | ax \leq b\}$ delle soluzioni della disequazione lineare $ax \leq b$. Ovviamente, l'iperpiano e' il "confine" del corrispondente semispazio.

<u>Nota bene</u>: iperpiano e semispazio rappresentano i vincoli!

### Poliedro
> E' l'intersezione $P$ di un numero finito di $m$ semispazi. In particolare devono esistere $A \in \mathbb{R}^{m \times n}$ e un vettore $b \in \mathbb{R}^m$ tali che $P = \{x | Ax \leq b\}$.

### Insieme convesso
> E' un insieme $C \subseteq \mathbb{R}^{n}$ tale che tutti i punti che connettono $x, y \in C$ sono anch'essi in $C$, ossia
> $$\forall x, y \in C, \forall \alpha \in [0, 1] \ \ \ \alpha x + (1 - \alpha)y \in C$$

E' circa la stessa definizione delle [[Funzione convessa|funzioni convesse]]. Si dimostra che i semispazi e i poliedri sono insiemi convessi.

### Matrice
Consideriamo $A$ la matrice dei semispazi, quindi dei vincoli. Se prendiamo un sottoinsieme $I$ di $\{1, \cdots, m\}$, e quindi delle righe di $A$, quello che viene fuori e' un'altro poliedro. Prendiamo anche $\bar{I} = \{1, \cdots, m\} \setminus I$, e definiamo
$$P_{I} = \{x | A_{I}x = b_{I} \land A_{\bar{I}}x \leq b_{\bar{I}}\}$$

A seconda di quale $I$ scegliamo, possiamo ottenere dei _lati del poliedro, dei vertici o anche degli insiemi vuoti_.

#### Faccia
> E' un poliedro nella forma $P_{I}$ tale che $P_{I} \neq \varnothing$. La [[Dimensione|dimensione]] di una faccia e' la dimensione del piu' piccolo [[Sottospazio vettoriale|sottospazio]] che la contiene.

<u>Nota bene</u>: il numero di facce distinte di un poliedro e' al piu' $2^{m}$ dove $m$ e' il numero di vincoli.

<u>Nota bene</u>: $P$ stesso e' una faccia, in particolare $P_{\varnothing}$.

#### Vertice
> E' una faccia di dimensione 0. Infatti, presa una matrice $A_{I}$ di rango massimo $n$, allora significa che l'equazione $A_{I}x = b_{I}$ ha una e una sola soluzione, avendo [[Rango righe|rango]] massimo, e quindi intuitivamente e' un vertice.

<u>Nota bene</u>: di conseguenza $A_{I}$ e' [[Matrice invertibile|invertibile]]!

#### Soluzioni di base
> Supponendo di avere un insieme di vincoli $B$ tale che $A_{B}$ sia quadrata e invertibile, allora:
> - $B$ e' detta _base_;
> - $A_{B}$ e' detta _matrice di base_;
> - $x_{B} = A_{B}^{-1}b_{B}$ e' detta _soluzione di base_.

Chiaramente, se $x_{B} \in P$ allora sara' un vertice di $P$, e la soluzione di base si dice ammissibile, altrimenti non e' ammissibile (e quindi e' fuori dal poliedro!).

Di conseguenza **i vertici di $P$ sono tutte e sole le sue soluzioni di base ammissibili**.

#### Vincoli attivi
> Se $x \in P$ allora i vincoli che vengono soddisfatti come uguaglianze in $x$ sono detti _attivi_, e li chiamiamo $I(x)$ tale che
> $$I(x) = \{i | A_{i}x = b_{i}\}$$

Vale che per ogni $J \subseteq I(x)$ l'insieme $P_{J}$ e' una faccia di $P_{i}$, e $P_{I(x)}$ e' la faccia minimale tra esse (perche' e' l'intersezione di tutti i vincoli attivi, che quindi riduce la dimensione dello spazio).

### Altra rappresentazione
Abbiamo definito i poliedri come intersezioni di semispazi, e quindi di vincoli. Ma _possiamo rappresentare i poliedri anche a partire proprio dai suoi vertici_!

#### Inviluppo convesso
> Dato un insieme di punti $X = \{x_{1}, \cdots, x_{s}\} \subseteq \mathbb{R}^{n}$, l'**inviluppo convesso** e' il piu' piccolo insieme convesso che contiene tutti i punti di $X$, o formalmente
> $$conv(X) = \{x = \sum\limits_{i=1}^{s} \lambda_{i}x_{i} | \sum\limits_{i=1}^{s} \lambda_{i} = 1 \land \lambda_{i} \geq 0\}$$

In altri termini, questo contiene tutte le [[Combinazione lineare|combinazioni lineari]] dei punti in $X$ tali che i coefficienti $\lambda$ sommano a 1 e sono tutti positivi.

Si dimostra che $conv(X)$ contiene tutti i punti di $X$, e non solo e' un poliedro, ma un _politopo_, ossia limitato in cui i vertici sono tutti in $X$.

<u>Nota bene</u>: non tutti gli elementi di $X$ sono per forza dei vertici dell'inviluppo convesso, questo succede se dei punti di $X$ appartengono all'area del politopo.

#### Cono convesso
> Un insieme $C \subseteq \mathbb{R}^{n}$ e' un **cono** se $\forall x \in C$ e $\forall \alpha \in \mathbb{R}^{+}$ avviene che $\alpha x \in C$.

In altri termini, qualunque allungamento o accorciamento di un vettore appartiene ancora a $C$.

> Un **cono convesso** e' un cono che e' anche un insieme convesso, ossia
> $$\forall x, y \in C \land \lambda, \mu \in \mathbb{R}^{+} \implies \lambda x + \mu y \in C$$

> Possiamo restringere i coni a certe direzioni, con **coni finitamente generati** da un insieme $V$ di vettori:
> $$cono(V) = \{v = \sum\limits_{i=1}^{t} \nu_{i} v_{i} | \nu_{i} \in \mathbb{R}^{+}\}$$

## Teoremi
Fatte queste premesse, possiamo enunciare alcuni teoremi fondamentali. In particolare:
- [[Teorema di Motzkin]];
- [[Teorema fondamentale della programmazione lineare]].

Bisogna anche introdurre brevemente il concetto di dualita', della [[Teoria della dualita'|teoria della dualita']]. Infine mancano le nozioni di [[Direzione ammissibile|direzione ammissibile]] e [[Direzione di crescita|direzione di crescita]].

## Algoritmo
L'algoritmo che utilizza tutte queste nozioni per risolvere un problema di programmazione lineare e' l'[[Algoritmo del simplesso|algoritmo del simplesso]].

## Referenze