---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 24-11-2024 13:46:29
links:
  - "[[Lecture 11112024131700]]"
---
# Convoluzione
---
## Introduzione
> La **convoluzione** è un'operazione matematica principalmente applicata su [[Matrice|matrici]] che consente di combinare un [[Matrice di convoluzione|kernel]] $K \in \mathbb{R}^{D \times D}$ (con $D$ dispari) con una immagine $A \in \mathbb{R}^{M \times N}$ per ottenere un'immagine modificata $C \in \mathbb{R}^{M \times N}$, tale che
> $$C = [K * (A|B)]$$
> dove $B \in \mathbb{R}^{(M+(D-1)) \times (N+(D-1))}$ è l'[[Matrice estesa|estensione]] di $A$ (necessaria per applicare il kernel sui bordi di $A$).
> Solitamente, $C$ viene calcolata come
> $$C_{(i, j)} = \sum\limits_{m=1}^{\frac{D-1}{2}} \sum\limits_{n=1}^{\frac{D-1}{2}} K(m,n) W_{(i,j)}(m,n)$$
> dove $W_{(i,j)}$ è la [[Sottomatrice|sottomatrice]] $D \times D$ di $B$ [[Centro di una matrice|centrata]] in $(i+\frac{D-1}{2},j+\frac{D-1}{2})$.

## Referenze