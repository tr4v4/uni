---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 21-04-2025 21:27:30
links:
  - "[[Lecture 14042025091835]]"
---
# Teoria della dualita'
---
## Introduzione
> La **teoria della dualità** è una teoria dell'[[Algebra lineare|algebra lineare]] che permette di associare a un [[Programmazione lineare|problema di programmazione lineare]] un altro problema, detto **duale**, che _contiene informazioni utili per risolvere il problema originale_.

In particolare questa teoria si basa sulla definizione di _involuzione_, una funzione che applicata ogni problema PL in un suo duale, il quale duale corrisponde proprio al primale.

![[teoria-della-dualita'.png]]

## Nozioni
Definiamo in particolare il concetto di coppie di problemi:
- _coppie asimmetriche_
	- primale --> $\max\{cx | Ax \leq b\}$
	- duale --> $\min\{by | A^{T}y = c \land y \geq 0\}$
- _coppie simmetriche_
	- primale --> $\max\{cx | (Ax \leq b) \land (x \geq 0)\}$
	- duale --> $\min\{by | (A^{T}y \geq c) \land (y \geq 0)\}$

## Teoremi
I due teoremi principali della teoria della dualità sono:
- [[Teorema debole di dualita']]
- [[Teorema forte di dualita']]

## Referenze
- lo stesso [[Teorema max-flow min-cut|teorema max-flow min-cut]] si puo' dimostrare usando la teoria della dualità