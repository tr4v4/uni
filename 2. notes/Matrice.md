---
tags:
  - category/note
  - status/finished
  - topic/algebra-e-geometria
date: 20-02-2024 20:43:18
links:
  - "[[Lecture 20022024091619]]"
  - "[[Lecture 21022024091849]]"
  - "[[Lecture 21032024111439]]"
  - "[[Lecture 04042024112239]]"
  - "[[Lecture 16042024091615]]"
---
# Matrice
---
## Introduzione
> Una **matrice** $A$ di _$m$ righe e $n$ colonne è una tabella_ (di numeri reali) strutturata nel seguente modo:
> $$\begin{pmatrix} a_{11} & a_{12} & ... & a_{1n} \\ a_{21} & a_{22} & ... & a_{2n} \\ ... & ... & ... & ... \\ a_{m1} & a_{m2} & ... & a_{mn} \end{pmatrix}$$
> dove $a_{ij}$ è il coefficiente di posto $i, j$ della matrice $A$, per cui
> - $i$ è l'indice della riga
> - $j$ è l'indice della colonna
> 
> L'insieme delle matrici con $m$ righe e $n$ colonne si indica con
> $$M_{m, n} (\mathbb{R}) = M_{m \times n} (\mathbb{R})$$
> Una matrice $A \in M_{m \times n} (\mathbb{R})$ si dice _quadrata_ $\iff m = n$, e si può indicare con $M_{n} (\mathbb{R})$.
> Due matrici $A$ e $B$ sono uguali $\iff a_{ij} = b_{ij}$ per ogni $i$ e $j$ (che vanno rispettivamente da 1 a $m$ e da 1 a $n$).
> Una riga di una matrice $A \in M_{m \times n} (\mathbb{R})$ può essere vista come una matrice $1 \times n$; mentre una colonna come una matrice $m \times 1$.

## Operazioni
### Trasposizione
Data una matrice $A \in M_{m \times n} (\mathbb{R})$, la sua **trasposta** $A^{T}$ è una matrice dove l'elemento di posto $i, j$ di $A^{T}$ è l'elemento $a_{ji}$ di $A$. Fondamentalmente _si invertono le righe con le colonne_. Per cui
$$A \in M_{5 \times 4} (\mathbb{R}) \ \ \ \implies \ \ \ A^{T} \in M_{4 \times 5} (\mathbb{R})$$

### Somma
La **somma** tra due matrici $A, B \in M_{m \times n} (\mathbb{R})$ può avvenire sse $A$ e $B$ hanno la stessa forma. La matrice risultante $C \in M_{m \times n} (\mathbb{R})$ sarà della forma
$$C_{ij} = A_{ij} + B_{ij}$$

### Prodotto
Il **prodotto** tra due matrici $A \in M_{m \times k} (\mathbb{R})$ e $B \in M_{k \times n} (\mathbb{R})$ è una matrice $C \in M_{m \times n} (\mathbb{R})$ dove $C_{ij} = \text{riga i di A} \cdot \text{colonna j di B}$. Ogni coefficiente di $C$ sarà il risultato del [[Prodotto scalare|prodotto scalare]] tra la riga $i$-esima di $A$ e la colonna $j$-esima di $B$, ovvero assumerà una forma del tipo:
$$a_{i1} \cdot b_{1j} + a_{i2} \cdot b_{2j} + ... + a_{ik} \cdot b_{kj}$$

<u>Attenzione</u>: ovviamente, per poter rendere possibile il prodotto scalare tra riga e colonna di $A$ e $B$, _è necessario che il numero di colonne di $A$ sia uguale al numero di righe di $B$, non vale il contrario_! In caso contrario, la matrice risultante si dice "_non definita_".

<u>Attenzione</u>: _il prodotto tra matrici non è commutativo_, ovvero $A \cdot B \neq B \cdot A$.

## Proprietà
Le proprietà delle matrici, se definite, si riassumono in:
- **distributività**
	- $(A + B)C = AC + BC$
	- $C(A + B) = CA + CB$
- **traspositività**
	- ${AB}^{T} = B^{T}A^{T}$
- **associatività**
	- $(AB)C = A(BC)$

Importante è anche notare che $M_{m \times n} (\mathbb{R})$ con $+$ e $\cdot$ forma un [[Anello|anello]] con:
- $0 = \begin{pmatrix} 0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}$ come elemento neutro per $+$
- $I = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix}$ come elemento neutro per $\cdot$

Quest'ultima matrice è di fatto la [[Matrice identità|matrice identità]].

## Forme
- [[Matrice a scala]]
- [[Matrice triangolare]]
- [[Matrice identità]]
- [[Matrice diagonale]]
- [[Matrice diagonalizzabile]]

## Proposizioni
### Indipendenza
In virtù del [[Teorema della dimensione#Corollario|corollario del teorema della dimensione]], si ha che _la [[Dimensione|dimensione]] dello [[Sottospazio generato|spazio generato]] dalle righe è la stessa dello spazio generato dalle colonne_. Una conseguenza di ciò è che
> Presa una matrice $A \in M_{m \times n} (\mathbb{R})$, e ridotta a scala con [[Algoritmo di Gauss|Gauss]], allora ottenute $r \leq m$ righe linearmente indipendenti, **aggiungendo delle colonne ad $A$ scalata le righe rimangono linearmente indipendenti**.

<u>Nota bene</u>: ovviamente _questo vale anche per $A^{T}$, ovvero per le colonne_, per cui aggiungendo delle colonne ad $A^{T}$ scalata le righe rimangono sempre linearmente indipendenti.

### Base del sottospazio delle colonne
> Presa una matrice $A$ e ridotta a scala in $A'$ con $r$ pivot, tale che le righe non nulle di $A'$ sono una base del sottospazio generato dalle righe di $A$, allora **le colonne di $A$ corrispondenti ai pivot di $A'$ sono una base del sottospazio generato dalle colonne di $A$**.

## Definizioni
- [[Rango righe]]
- [[Operazioni elementari]]

## Referenze