---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 24-03-2024 15:57:34
links:
  - "[[Lecture 19032024112453]]"
---
# Albero bilanciato
---
## Introduzione
> Un [[Albero binario|albero binario]] si dice **bilanciato** (o **bilanciato in altezza**) se per ogni nodo $v$ il [[Fattore di bilanciamento|fattore di bilanciamento]] $\beta(v)$ è compreso tra -1 e 1:
> $$|\beta(v)| \leq 1$$

### Esempi
![[albero-bilanciato.png]]
![[albero-sbilanciato.png]]

## Tipi
Ci sono una serie di alberi autobilancianti che sono state ideate e implementate, tra cui:
- [[Albero AVL]]
- [[B-albero]]
- [[Albero 2-3]]
- [[RB-albero]]

Tutte queste supportano operazioni di inserimento, ricerca e rimozione in [[Complessità computazionale|tempo logaritmico]].

## Referenze