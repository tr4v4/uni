---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 13-10-2024 17:35:57
links:
  - "[[Lecture 30092024131914]]"
---
# Fattorizzazione agli autovalori
---
## Introduzione
> Supponendo che una [[Matrice|matrice]] quadrata $A \in M_{n}(\mathbb{R})$ abbia $n$ [[Autovalore|autovalori]] distinti, allora è possibile **fattorizzare agli autovalori** $A$ come:
> $$A = VDV^{-1}$$
> dove:
> - $V$ è la matrice che ha gli autovettori $v_{1}, \cdots, v_{n}$ in colonna;
> - $D$ è la [[Matrice diagonale|matrice diagonale]] che ha gli autovalori $\lambda_{1}, \cdots, \lambda_{n}$ sulla diagonale;

<u>Nota bene</u>: automaticamente, se $A$ ha la decomposizione agli autovalori allora è [[Matrice diagonalizzabile|diagonalizzabile]].

## Dimostrazione
Suppongo
$$A v_{i} = \lambda_{i}v_{i} \ \ \ i = 1, \cdots, n$$

allora posso scrivere
$$[Av_{1}, \cdots, Av_{n}] = [\lambda_{1}v_{1}, \cdots, \lambda_{n}v_{n}]$$
dove $Av_{i}$ è la $i$-esima colonna di una matrice.

Raccolgo $A$[^1] a sinistra,
$$A[v_{1}, \cdots, v_{n}] = [\lambda_{1}v_{1}, \cdots, \lambda_{n}v_{n}]$$

e riscrivo la matrice di destra come una matrice composta dagli scalari $\lambda_{1}, \cdots, \lambda_{n}$ sulla diagonale (e 0 in tutto il resto) moltiplicata per la matrice $[v_{1}, \cdots, v_{n}]$ (che ha come colonne gli [[Autovettore|autovettori]]):
$$A[v_{1}, \cdots, v_{n}] = [v_{1}, \cdots, v_{n}] \begin{bmatrix} \lambda_{1} & & \\ & \ddots & \\ & & \lambda_{n} \end{bmatrix}$$

Chiamo $V = [v_{1}, \cdots, v_{n}]$ e $D = \begin{bmatrix} \lambda_{1} & & \\ & \ddots & \\ & & \lambda_{n} \end{bmatrix}$, per cui ho
$$AV = VD$$

e moltiplicando ambo i membri a destra per $V^{-1}$ ottengo:
$$A = VDV^{-1}$$

**Qed**.

## Referenze
[^1]: posso per la _distributività_