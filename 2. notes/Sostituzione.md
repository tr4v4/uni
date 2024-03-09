---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 21-11-2023 21:53:10
links:
  - "[[Lecture 16112023092027]]"
---
# Sostituzione
---
## Introduzione
> La **sostituzione** in [[Logica del primo ordine|logica del prim'ordine]] è un'_operazione che sfrutta la [[Alpha-convertibilità|alpha-convertibilità]] per modificare i nomi delle variabili legate di una formula_. Questo risulta necessario nel momento in cui si vuole evitare il fenomeno dello [[Shadowing|shadowing]].

Quando si sostituisce è cruciale rispettare il [[Diagramma di legame|diagramma di legame]], per questo _esiste una definizione che stabilisce regole rigorose per modificare i nomi alle variabili senza mutarne il significato semantico_.

## Definizione
La sostituzione si definisce per induzione strutturale come:
- $x[t/x]= t$
- $y[t/x]= y$
- $f^{n}(t_{1}, t_{2}, t_{3}, ...)[t/x] = f^{n}(t_{1}[t/x], t_{2}[t/x], t_{3}[t/x], ...)$
- $P^{n}(t_{1}, t_{2}, t_{3}, ...)[t/x] = P^{n}(t_{1}[t/x], t_{2}[t/x], t_{3}[t/x], ...)$
- $\bot[t/x]= \bot$
- $\top[t/x]= \top$
- $\neg F[t/x] = \neg(F[t/x])$
- $(F_{1} \land F_{2})[t/x]= F_{1}[t/x] \land F_{2}[t/x]$
- $(F_{1} \lor F_{2})[t/x]= F_{1}[t/x] \lor F_{2}[t/x]$
- $(F_{1} \implies F_{2})[t/x]= F_{1}[t/x] \implies F_{2}[t/x]$
- $(\forall x. P)[t/x]= \forall x. P$
- $(\forall y. P)[t/x]= \forall z. (P[z/y][t/x]) \text{ per } z \notin FV(t) \cup FV(P)$
- $(\exists x. P)[t/x]= \exists x. P$
- $(\exists y. P)[t/x]= \exists z. (P[z/y][t/x]) \text{ per } z \notin FV(t) \cup FV(P)$

<u>Nota bene</u>: _nei casi dei quantificatori in cui la variabile da sostituire è legata, la sostituzione non ha alcun effetto_. Questo perché sulle variabili legate un cambiamento di nome per ogni occorrenza è per forza $\alpha$-convertibile: fondamentalmente non c'è bisogno di fare una sostituzione.

<u>Nota bene</u>: _nei casi dei quantificatori in cui la variabile da sostituire è libera, la situazione si complica_. Infatti non avviene una semplice sostituzione, questo perché potrebbe verificarsi uno _shadowing tra $y$ e $t$_. Se mettiamo infatti caso di scegliere al posto di $x$ il termine $y$, esso si "confonderebbe" con l'$y$ del quantificatore (universale o esistenziale che sia). Per questo è necessario, prima di fare qualunque sostituzione di $x$, sostituire tutte le occorrenze di $y$ in $P$ con una **variabile fresca**, ovvero che non è mai stata utilizzata --> $z \notin FV(t) \cup FV(P)$.

## Referenze