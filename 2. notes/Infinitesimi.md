---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 12-11-2023 18:15:09
links:
  - "[[Lecture 10112023134301]]"
  - "[[Lecture 13112023094129]]"
---
# Infinitesimi
---
## Introduzione
> Un **infinitesimo** è una _[[Funzione matematica|funzione]] che tendente a un punto converge a 0_, per cui quindi vale che
> $$\lim_{x \to x_{0}} f(x) = 0$$

## Confronto
Quando si vogliono confrontare due infinitesimi, per capire quali dei due cresce meno velocemente, si fa il limite del loro rapporto:
$$\lim_{x \to x_{0}} \frac{f(x)}{g(x)} = \begin{cases} L = 0 & f(x) \text{ infinitesimo di ordine superiore a } g(x) \\ L = \pm \infty & g(x) \text{ infinitesimo di ordine superiore a } f(x) \\ 0 < L \in \mathbb{R} & f(x) \text{ infinitesimo dello stesso ordine di } g(x) \end{cases}$$

Da questo nasce la [[Gerarchia degli infinitesimi|gerarchia degli infinitesimi]], dimostrabile con il [[Teorema di de l'Hopital|teorema di de l'Hopital]].

<u>Nota bene</u>: quando due infinitesimi tendono a 0 alla stessa velocità, essi sono detti **equivalenti**.

## Utilizzo
Gli infinitesimi, nel contesto dello [[Sviluppo in serie di Taylor|sviluppo in serie di Taylor]], diventano il prototipo dell'errore: [[O-piccolo|o-piccolo]].

## Referenze