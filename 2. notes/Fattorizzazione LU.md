---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 04-10-2024 13:45:06
links:
  - "[[Lecture 26092024092021]]"
  - "[[Lecture 30092024131914]]"
---
# Fattorizzazione LU
---
## Introduzione
> La **fattorizzazione LU** è un metodo per la [[Algoritmi per la risoluzione di sistemi lineari|risoluzione di sistemi lineari]] che sfrutta l'idea della fattorizzazione della matrice $A$ in:
> $$A = L \cdot U$$
> dove $L$ e $U$ sono [[Matrice triangolare|matrici triangolari]], rispettivamente _inferiore_ e _superiore_.

## Idea
### Fattorizzazione
La prima cosa è trovare $L$ e $U$ triangolari tali che $A = L \cdot U$, con $A \in M_{n}(\mathbb{R})$.

#### Calcolo $U$
Per trovare $U$ mi devo costruire $n-1$ matrici $E_{1}, \cdots, E_{n-1}$ tali che:
- $E_{1}$ sarà la [[Matrice identità|matrice identità]] $I_{n}$ con gli elementi sulla prima colonna calcolati come $e_{i1} = - \frac{m_{i1}}{m_{11}}$ dove $M = A$ e $i > 1$
- $E_{2}$ sarà la matrice identità $I_{n}$ con gli elementi sulla seconda colonna calcolati come $e_{i2} = - \frac{m_{i2}}{m_{22}}$ dove $M = E_{1}A$ e $i > 2$
- ... e così via fino a $E_{n-1}$

A questo punto otterrò la matrice
$$E_{n-1}\cdots E_{2}E_{1}A$$

che, per costruzione, _sarà una matrice triangolare superiore_: $U$.

#### Calcolo $L$
A questo punto, sapendo che
$$U = E_{n-1}\cdots E_{2}E_{1}A$$
e dovendo ottenere $A = LU$, allora
$$L = {E_{1}}^{-1}{E_{2}}^{-1} \cdots {E_{n}}^{-1}$$

che, per costruzione, sarà una _matrice triangolare inferiore_.

### Risoluzione sistema
Ora, avendo trovato $L$ e $U$, il sistema può essere riscritto come
$$Ax = b \iff L(U(x)) = b$$

che è facilissimo da risolvere:
1. considero $y = U(x)$ e risolvo il sistema $Ly = b$;
2. quindi, trovato $y$ per sapere $x$ risolvo $Ux = y$.

Essendo, sia $L$ che $U$ matrici triangolari, automaticamente sono anche [[Matrice a scala|a scala]], per cui **i due sistemi sono facilmente risolvibili per sostituzioni successive** (prima dal basso e poi dall'alto).

## Problemi
### Fattorizzazione limitata
Il grande vincolo di questo algoritmo sta nel fatto che **non tutte le matrici $A$ non singolari possono fattorizzare in $LU$**. In particolare, la fattorizzazione è possibile solo per le matrici che hanno tutti i [[Matrice minore|minori]] principali diversi da 0.
Per cui $\iff$
$$\det(A_{ii}) \neq 0 \ \ \ \forall i \in \{1, \cdots, n\}$$

### Errori algoritmici
Se l'elemento diagonale $a_{11}$ di $A$ è molto piccolo, allora per il calcolo di $E_{1}$ si ha che $e_{i1} = - \frac{a_{i1}}{a_{11}}$ diventa molto grande. Di conseguenza, per via dei limiti della [[Codifica floating-point|codifica floating-point]], si potrebbero perdere delle cifre decimali, _portando a [[Errore algoritmico|errori algoritmici]] molto grandi_.

### Soluzione
Per allargare allora il dominio delle matrici correttamente fattorizzabili, si fa la fattorizzazione LU su una matrice $A$ su cui sono state scambiate delle righe attraverso una [[Matrice di permutazione|matrice di permutazione]] $P$:
$$PA = LU$$

Questa matrice $P$ allora serve a:
1. _garantire il funzionamento dell'algoritmo su matrici che non hanno tutti i minori principali diversi da 0_;
2. _limitare l'errore algoritmico per elementi sulla diagonale $a_{ii}$ molto piccoli._

Di questi scambi bisogna chiaramente tener conto anche per il risultato finale. Infatti:
$$P \neq I_{n} \implies Ly = Pb$$

## Algoritmo
```python
import numpy as np
import scipy as sp

def solve_linear_system(A: np.ndarray, b: np.ndarray) -> np.ndarray:
	P, L, U = sp.linalg.lu(A)
	y = np.linalg.solve(L, b@P)
	x = np.linalg.solve(U, y)
	return x
```

## Complessità
La [[Complessità computazionale|complessità computazionale]] dell'algoritmo risulta essere:
$$O\left(\frac{n^{3}}{3}\right) + O\left(\frac{n^{2}}{2}\right) + O\left(\frac{n^{2}}{2}\right) = O\left(\frac{n^{3}}{3}\right) + O(n^{2})$$

## Referenze