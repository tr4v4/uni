---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 24-03-2025 16:57:35
links:
  - "[[Lecture 12032025091447]]"
---
# Teorema max-flow min-cut
---
## Introduzione
> Il **teorema max-flow min-cut** dice che _il valore del massimo [[Flusso|flusso]] è uguale alla minima capacità dei [[Taglio|tagli]]_.

## Dimostrazione
Per dimostrare il teorema ci avvaliamo dell'[[Algoritmo di Ford-Fulkerson|algoritmo di Ford-Fulkerson]]. Supponiamo infatti di aver trovato il flusso massimo $x$ con tale algoritmo. Ora, prendiamo il [[Taglio s-t|taglio s-t]] $(N_{s}, N_{t})$ tale che $N_{s}$ contenga tutti i nodi raggiungibili da $s$ nel [[Grafo residuo|grafo residuo]] $G_{x}$, e $N_{t} = N \setminus N_{s}$. A questo punto, dal lemma sull'algoritmo, sappiamo che tale taglio ha proprio la capacità del flusso massimo $x$.

Segue che _questo taglio dev'essere quello di capacità minima_: se non fosse di capacità minima, allora preso un altro taglio questo verrebbe attraversato da $x$, il che violerebbe il lemma sulle capacità dei tagli.

**Qed**.

## Referenze