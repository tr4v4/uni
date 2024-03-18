---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 29-12-2023 19:37:39
links:
  - "[[Lecture 13122023131453]]"
---
# Definizione di proiezione
---
## Introduzione
> Dato un [[Morfismo|morfismo]] $f: \mathbb{A} \to \mathbb{B}$ e una [[Definizione di relazione di equivalenza indotta di un morfismo|relazione di equivalenza indotta]] $\sim_{f}$, si definisce **funzione di proiezione**
> $$[\cdot]: \mathbb{A} \to \mathbb{A}_{/\sim_{f}}$$
> la [[Funzione matematica|funzione]] che mappa ogni elemento $x \in \mathbb{A}$ nella sua [[Classe di equivalenza|classe di equivalenza]] rispetto alla relazione $\sim_{f}$, t.c. $[x]_{\sim_{f}} := \{x' \in \mathbb{A} | x' \sim_{f} x\}$.

<u>Nota bene</u>: l'elemento che viene scelto per rappresentare la classe di equivalenza nell'[[Insieme quoziente|insieme quoziente]] $\mathbb{A}_{/\sim_{f}}$ è detto _rappresentante_.

Nota anche che, in quanto definita da $\mathbb{A}$ al suo quozientamento rispetto a $\sim_{f}$, _la funzione di proiezione è sempre [[Funzione suriettiva|suriettiva]]_. Viceversa _è efficace sse NON è [[Funzione iniettiva|iniettiva]], perché se lo fosse non avverrebbe alcuna [[Astrazione|astrazione]] di $\mathbb{A}$_.

Possiamo fondamentalmente definire **la proiezione di un insieme rispetto a un morfismo come alla sua astrazione rispetto ad una certa proprietà, che raggruppa gli elementi che hanno la stessa immagine nella propria classe di equivalenza**.

## Referenze