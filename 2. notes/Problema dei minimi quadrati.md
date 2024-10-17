---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 13-10-2024 17:32:32
links:
  - "[[Lecture 30092024131914]]"
---
# Problema dei minimi quadrati
---
## Introduzione
Per poter affrontare il problema dei minimi quadrati è necessario conoscere:
- [[Fattorizzazione agli autovalori|fattorizzazione agli autovalori]]
- [[Fattorizzazione ai valori singolari|fattorizzazione ai valori singolari]]

## Definizione
> Preso un [[Sistema lineare|sistema lineare]] $Ax = b$ dove $A \in M_{m \times n}(\mathbb{R})$ con $m > n$ (ho più equazioni che incognite), per cui in generale non esiste una soluzione, il **problema dei minimi quadrati** consiste nel trovare un $x \in \mathbb{R}^{n}$ talche che venga _minimizzata la differenza_ $Ax - b$, o formalmente
> $${\arg_{\min}}_{x \in \mathbb{R}^{n}} {\|Ax - b\|_{2}}^{2}$$
> Per cui si cerca l'$x \in \mathbb{R}^{n}$ che minimizzi la [[Norma euclidea|norma euclidea]] del vettore $Ax - b$ al quadrato.
> <u>Nota bene</u>: $x = \arg_{\min}$, invece $y = Ax - b = \min$.

<u>Nota bene</u>: il motivo per cui si fa la norma al quadrato è per una semplificazione dei calcoli.


Si tratta di un _problema estremamente comune_, soprattutto nel [[Machine learning|machine learning]].

## Formalizzazione
Definiamo una [[Funzione matematica|funzione]] $F: \mathbb{R}^{n} \to \mathbb{R}^{+}$ tale che
$$F(x) = {\|Ax-b\|_{2}}^{2}$$

<u>Nota bene</u>: il codominio di $F$ è $\mathbb{R}^{+}$ poiché $Ax - b \neq 0 \ \ \ \forall x \in \mathbb{R}^{n}$.

Allora si tratta di un **problema di ottimizzazione**: vogliamo trovare il minimo globale di $F$. La cosa positiva è che _$F$ è lineare rispetto all'incognita_, per cui trovare il minimo è relativamente semplice.

Definiamo intanto $Ax - b = r$ dove $r$ è detto _residuo_. Si vuole minimizzare il residuo.

## Soluzione
Il meccanismo di risoluzione del problema dei minimi quadrati nasce dalla seguente proposizione.
> Sia $A \in M_{m \times n}(\mathbb{R})$ con $m > n$ e $rk(A) = k \leq n$, allora il problema dei minimi quadrati ammette sempre almeno una soluzione, e:
> - $k = n \implies$ il problema ammette una e una sola soluzione;
> - $k < n \implies$ il problema ammette infinite soluzioni, che formano un sottospazio di $\mathbb{R}^{n}$ di dimensione $n-k$.

### $k = n$
Se $k = n$, allora la soluzione si ottiene passando alle **equazioni normali**. In particolare
$${\|Ax-b\|_{2}}^{2} = x^{T}A^{T}Ax - 2x^{T}A^{T}b + b^{T}b$$
per cui
$$F(x) = x^{T}A^{T}Ax - 2x^{T}A^{T}b + b^{T}b$$

Allora per minimizzare $F$, trattandola come una funzione qualsiasi, dobbiamo porre la [[Derivata|derivata]] a 0. Sapendo che l'incognita è $x \in \mathbb{R}^{n}$, in realtà poniamo il [[Gradiente|gradiente]] a $\underline{0}$.

Ricordiamo che se $F: \mathbb{R}^{n} \to \mathbb{R}$, allora $\nabla F = \left( \frac{\partial F}{\partial x_{1}}, \cdots, \frac{\partial F}{\partial x_{n}} \right)$, e che se $x^{*}$ è il minimo di $F$, allora $\nabla F(x^{*}) = \underline{0}$.

Non resta che calcolare $\nabla F$. Sapendo che si tratta di un operatore lineare, dividiamo le derivazioni vettoriali nelle 3 componenti di $F$:
- $\nabla F(x^{T}A^{T}Ax) = 2A^{T}Ax$
- $\nabla F(2x^{T}A^{T}b) = 2A^{T}b$
- $\nabla F(b^{T}b) = 0$

In definitiva
$$\nabla F(x) = 2A^{T}Ax - 2A^{T}b$$

Ora, per trovare il minimo di $F$, poniamo $\nabla F(x) = \underline{0}$, e otteniamo il **sistema delle equazioni normali**:
$$A^{T}Ax = A^{T}b$$

Si ha che $A^{T}Ax$ e $A^{T}b$ sono chiamate equazioni normali, e hanno proprietà interessanti:
- $A^{T}A$ è quadrata ($n \times n$) ed è _simmetrica semidefinita positiva_, inoltre sapendo che $rk(A) = n$ allora è proprio _definita positiva_;
- $A^{T}b \in \mathbb{R}^{n}$.

Sapendo che il sistema delle equazioni normali è un _sistema lineare quadrato con matrice simmetrica e definita positiva_, allora _automaticamente la soluzione del sistema è il punto di minimo che si sta cercando_. Inoltre, proprio per le proprietà di $A^{T}A$, si può risolvere il sistema facilmente con la [[Fattorizzazione di Cholesky|fattorizzazione di Cholesky]]:
1. ottengo $A^{T}A = LL^{T}$
2. risolvo $Ly = A^{T}b$
3. risolvo $L^{T}x = y$

<u>Attenzione</u>: $K(A^{T}A) = K(A)^{2}$, ossia il [[Numero di condizione|numero di condizione]] di $A^{T}A$ è il numero di condizione di $A$ al quadrato, per cui essendo $K(A) \geq 1$, allora $K(A)^{2} \geq K(A)$. Bisogna stare molto attenti perché _è facile incorrere in problemi mal posti_.

### $k < n$
In quest'altro caso, ci sono infinite soluzioni. Allora decido di calcolare la soluzione $\bar{x}$ di norma minima, ossia
$$\bar{x} = \min {\|y\|_{2}}^{2}$$
con $y \in S$ e $S$ l'insieme delle infinite soluzioni del problema.

<u>Nota bene</u>: in realtà questo metodo vale anche per $k = n$, ma per quello conviene usare le equazioni normali.

Calcoliamo $\bar{x}$ usando la [[Fattorizzazione ai valori singolari|fattorizzazione ai valori singolari]] (SVD). In particolare c'è un teorema che asserisce che, data $A = U \Sigma V^{T}$, e $rk(A) = k < n$, allora la soluzione $\bar{x}$ di norma minima al problema dei minimi quadrati è calcolabile come
$$\bar{x} = \sum\limits_{i=1}^{k} \frac{u_{i}^{T}b}{\sigma_{i}}v_{i}$$

#### Dimostrazione
Suppongo
$$A = U \Sigma V^{T}$$

Sapendo che $U$ è [[Matrice ortogonale|ortogonale]], allora anche $U^{T}$ è ortogonale e _isometrica_ ($\|x\|_{2} = \|U^{T}x\|_{2}$). Per cui posso scrivere l'equivalenza
$${\|Ax - b\|_{2}}^{2} = {\|U^{T}Ax - U^{T}b\|_{2}}^{2}$$

Sapendo che $V^{T} = V^{-1}$ (perché $V$ ortogonale), posso scrivere
$${\|U^{T}Ax - U^{T}b\|_{2}}^{2} = {\|U^{T}AVV^{T}x - U^{T}b\|_{2}}^{2}$$

Noto che $U^{T}AV = \Sigma$, e chiamando:
- $y = V^{T}x$
- $g = U^{T}b$

riscrivo il tutto come
$${\|U^{T}AVV^{T}x - U^{T}b\|_{2}}^{2} = {\|\Sigma y - g\|_{2}}^{2}$$

Ora, per definizione di norma euclidea, ho che
$${\|\Sigma y - g\|_{2}}^{2} = \sum\limits_{i=1}^{n} (\sigma_{i}y_{i} - g_{i})^{2}$$

e sapendo per ipotesi $k < n$, allora per le proprietà della decomposizione ai valori singoli, avrò che $\sigma_{k+1} = \cdots \sigma_{n} = 0$, per cui posso scomporre la [[Sommatoria|sommatoria]] come
$$\sum\limits_{i=1}^{n} (\sigma_{i}y_{i} - g_{i})^{2} = \sum\limits_{i=1}^{k} (\sigma_{i}y_{i} - g_{i})^{2} + \sum\limits_{i=k+1}^{n} {g_{i}}^{2}$$

Detto questo, non posso considerare il secondo termine ($\sum\limits_{i=k+1}^{n} {g_{i}}^{2}$) ai fini della minimizzazione (perché $g_{i}$ non dipende da $x$). Quindi mi concentro sul minimizzare $\sum\limits_{i=1}^{k} (\sigma_{i}y_{i} - g_{i})^{2}$, rendendo nullo $\sigma_{i}y_{i} - g_{i}$:
$$\sigma_{i}y_{i} - g_{i} = 0 \iff y_{i} = \frac{g_{i}}{\sigma_{i}} \ \ \ \forall i = 1, \cdots, k$$

Ricompongo tutti i vari elementi. So che
- $g_{i} = {u_{i}}^{T}b$
- $y = V^{T}x \iff x = Vy$

Per cui, sostituendo, ottengo
$$y_{i} = \frac{{u_{i}}^{T}b}{\sigma_{i}} \in \mathbb{R} \ \ \ \forall i = 1, \cdots, k$$

e sapendo
$$y = (y_{1}, \cdots, y_{k}, 0, \cdots, 0) \in \mathbb{R}^{n}$$

ho che
$$x = Vy = \sum\limits_{i=1}^{n} v_{i}y_{i} = \sum\limits_{i=1}^{k} v_{i} \frac{u_{i}^{T}b}{\sigma_{i}}$$

Fondamentalmente, calcolando $x$ in questo modo, minimizziamo $\sum\limits_{i=1}^{k} (\sigma_{i}y_{i} - g_{i})^{2}$ e quindi di conseguenza ${\|Ax - b\|_{2}}^{2}$.

E' importantissimo non scordarsi del termine "scartato" $\sum\limits_{i=k+1}^{n} {g_{i}}^{2}$. Questo, infatti, non è altro che la norma del residuo $r$ al quadrato:
$${\|r\|_{2}} = \sum\limits_{i=k+1}^{n} {g_{i}}^{2} = \sum\limits_{i=k+1}^{n} ({u_{i}}^{T}b)^{2}$$

#### Pseudoinversa
E' possibile definire di una matrice $A$ decomposta in valori singoli come $A = U \Sigma V^{T}$, la sua pseudoinversa
$$A^{+} = V \Sigma^{+}U^{T}$$

dove $\Sigma^{+}$ è la matrice che ha sulla diagonale $\frac{1}{\sigma_{i}}$ per $i \leq k$.

La pseudoinversa ha le seguenti proprietà:
- $AA^{+}A = A$
- $A^{+}AA^{+} = A^{+}$
- $(AA^{+})^{T} = AA^{+}$
- $(A^{+}A)^{T} = A^{+}A$

Ma l'utilità della pseudoinversa sta nel poter scrivere la soluzione del problema dei minimi quadrati in modo simile a un sistema lineare. Infatti
$$\bar{x} = V \Sigma^{+} U^{T} b$$
e quindi la soluzione $\bar{x}$ può essere vista come
$$\bar{x} = A^{+}b$$

Inoltre, considerando che l'inversa di $A$ non esiste, è possibile definire il [[Numero di condizione|numero di condizione]] di in termini della pseudoinversa:
$$K(A) = \|A\| \cdot \|A^{+}\|$$

o in alternativa si può usare il numero di condizionamento spettrale
$$K(A)_{2} = \|A\|_{2} \cdot \|A^{+}\|_{2} = \frac{\sigma_{1}}{\sigma_{n}}$$

## Referenze