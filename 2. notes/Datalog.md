---
tags:
  - category/note
  - status/pending
  - topic/basi-di-dati
date: 13-10-2025 12:56:16
links:
  - "[[Lecture 09102025151427]]"
---
# Datalog
---
## Introduzione
> **Datalog** è un linguaggio per le query su [[Database|database]], ispirato a [[Prolog]].

I predicati sono divisi in:
- _predicati estensionali_ - relazioni delle basi di dati;
- _predicati intensionali_ - corrispondono alle [[Viste|viste]];

I predicati intensionali sono definiti mediante regole con la seguente sintassi:
$$head \leftarrow body$$
dove:
- $head$ è un _predicato atomico_ (intensionale);
- $body$ è una _congiunzione di predicati atomici_;

Le query sono specificato usando il prefisso $?$.

### Esempi
La query
$$?EMPLOYEE(Number: m, Name: n, Age: 30, Wage: w)$$
restituisce tutti i dipendenti con età pari a 30.

La query
$$RICHER(Number: m, Name: n, Age: a, Wage: w) \leftarrow EMPLOYEE(Number: m, Name: n, Age: a, Wage: w), w > 40$$
$$? RICHER(Number: m, Name: n, Age: a, Wage: w)$$
restituisce i dipendenti che guadagnano più di 40 soldi.



## Referenze