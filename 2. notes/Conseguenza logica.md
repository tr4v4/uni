---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 08-11-2023 23:02:07
links:
  - "[[Lecture 08112023131119]]"
  - "[[Lecture 09112023131356]]"
---
# Conseguenza logica
---
## Introduzione
> $\Gamma \Vdash F$, ovvero **$F$ è conseguenza logica di $\Gamma$**, quando per ogni [[Mondo|mondo]] $v$ si ha che, se $[[G]]^{v} = 1$ per ogni $G \in \Gamma$, allora $[[F]]^{v} = 1$.

Equivalentemente possiamo dire:
- $\min\{[[G]]^{v} | G \in \Gamma\} \leq [[F]]^{v}$
- $F$ vale in tutti quei mondi in cui tutte le formule di $\Gamma$ valgono
- supponendo di essere in un mondo in cui valgono tutte le formule di $\Gamma$, in quel mondo vale $F$
- l'insieme dei mondi in cui tutte le formule di $\Gamma$ valgono è un [[Definizione di essere sottoinsieme|sottoinsieme]] di quello in cui vale $F$
	- $\bigcap_{G \in \Gamma} \{v | [[G]]^{v} = 1\} \subseteq \{v | [[F]]^{v} = 1\}$

### Osservazioni
Dobbiamo pensare alle formule di $\Gamma$ come a dei **filtri** sull'insieme di tutti i mondi: _più formule in $\Gamma$ ci sono, più filtri abbiamo, meno mondi teniamo, e quindi è più facile che l'intersezione di tutti i mondi in cui valgono le formule di $\Gamma$ sia un sottoinsieme dei mondi in cui vale $F$_.

## Inconsistenza
$\Gamma$ si dice **inconsistente** se non ci sono mondi per cui valgono (sono a 1) tutte le formule di $\Gamma$, ovvero se l'intersezione di tutti i mondi di in cui valgono le formule di $\Gamma$ è l'[[Assioma dell'insieme vuoto|insieme vuoto]] $\varnothing$. Se si raggiunge l'inconsistenza delle ipotesi, allora la conseguenza logica è qualunque $F$, anche l'**assurdo** $\bot$.
Ovvero:
$$\Gamma \Vdash \bot$$

che ci spiega da dove derivino la [[Regole di inferenza del BOTTOM|regole di inferenza del bottom]]: **dall'assurdo si può dimostrare qualunque cosa**.

## Conseguenze
La conseguenza logica giustifica la [[Derivabilità di una regola di inferenza|derivabilità]] e il _ragionamento ipotetico_: è a tutti gli effetti ciò che studia la logica. Inoltre _non c'entra niente con il mondo delle dimostrazioni_ (es. [[Deduzione naturale|deduzione naturale]]), perché è proprio una [[Semantica|relazione semantica]]. Le dimostrazioni, d'altro canto, sono invece [[Sintassi|oggetti sintattici]], che ci garantiscono la conseguenza logica e ci forniscono una spiegazione del perché essa vale: **la conseguenza logica di per sé non ci dice nulla sulla relazione tra $\Gamma$ e $F$.**

La conseguenza logica, infine, è ciò che definisce:
- [[Teorema di correttezza]]
- [[Teorema di completezza]]

## Referenze