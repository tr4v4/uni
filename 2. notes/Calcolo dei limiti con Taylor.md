---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 17-11-2023 20:21:38
links:
  - "[[Lecture 17112023134446]]"
  - "[[Lecture 20112023094358]]"
---
# Calcolo dei limiti con Taylor
---
## Introduzione
Per calcolare un [[Limite|limite]] di due [[Infinitesimi|infinitesimi]] $f(x)$ e $g(x)$ della forma
$$\lim_{x \to 0} \frac{f(x)}{g(x)} = \left[\frac{0}{0}\right]$$
si può sfruttare lo [[Sviluppo in serie di Taylor|sviluppo in serie di Taylor]], seguendo i seguenti passi:
1. scegliamo tra numeratore e denominatore la funzione più semplice
2. sviluppiamo [[Sviluppo in serie di Taylor#Utilizzo|fino al grado necessario]] la funzione scelta
3. sviluppiamo la restante funzione _almeno_ all'ordine di sviluppo trovato per l'altra funzione
4. calcoliamo il risultato, sfruttando l'[[Algebra degli o-piccoli|algebra degli o-piccoli]]

In particolare per il 4° punto, è importante sfruttare l'algebra degli o-piccoli per evitarsi calcoli complessi. Ricordare, per esempio, che **l'o-piccolo ingloba tutti i monomi di grado superiore**, quindi questi _si possono escludere nei calcoli_.

## Referenze