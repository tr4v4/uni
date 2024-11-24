---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 24-11-2024 14:24:43
links:
  - "[[Lecture 11112024131700]]"
---
# Matrice di convoluzione
---
## Introduzione
> La **matrice di convoluzione** (o **kernel**) è una [[Matrice|matrice]] quadrata $K \in \mathbb{R}^{D \times D}$ con $D$ dispari che viene utilizzata per applicare la [[Convoluzione|convoluzione]] ad una immagine $A \in \mathbb{R}^{M \times N}$.

## Filtri
A seconda dei valori contenuti nella matrice di convoluzione, si possono ottenere diversi effetti. Ad esempio:
- se $K$ contiene valori tutti uguali, si ottiene un _filtro di media_;
- se $K$ contiene valori positivi e negativi, con somma nulla, si ottiene un _filtro di edge detection_.
- ecc...

## Referenze