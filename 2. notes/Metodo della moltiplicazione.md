---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 24-03-2024 22:01:55
links:
  - "[[Lecture 21032024091145]]"
---
# Metodo della moltiplicazione
---
## Introduzione
> Il **metodo della moltiplicazione** è una [[Funzione hash|funzione hash]] $h$ che presa in input una chiave $k$ è definita come
> $$h(k) = \lfloor m(kC - \lfloor kC \rfloor) \rfloor$$
> dove $m$ è la lunghezza dell'[[Array|array]] `T` della [[Tabella hash|tabella hash]] e $C$ una costante $\in ]0, 1[$. Fondamentalmente _si moltiplica $k$ per $C$ e si tiene la parte frazionaria; quindi si moltiplica ques'ultima per $m$ e si tiene la parte intera_.

In questo caso il valore di $m$ non è critico (a differenza di quanto avviene con il [[Metodo della divisione|metodo della divisione]]), ma $C$ influenza la _proprietà di uniformità_ di $h$. La costante $C = \frac{\sqrt{5} - 1}{2}$[^1] suggerita da [[Knuth]] e in seguito smentita dovrebbe statisticamente favorire la distribuzione delle chiavi.

## Referenze
[^1]: $\phi$, in _The Art of Computer Programming_