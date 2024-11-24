---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 24-11-2024 14:04:11
links:
  - "[[Lecture 11112024131700]]"
---
# Matrice estesa
---
## Introduzione
> La **matrice estesa** è una tecnica utilizzata per _applicare la [[Convoluzione|convoluzione]] su una [[Matrice|matrice]] $A \in \mathbb{R}^{M \times N}$_. Essa consiste nell'_aggiungere ai bordi di $A$ delle righe e colonne a formare $B$_, la sua estensione.
> Formalmente, se $A \in \mathbb{R}^{M \times N}$ e $k \in \mathbb{N}$, allora $B \in \mathbb{R}^{(M+2k) \times (N+2k)}$ **estende** $A$ $\iff$
> $$\forall (i, j) \in \{1, \cdots, M\} \times \{1, \cdots, N\}. \ \ \ A_{(i,j)} = B_{(i+k, j+k)}$$
> <u>Nota bene</u>: $B$ dev'essere di dimensione $(M + 2k) \times (N + 2k)$ e non $(M + k) \times (N + k)$ _per mantenere $A$ al centro di $B$_, infatti se voglio estendere $B$ con un bordo spesso $1$, dovrò aggiungere $2$ righe e $2$ colonne (una per ogni lato).
> <u>Osservazione</u>: ogni matrice ha _infinite estensioni_!

## Condizioni al bordo
Bisogna capire come trattare i bordi di $A$ in $B$, ossia come estendere $A$. Ci sono 3 principali metodi:
1. **zero padding**: si estende $A$ con zeri, quindi nel caso dell'[[Imaging|imaging]] si assume che l'immagine sia nera oltre i bordi;
2. **periodic padding**: si estende $A$ con i valori di $A$ stessa in modo periodico, circolante, tale che, nel caso dell'imaging, l'immagine si ripeta in alto, in basso, a destra e a sinistra;
3. **reflective padding**: si estende $A$ riflettendo i valori di $A$ stessa, in modo tale che, nel caso dell'imaging, l'immagine si ripeta riflessa in alto, in basso, a destra e a sinistra.

## Referenze