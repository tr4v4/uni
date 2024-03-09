---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 18-10-2023 20:43:54
links:
  - "[[Lecture 18102023131238]]"
  - "[[Lecture 19102023092110]]"
  - "[[Lecture 09112023131356]]"
---
# Regole di inferenza dell'AND
---
## Regole
### [[Regole di introduzione|Introduzione]]
Devo dimostrare
$$F_{1} \land F_{2}$$
allora dimostro $$F_{1} \text{ e } F_{2}$$
_E' invertibile_.
![[regola-introduzione-and.png]]

<u>Nota bene</u>: questa regola _ramifica in 2 rami_ da provare.

#### [[Teorema di correttezza|Correttezza]]
Per la definizione di correttezza, usando la regola $F_{1}, F_{2} \vdash F_{1} \land F_{2}$ dobbiamo dimostrare che
$$F_{1}, F_{2} \Vdash F_{1} \land F_{2}$$

Assumiamo quindi di trovarci in un [[Mondo|mondo]] $v$ in cui $[[F_{1}]]^{v} = [[F_{2}]]^{v} = 1$, abbiamo che $[[F_{1} \land F_{2}]] = \min \{[[F_{1}]]^{v}, [[F_{2}]]^{v}\} = 1$.

**Qed**.

#### [[Invertibilità di una regola di inferenza|Invertibilità]]
Per la definizione di invertibilità, dobbiamo dimostrare
$$F_{1} \land F_{2} \Vdash F_{i} \ \ \ \ \ (i \in \{1, 2\})$$

Assumiamo di trovarci in un mondo $v$ in cui $[[F_{1} \land F_{2}]]^{v} = \min \{[[F_{1}]]^{v}, [[F_{2}]]^{v}\} = 1$, allora si ha per forza che $[[F_{i}]]^{v} = 1$ per ogni $i \in \{1, 2\}$.

### [[Regole di eliminazione|Eliminazione]]
Ho 
$$F_{1} \land F_{2}$$
quindi
$$\text{suppongo } F_{1} \text{ e suppongo } F_{2}$$

_Non è [[Invertibilità di una regola di inferenza|invertibile]], lo diventa se $F_{1} \land F_{2}$ sono dimostrabili_, per esempio se sono ipotesi.
![[regola-eliminazione-and.png]]

<u>Nota bene</u>: questa regola _non ramifica su alcun nuovo ramo_.

#### Eliminazione alternativa
Si può anche scrivere con molta più rapidità, in accordo al principio di [[Derivabilità di una regola di inferenza|derivabilità]]:
![[regole-eliminazione-alternative-AND.png]]

#### Correttezza
Vogliamo dimostrare
$$F_{1} \land F_{2}, F_{1} \implies F_{2} \implies F_{3} \vdash F_{3}$$

Applicando la [[Semantica classica#Definizione|definizione di semantica classica]], per un mondo $v$, abbiamo che $[[F_{1} \land F_{2}]]^{v} = \min \{[[F_{1}]]^{v}, [[F_{2}]]^{v}\} = 1$, da cui $[[F_{1}]]^{v} = [[F_{2}]]^{v} = 1$. La seconda ipotesi invece si traduce in $\max \{1 - [[F_{1}]]^{v}, 1 - [[F_{2}]]^{v}, [[F_{3}]]^{v}\} = \max \{0, 0, [[F_{3}]]^{v}\} = [[F_{3}]]^{v} = 1$. Da cui $[[F_{3}]]^{v} = 1$ in ogni mondo $v$.

**Qed**.

#### Invertibilità
Ricordando che l'invertibilità si ha solo se $F_{1} \land F_{2}$ è tra le ipotesi, possiamo dimostrare
$$F_{3} \Vdash F_{1} \implies F_{2} \implies F_{3}$$

Infatti se per un mondo $v$ si ha $[[F_{3}]]^{v} = 1$, allora a prescindere da $F_{1}$ e $F_{2}$ il risultato dell'implica sarà sempre 1.

## Referenze