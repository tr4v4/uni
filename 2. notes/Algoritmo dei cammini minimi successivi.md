---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 24-03-2025 20:52:29
links:
  - "[[Lecture 19032025092241]]"
---
# Algoritmo dei cammini minimi successivi
---
## Introduzione
> L'**algoritmo dei cammini minimi successivi** è un [[Algoritmo|algoritmo]] per risolvere il [[Problema del flusso di costo minimo|problema del flusso di costo minimo]], basata sulla nozione di _pseudoflusso minimale_.

## Algoritmo
1. definiamo $x$ uno pseudoflusso minimale;
2. se lo sbilanciamento complessivo è 0 ($g(x) = 0$) terminiamo e restituiamo $x$;
3. cerchiamo un cammino di costo minimo $P$ da un nodo $i \in O_{x}$ e $j \in D_{x}$; se non esiste termina perché il problema è vuoto;
4. $x = x(P, \min\{\theta(P, x), e_{x}(i) - e_{x}(j)\})$;
5. torna al punto 2.

## Referenze