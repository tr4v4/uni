---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 23-09-2025 17:13:10
links:
  - "[[Lecture 09042025110710]]"
---
# Tipo somma
---
## Introduzione
> I [[Tipi di dato|tipi di dato]] [[Tipi composti|composti]] **somma**, anche detti **tipi scelta** o **coprodotti**, sono _tipi che indicano che una [[Variabile|variabile]] di quel tipo puo' contenere un'unione disgiunta di tipi_.

Per esempio, se prendiamo $\text{int} = \{-13, 0, 1, 17, \cdots\}$ e $\text{char} = \{Y, a, Z, b, H, \cdots\}$, allora il tipo
$$\text{int} \cup \text{char} = \{-13, Y, 0, a, 1, Z, \cdots\}$$
indica un _tipo di una variabile che puo' assumere sia un valore intero che un valore carattere_.

Visto che tecnicamente, tra i caratteri ci sono anche i caratteri $\{0, 1, 2, \cdots\}$, per non confonderli con gli interi si tiene traccia per ogni abitante dell'insieme (`int` e `char`) a che tipo fa riferimento nel tipo somma:
$$\text{int}^{*} \cup \text{char}^{*} = \{(-13, i), (Y, c), (0, i), (a, c), (1, i), (5, c), \cdots\}$$

## Rappresentazione
Alcuni linguaggi, come [[Rust]], hanno esteso la loro definizione dei [[Tipi di base#Enum|tipi enum]] per catturare il caso dei tipi di somma. [[Java]] invece usa le `sealed` classes. In [[C]] si usano le `union` (ma a quel punto non c'e' differenza tra un tipo della somma e l'altro...).

## Referenze