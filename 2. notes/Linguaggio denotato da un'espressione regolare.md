---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 07-10-2024 22:02:25
links:
  - "[[Lecture 03102024120247]]"
---
# Linguaggio denotato da un'espressione regolare
---
## Introduzione
> Dato l'alfabeto $A$, definiamo la [[Funzione matematica|funzione]]
> $$\mathscr{L}: \text{ExpReg} \to \mathscr{P}(A^{*})$$
> che associa ad ogni [[Espressione regolare|espressione regolare]] un [[Definizione di essere sottoinsieme|sottoinsieme]][^1] di tutte le combinazioni delle lettere di $A$, ossia un [[Linguaggio formale|linguaggio]], come
> - $\mathscr{L}[\varnothing] = \varnothing$
> - $\mathscr{L}[\epsilon] = \{\epsilon\}$
> - $\mathscr{L}[a] = \{a\}$
> - $\mathscr{L}[r_{1} \cdot r_{2}] = \mathscr{L}[r_{1}] \cdot \mathscr{L}[r_{2}]$
> - $\mathscr{L}[r_{1} / r_{2}] = \mathscr{L}[r_{1}] \cup \mathscr{L}[r_{2}]$
> - $\mathscr{L}[r^{*}] = (\mathscr{L}[r])^{*}$
> 
> Il linguaggio in output della funzione è detto **linguaggio denotato da un'espressione regolare**.

<u>Nota bene</u>: nella definizione del linguaggio denotato, **ciò che appare nel dominio sono le produzioni dell'espressione regolare**, mentre **l'elemento del codominio associato è un linguaggio**.

## Referenze
[^1]: il codominio, di fatto, è l'[[Assioma dell'insieme potenza|insieme delle parti]] di $A^{*}$