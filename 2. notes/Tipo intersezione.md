---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 17-10-2025 21:42:56
links:
  - "[[Lecture 14052025105842]]"
---
# Tipo intersezione
---
## Introduzione
> I **tipi intersezione** sono una diretta conseguenza delle proprieta' del [[Sottotipaggio|sottotipaggio]] nel contesto della [[OOP]]. Infatti $S$ e' un tipo intersezione se
> $$S <: R \land T$$
> In tal caso $S$ indica l'intersezione dei valori che abitano in $R$ e in $T$. E se $R$ e $T$ non si sovrappongono, ecco che $S$ diventa l'unione delle loro capacita'[^1].

In [[Java]] questo si fa **estendendo un'[[Interfaccia|interfaccia]] con una lista di interfacce**.
```Java
interface Reader {Readable read()}
interface Writer {void write(Writable w)}
interface RW extends Reader, Writer {}
```

## Referenze

[^1]: diversa tuttavia dai [[Tipo somma|tipi somma]]: in questi ultimi diciamo il tipo o e' uno o e' un'altro; nei tipi intersezioni diciamo che e' sia uno che l'altro!
