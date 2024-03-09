---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 28-11-2023 19:47:47
links:
  - "[[Lecture 22112023134305]]"
---
# ADT
---
## Introduzione
> Gli **ADT** (_Algebric Data Type_) sono un _[[Tipi di dati|tipo di dato]] definito algebricamente_.

Sono alla base di ciò che è processabile per mezzo di [[Ricorsione|ricorsione]]/[[Ricorsione strutturale|ricorsione strutturale]]. Di fatto costituiscono il tipo di dato "base" della maggior parte dei [[Linguaggio di programmazione funzionale|linguaggi di programmazione funzionale]].

## Composizione
Un tipo di dato algebrico si compone di:
- _nome del tipo_ (es. naturale, lista di naturali, coppia, ecc...)
- _lista di possibili forme_ (o _costruttori_ per quel tipo)[^1]

e _possono contenere altri tipi di dati nella loro definizione_, anche _loro stessi_ (usando la ricorsione).

<u>Osservazione</u>: ogni valore di un ADT è un **albero** i cui nodi sono una possibile forma e i cui sotto-alberi sono altri valori.

### Esempi
- `Booleani`: $\mathbb{B} ::= tt \ | \ ff$
- `Numeri naturali`: $\mathbb{N} ::= O \ | \ S \ \mathbb{N}$
- `Liste di numeri naturali`: $\mathbb{L} ::= [] \ | \ \mathbb{N} :: \mathbb{L}$
- `Coppie formate da un booleano e un naturale`: $C ::= (\mathbb{B}, \mathbb{N})$
- `Alberi binari con numeri nelle foglie`: $T ::= \mathbb{N} \ | \ T \cdot T$
- `Alberi binari con numeri nei nodi interni`: $T' ::= \varnothing \ | \ \mathcal{N}(T', \mathbb{N}, T')$

<u>Nota bene</u>: valgono le _regole di associatività e precedenza degli operatori_, quindi usare le parentesi per evitare confusioni.

## Referenze
[^1]: stessa sintassi della [[Logica proposizionale|logica proposizionale]]