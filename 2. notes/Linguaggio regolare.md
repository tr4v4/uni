---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 07-10-2024 22:10:59
links:
  - "[[Lecture 03102024120247]]"
---
# Linguaggio regolare
---
## Introduzione
> Un [[Linguaggio formale|linguaggio]] $L \subseteq A^{*}$ (su alfabeto $A$) è detto **regolare** $\iff$ $\exists$ una [[Espressione regolare|espressione regolare]] $r$ tale che $L$ sia un [[Linguaggio denotato da un'espressione regolare|linguaggio denotato]] da $r$, ossia
> $$L = \mathscr{L}[r]$$

### Esempi
Fissato l'alfabeto $A = \{0, 1\}$, definiamo delle espressioni regolari e i linguaggi regolari ad essi associati:
- $0^{*}10^{*}$ è $L = \{w \in A^{*} | w \text{ contiene un solo 1}\}$
- $(0|1)^{*}1(0|1)^{*}$ è $L = \{w \in A^{*} | w \text{ contiene almeno un 1}\}$
- $(0|1)^{*}001(0|1)^{*}$ è $L = \{w \in A^{*} | w \text{ contiene 001 come sottostringa}\}$
- $1^{*}(001^{*})^{*}$ è $L = \{w \in A^{*} | \text{ogni occorrenza di 0 è seguita immediatamente da almeno un 1}\}$
- $((0|1)\cdot(0|1))^{*}$ è $L = \{w \in A^{*} | w \text{ è di lunghezza pari}\}$
- $(0|1)^{*}1$ è $L = \{w \in A^{*} | w \text{ termina con un 1}\}$

## Proposizioni
### 1.
> _Ogni linguaggio finito è regolare_.

Si prenda come esempio l'espressione regolare $r=a/bc$, e dimostro che $\mathscr{L}[r]=L$ con $L$ linguaggio finito:
$$\mathscr{L}[a/bc] = \mathscr{L}[a] \cup \mathscr{L}[bc] = \{a\} \cup \mathscr{L}[b]\cdot\mathscr{L}[c] = \{a\} \cup \{b\} \cdot \{c\} = \{a\} \cup \{bc\} = \{a, bc\}$$

<u>Nota bene</u>: esistono comunque linguaggi regolari infiniti, come $\mathscr{L}[a^{*}b] = \{a^{n}b | n \geq 0\}$ o $\mathscr{L}[a/a^{*}b] = \{a\} \cup \{a^{n}b | n \geq 0\}$.

## Referenze