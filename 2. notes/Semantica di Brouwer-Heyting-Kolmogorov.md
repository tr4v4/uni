---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 27-12-2023 17:53:00
links:
  - "[[Lecture 05122023161837]]"
---
# Semantica di Brouwer-Heyting-Kolmogorov
---
## Introduzione
> La **semantica di Brouwer-Heyting-Kolmogorov** è una [[Semantica|semantica]] della [[Logica intuizionista|logica intuizionista]], che prevede che ogni enunciato venga inquadrato come un problema, risolvibile per mezzo di un [[Algoritmo|algoritmo]]. Perciò si ha che _la [[Denotazione|denotazione]] di una formula è l'insieme di tutti gli algoritmi possibili per risolvere il problema_. Da ciò si ha che l'[[Assioma dell'insieme vuoto|insieme vuoto]] è l'_assenza di algoritmi_, e denota la falsità ($\bot$), mentre l'insieme non-vuoto contiene almeno un algoritmo per risolvere il problema, e denota la verità ($\top$).

## Definizione
> Si ha che:
> - $[[A]]^{v} = v(A)$
> - $[[\bot]]^{v} = \varnothing$
> - $[[\top]]^{v} = \{*\}$ (è un problema banale, risolvibile dall'algoritmo $*$)
> - $[[F \land G]]^{v} = [[F]]^{v} \times [[G]]^{v}$
> 	- sarebbe quindi l'insieme delle [[Coppia ordinata|coppie]] di algoritmi per cui il primo risolve $F$ e il secondo $G$ nel mondo $v$
> - $[[F \lor G]]^{v} = [[F]]^{v} \oplus [[G]]^{v}$
> 	- scelgo quale problema risolvere
> - $[[F \implies G]]^{v} = [[G]]^{v^{[[F]]^{v}}}$
> 	- è una funzione che mappa l'algoritmo che risolve $F$ in un altro algoritmo che risolve $G$
> 	- <u>nota bene</u> l'utilizzo dello [[Spazio di funzione|spazio di funzione]] per denotare dominio e codominio della funzione
> 	- è la cosa più diffusa in informatica, quando scriviamo codice 

## Referenze