---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 28-03-2024 15:17:36
links:
  - "[[Lecture 21032024091145]]"
  - "[[Lecture 25032024091657]]"
---
# Fattore di carico
---
## Introduzione
> Il **fattore di carico** $\alpha$ nel contesto delle [[Tabella hash|tabelle hash]] equivale al _rapporto tra il numero di elementi presenti nella tabella e la grandezza della tabella stessa_, ovvero
> $$\alpha = \frac{n}{m}$$
> dove:
> - $n$ è il numero di elementi presenti;
> - $m$ è il numero di slot della tabella;

## Teorema
> Sotto l'ipotesi di [[Uniformità semplice|hashing uniforme semplice]], **ogni slot della tabella ha mediamente $\alpha$ chiavi**.

## Ruolo
A prescindere da quale metodo di mitigazione delle [[Collisione hash|collisioni hash]] viene adottato è importante mantenere un fattore di carico basso. In particolare un fattore di carico
$$\alpha < 0.75$$
è **considerato ottimale**. L'idea è allora quella di **ridimensionare la tabella hash quando $\alpha$ supera questa soglia**. Ma attenzione: _il ridimensionamento comporta la totale ricostruzione della tabella, poiché gli indici hash cambiano_!

## Referenze