---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 30-10-2024 14:40:16
links:
  - "[[Lecture 15102024091721]]"
---
# Metodo LASSO
---
## Introduzione
> Il **metodo LASSO** è una tecnica di [[Regolarizzazione|regolarizzazione]] dell'[[Approssimazione ai minimi quadrati|approssimazione ai minimi quadrati]] della forma:
> $$\min_{\alpha} {\|X\alpha - y\|_{2}}^{2} + \lambda \|\alpha\|_{1}$$

## Idea
La funzione di regolarizzazione $\lambda \|\alpha\|_{1}$ è molto simile a quella di [[Regolarizzazione alla Tikhonov|Tikhonov]], cambia in particolare la [[Norma vettoriale|norma vettoriale]] usata: _norma 1_ e _[[Norma euclidea|norma euclidea]]_. Quali conseguenze ha?

Ebbene, se consideriamo un grafico a $d+1$ dimensioni (dove $d$ è il grado del polinomio) dei coefficienti in $\alpha$, possiamo notare che le [[Insieme di livello|curve di livello]] prodotte dalla norma euclidea compongono un cerchio, mentre quelle della norma 1 un rombo:
![[1norm-2norm.jpg]]

Se l'obiettivo della regolarizzazione è quello di porre a 0 più possibili coefficienti in $\alpha$, graficamente questo si traduce nell'_ottenere una retta tangente alla curva di livello cui punto di intersezione si trova su più assi del piano cartesiano a $d+1$ dimensioni_: **se il punto si trova sull'asse, allora il coefficiente associato all'asse ortogonale è a 0**.

Di fatto il rombo della norma 1 comporta la presenza di rette cui punto di intersezione con la curva di livello è proprio un asse, e quindi **favorisce delle soluzioni $\alpha$ contenenti un maggior numero di 0 rispetto alla norma 2**: proprio l'obiettivo della regolarizzazione.

## Risoluzione
L'efficacia di questo metodo _si paga nella non derivabilità della funzione da minimizzare_: **non è possibile passare alle equazioni normali**, ed è quindi necessario usare tecniche di [[Ottimizzazione di dati|ottimizzazione]].

## Referenze