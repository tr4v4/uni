---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
  - topic/logica-per-informatica
date: 24-09-2023 17:22:05
links:
  - "[[Lecture 22092023133316]]"
  - "[[Lecture 29092023135952]]"
  - "[[Lecture 11102023131154]]"
  - "[[Lecture 12102023091734]]"
---
# Numerabilità
---
## Definizione
> Un insieme si dice **numerabile** se è [[Equipotenza|equipotente]] a $\mathbb{N}$. Se un insieme è numerabile allora avrà la cosiddetta _cardinalità del numerabile_, indicata con si indica con $\aleph_{0}$.

<u>Osservazione</u>: **$\aleph_{0}$ è il più piccolo degli infiniti**[^1].

## Dimostrazioni
In generale, per dimostrare che un insieme è equipotente a un altro basta trovare una [[Funzione biiettiva|funzione biunivoca]] tra di essi. Ma per essere numerabile, un insieme basta che sia _codominio_ di una funzione suriettiva. Vale a dire che
$$f: \mathbb{N} \to A \text{ su} \implies |A| = |\mathbb{N}|$$

### $\mathbb{P} \to \mathbb{N}$
Se volessimo dimostrare per esempio che l'insieme dei numeri pari $\mathbb{P}$ ($\subsetneqq \mathbb{N}$) sia numerabile, quindi equipotente a $\mathbb{N}$, procederemmo trovando una funzione biunivoca tra i due insiemi. Per esempio
$$f: P \to N | f(p)=\frac{p}{2}$$
Visualizzando la funzione otterremo
![[Drawing 2023-09-24 18.13.10.excalidraw|750]]
da cui possiamo notare che è _biunivoca_. Per cui $\mathbb{P}$ è **numerabile**.

### Altre dimostrazioni
- [[Dimostrazione Z numerabile]]
- [[Dimostrazione Q numerabile]]
- [[Dimostrazione R non numerabile]]

Da cui si ottiene l'importante risultato
$$|\mathbb{N}| = |\mathbb{Z}| = |\mathbb{Q}| = |\mathbb{N} \times \mathbb{N}| < |\mathbb{R}|$$

## Referenze
[^1]: [[Teorema di Cantor]]