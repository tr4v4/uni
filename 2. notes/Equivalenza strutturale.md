---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 24-09-2025 23:57:22
links:
  - "[[Lecture 16042025110927]]"
---
# Equivalenza strutturale
---
## Introduzione
> Nei [[Sistema di tipi|sistemi di tipi]] che considerano una nozione **strutturale** di equivalenza (**STE**), vengono _confrontate le strutture dei tipi, ovvero la loro composizione_. Nella fattispecie, si ha che
> $$(T_{a1}, \cdots, T_{an}) \text{ STE } (T_{b1}, \cdots, T_{bn}) \iff \forall i \in [1, n], \ \ T_{ai} \text{ STE } T_{bi}$$
> (nel caso dell'equivalenza strutturale tra [[Tipo prodotto#Coppie e tuple|tuple]], ma il concetto e' sempre quello di entrare e confrontare induttivamente l'equivalenza nei tipi che compongono i tipi di partenza, fino ai [[Tipi di base|tipi base]]).
> E' eseguito staticamente. Di fatto e' la **versione statica ma piu' forte del [[Duck typing|duck typing]]**. Piu' forte/restrittiva perche' _anche se non viene usato un certo campo di una struttura (per esempio) che non corrisponde a quella richiesta come parametro formale di una funzione, il sistema di tipi da' errore_!

## Referenze