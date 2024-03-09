---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 24-10-2023 10:25:52
links:
  - "[[Lecture 19102023092110]]"
  - "[[Lecture 09112023131356]]"
---
# Regole di inferenza dell'OR
---
## Introduzione
### [[Regole di introduzione|Introduzione]]
Ci sono 2 regole d'introduzione dell'OR. Per dimostrare una disgiunzione $F_{1} \lor F_{2}$ devo infatti scegliere se dimostrare $F_{1}$ o $F_{2}$:
![[regole-introduzione-OR.png]]

Proprio per questa **scelta**, queste regole _non sono [[Invertibilità di una regola di inferenza|invertibili]] (fortemente)_. Per questo solitamente durante una dimostrazione si cerca di postporre il suo utilizzo il più possibile: **non sappiamo quale delle due tesi sia dimostrabile**.

#### [[Teorema di correttezza|Correttezza]]
Se vale $F_{1} \vdash F_{1} \lor F_{2}$, allora dobbiamo dimostrare
$$F_{1} \Vdash F_{1} \lor F_{2}$$

Assumiamo di essere in un mondo $v$ in cui $[[F_{i}]]^{v} = 1$ per $i \in \{1, 2\}$, abbiamo per la [[Semantica classica#Definizione|definizione di semantica classica]] $\max \{[[F_{1}]]^{v}, [[F_{2}]]^{v}\}$ che può essere $\max \{1, [[F_{2}]]^{v}\} = 1$ o $\max \{[[F_{1}]]^{v}, 1\} = 1$.

**Qed**.

### [[Regole di eliminazione|Eliminazione]]
Per questa regola bisogna _procedere per casi_. Se sappiamo $F_{1} \lor F_{2}$, dobbiamo dimostrare $F$ per entrambi i casi possibili, ovvero per quello in cui vale $F_{1}$ e per quello in cui vale $F_{2}$:
![[regola-eliminazione-OR.png]]

Anche in questo caso, _a meno che non si abbia $F_{1} \lor F_{2}$ come ipotesi, la regola non è invertibile_.

## Referenze