---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-08-2025 19:10:31
links:
  - "[[Lecture 05112024110833]]"
---
# Produzioni epsilon
---
## Introduzione
> In una [[Grammatiche|grammatica]] le **produzioni-$\epsilon$** sono produzioni per un nonterminale della forma
> $$A \to \epsilon$$

Di solito si vogliono eliminare per favorire i [[Parser bottom-up|parser bottom-up]].

## Eliminazione
In input abbiamo una [[Grammatiche libere|grammatica libera]] $G$ che contiene produzioni-$\epsilon$, e in output vogliamo una grammatica libera $G'$ senza produzioni-$\epsilon$, tale che
$$L(G') = L(G) \setminus \{\epsilon\}$$

Notiamo che a partire da $G'$, possiamo tornare a $G$ semplicemente introducendo una produzione $S' \to \epsilon | S$ con $S'$ simbolo di $G''$ (equivalente a $G$) e $S$ simbolo iniziale di $G'$.

Per poter andare avanti, introduciamo la definizione di _simbolo annullabile_.

### Simbolo annullabile
> Un simbolo $A \in NT$ si dice **annullabile** quando $A \implies^{+} \epsilon$.

Allora raggruppiamo tutti i simboli annullabili della grammatica $G$ in
$$N(G) = \{A \in NT | A \implies^{+} \epsilon\}$$
calcolato induttivamente come:
- $N_{0}(G) = \{A \in NT | A \to \epsilon \in R\}$
- $N_{i+1}(G) = N_{i}(G) \cup \{B \in NT | B \to C_{1} \cdots C_{k} \in R \land C_{1}, \cdots, C_{k} \in N_{i}(G)\}$

Notiamo che $N_{i}(G) \subseteq N_{i+1}(G)$, ma soprattutto che
$$\exists i_{C} : N_{i_{C}}(G) = N_{i_{C}+1}(G)$$
perche' $NT$ e' finito!

A questo punto **$N(G) = N_{i_{C}}(G)$ e' l'insieme di tutti i simboli annullabili**.

### Algoritmo
Una volta calcolato questo insieme per $G = (NT, T, S, R)$, costruiamo la grammatica $G' = (NT, T, S, R')$ dove _per ogni produzione $A \to \alpha \in R$, con $\alpha \neq \epsilon$, in cui occorrono i simboli annullabili $Z_{1}, \cdots, Z_{k}$ ($\in N(G)$), mettiamo in $R'$ tutte le produzioni del tipo $A \to \alpha'$ dove $\alpha'$ si ottiene da $\alpha$ cancellando tutti i possibili sottoinsiemi di $Z_{1}, \cdots, Z_{k}$ (incluso $\varnothing$), ad eccezione del caso in cui $\alpha'$ risulti $\epsilon$ (post-cancellazione)_.

In questo modo garantiamo che:
- in $G'$ non mettiamo mai produzioni $A \to \epsilon \in R$;
- in $G'$ non introduciamo mai nuove produzioni $A \to \epsilon$.

Detto cio', e' facilmente dimostrabile che **data una grammatica libera $G$, la grammatica $G'$ determinata dall'algoritmo sopra non ha produzioni-$\epsilon$ e $L(G') = L(G) \setminus \{\epsilon\}$**.

Ricordiamo che se poi vuoi proprio che $G'$ sia equivalente a $G$, allora definendo
$$G'' = (NT \cup \{S'\}, T, S', R' \cup \{S' \to \epsilon|S\})$$
avrai che $L(G'') = L(G)$.

### Esempio
Prendiamo la grammatica $G$ definita da
$$S \to AB \ \ \ \ \ A \to aAA|\epsilon \ \ \ \ \ B \to bBB|\epsilon$$

Calcoliamo l'insieme dei simboli annullabili:
- $N_{0}(G) = \{A, B\}$
- $N_{1}(G) = \{A, B, S\}$
- $N(G) = N_{1}(G) = \{A, B, S\}$

A questo punto prendiamo la produzione $S \to AB$ e togliamo da $AB$ ogni possibile sottoinsieme di $N(G) = \{A, B, S\}$ (ovviamente non consideriamo $S$):
- $\varnothing \implies S \to AB$, la mettiamo in $G'$;
- $\{A\} \implies S \to B$, la mettiamo in $G'$;
- $\{B\} \implies S \to A$, la mettiamo in $G'$;
- $\{A, B\} \implies S \to \epsilon$, NON la mettiamo in $G'$;

Quindi in $G'$ avremo $S \to AB|A|B$.

Ora consideriamo la produzione $A \to aAA$:
- $\varnothing \implies A \to aAA$, la mettiamo in $G'$;
- $\{A\} \implies A \to aA$, la mettiamo in $G'$;
- $\{A\} \implies A \to aA$, la mettiamo in $G'$ (copia della precedente! la mettiamo solo una volta...);
- $\{A, A\} \implies A \to a$, la mettiamo in $G'$;

Quindi in $G'$ avremo $A \to aAA|aA|a$, e rispettivamente quindi $B \to bBB|bB|b$.

<u>Nota bene</u>: le due produzioni $A \to \epsilon$ e $B \to \epsilon$ sono ignorate.

A questo punto la grammatica $G'$ sara':
$$S \to AB|A|B \ \ \ \ \ A \to aAA|aA|a \ \ \ \ \ B \to bBB|bB|b$$
e ovviamente pero' $\epsilon \notin L(G')$. Per rimediare e quindi ottenere una [[Grammatiche equivalenti|grammatica equivalente]] a $G$ costruiamo la grammatica $G''$ che ha simbolo iniziale $S'$ e come produzione in piu' $S' \to \epsilon|S$.

## Referenze