---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 27-08-2025 19:03:04
links:
  - "[[Lecture 07112024120244]]"
  - "[[Lecture 12112024110924]]"
---
# Grammatiche LL(1)
---
## Introduzione
> Una [[Grammatiche|grammatica]] e' $LL(1)$ $\iff$ ogni casella della [[Tabella di parsing LL(1)|tabella di parsing]] $LL(1)$ contiene al piu' una produzione.

Se $G$ e' $LL(1)$, allora _il [[Parser top-down|parser top-down]] ricostruisce l'[[Albero di derivazione|albero di derivazione]] per l'input $w$ in modo top-down, predicendo quale produzione usare (tra le possibili per uno stesso nonterminale) guardando il prossimo carattere dell'input_.

<u>Nota bene</u>: un [[Linguaggio formale|linguaggio]] e' $LL(1)$ se esiste una grammatica di classe $LL(1)$ che lo genera[^1].

## Teoremi
### First e follow
Questo teorema connette le grammatiche $LL(1)$ con i [[First e follow|first e follow]].
> Una grammatica $G$ e' $LL(1)$ $\iff$ per ogni coppia di produzioni distinte con la stessa testa
> $$A \to \alpha | \beta$$
> si ha che:
> 1. $\text{First}(\alpha) \cap \text{First}(\beta) = \varnothing$;
> 2. $\epsilon \in \text{First}(\alpha) \implies \text{First}(\beta) \cap \text{Follow}(A) = \varnothing$;
> 3. $\epsilon \in \text{First}(\beta) \implies \text{First}(\alpha) \cap \text{Follow}(A) = \varnothing$.

Fondamentalmente ci da' un criterio per determinare se una grammatica e' $LL(1)$ senza dover costruire la tabella di parsing!

#### Dimostrazione
Lo sketch della dimostrazione prevede di utilizzare la tabella di parsing $LL(1)$ corrispondente della grammatica $LL(1)$. Infatti se valgono le 3 condizioni allora la tabella di parsing contiene al piu' una produzione in ogni casella; e vale anche il viceversa.

### Linguaggi regolari
> Ogni [[Linguaggio regolare|linguaggio regolare]] e' [[Linguaggio generato|generabile]] da una grammatica $G$ di classe $LL(1)$.

#### Dimostrazione
Se $L$ e' regolare allora $\exists$ un [[DFA]] $M = (\Sigma, Q, \delta, q_{0}, F)$ tale che $L = L[M]$. A partire da $M$ costruiamo la grammatica regolare $G = (NT, T, S, R)$ con $NT = \{[q] | q \in Q\}$[^2], $T = \Sigma$, $S = [q_{0}]$ e $R$ definita da:
- se $\delta(q, a) = q'$ allora $[q] \to a[q'] \in R$;
- se $q \in F$ allora $[q] \to \epsilon \in R$.

In questo modo **$G$ e' sicuramente $LL(1)$**.

Infatti:
- considerando che $M$ e' un DFA, allora per ogni stato $[q]$ e per ogni carattere $a$ esistera' una sola produzione $[q] \to a[q']$, per cui i first delle produzioni di uno stesso nonterminale avranno sempre intersezione nulla;
- inoltre, le uniche produzioni-$\epsilon$ si hanno da $q \in F$, che hanno come follow per forza di cose solo $\$$, che non puo' mai essere un first di un qualunche altro $\beta$.

**Qed**.

## Referenze
- [[Grammatiche LL(k)]]

[^1]: e' fondamentalmente la stessa definizione di [[Linguaggio ambiguo|linguaggio non ambiguo]]
[^2]: raccoglie gli stati nella [[Relazione di equivalenza|relazione di equivalenza]] (sistema usato nella [[Minimizzazione di DFA|minimizzazione di DFA]])
