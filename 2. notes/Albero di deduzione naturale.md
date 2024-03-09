---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 15-10-2023 22:29:16
links:
  - "[[Lecture 12102023091734]]"
  - "[[Lecture 18102023131238]]"
---
# Albero di deduzione naturale
---
## Introduzione
> Un **albero di deduzione naturale** per $\Gamma \vdash F$ (dove $\Gamma$ sono le _ipotesi globali_ e $F$ la _tesi da dimostrare_) è una [[Strutture dati|struttura dati]] _arborescente_.

I nodi dell'albero fanno a loro volta partire sotto-alberi, fino ad arrivare a delle foglie, in una _struttura [[Ricorsione|ricorsiva]]_.

## Composizione
Si tratta di un albero che viene rappresentato partendo dal basso (come da natura) ma al quale ci si riferisce al contrario: _il basso è l'alto e l'alto è il basso_.
Ora:
- i nodi sono etichettati da formule
- le foglie sono formule scaricate
	- $[G]$ se con **ipotesi locali**
	- $G$ se con **ipotesi globali**
- la radice è etichettata con $F$
- le foglie non scaricate sono etichettate con formule appartenenti a $\Gamma$
- i nodi interni, oltre alla formula, sono etichettati con delle [[Regole di inferenza|regole di inferenza]]

## Referenze