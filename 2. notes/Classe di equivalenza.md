---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 15-10-2023 18:12:28
links:
  - "[[Lecture 11102023131154]]"
---
# Classe di equivalenza
---
## Introduzione
> Definita $\equiv \subseteq A \times A$ come una [[Relazione di equivalenza|relazione di equivalenza]] su $A$, si definisce **classe di equivalenza** di $x \in A$ rispetto a $\equiv$ l'insieme:
> $$[x]_{\equiv} = \{y \in A | y \equiv x\}$$
> ovvero, $[x]_{\equiv}$ rappresenta tutti elementi $y$ di $A$ che sono in relazione di equivalenza con $x$.

### Esempi
Se prendiamo $A$ come l'insieme delle parole, allora per la relazione $\equiv \subseteq A \times A$ definita come _avere la stessa lettera iniziale_ avviene che:
- $[albero]_{\equiv} = \{albero, alga, armadillo, ...\}$
- $[alga]_{\equiv} = \{albero, alga, armadillo, ...\}$
- $[banana]_{\equiv} = \{banana, borsetta, bullo, ...\}$

E quindi che
- $[albero]_{\equiv} = [alga]_{\equiv}$
- $[albero]_{\equiv} \cap [banana]_{\equiv} = \varnothing$

## Teorema
Per la relazione di equivalenza $\equiv \subseteq A \times A$, per ogni $x, y \in A$:
- $[x]_{\equiv} = [y]_{\equiv}$, se $x \equiv y$
- $[x]_{\equiv} \cap [y]_{\equiv} = \varnothing$, se $x \not \equiv y$

## Referenze
- [[Insieme quoziente]]