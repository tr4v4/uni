---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 14-10-2024 20:23:08
links:
  - "[[Lecture 08102024111650]]"
---
# DFA
---
## Introduzione
> Un **DFA** (_Automa a stati Finiti Deterministico_) è un [[Automa a stati finiti|automa a stati finiti]] definita da una quintupla
> $$(\Sigma, Q, \delta, q_{0}, F)$$
> dove:
> - $\Sigma$ è un _alfabeto finito di simboli in input_
> - $Q$ è un _insieme finito di stati_
> - $q_{0} \in Q$ è lo _stato iniziale_
> - $F \subseteq Q$ è l'_insieme degli stati finali_
> - $\delta$ è la _funzione di transizione_ del tipo $$\delta: Q \times \Sigma \to Q$$

## Caratteristiche
Si nota come l'unica differenza formale tra i DFA e gli [[NFA]] sta nella funzione di transizione $\delta$. Questa è tuttavia ciò che serve per caratterizzare il determinismo dei DFA rispetto al nondeterminismo degli NFA:
- $\forall q \in Q \ \ \ \delta(q, \epsilon) = \varnothing$, ovvero **non esistono le transizioni-$\epsilon$**;
- $\forall \sigma \in \Sigma, \forall q \in Q, \exists q'\in Q. \ \ \ \delta(q, \sigma) = \{q'\}$, ossia **ad ogni coppia (stato, carattere) è associato come output il [[Assioma del singoletto|singoletto]] di uno stato**.

Come conseguenza di queste proprietà, si ha che:
- nei DFA è _garantita una scansione completa dell'input_, infatti l'output di $\delta$ è $\in Q$;
- sappiamo se _$w \in L[D]$ in un tempo $O(|w|)$_, quindi lineare rispetto alla lunghezza della stringa;
- è _più difficile da definire di un NFA_.

E' anche importante notare che i DFA sono un [[Definizione di essere sottoinsieme|sottoinsieme]] degli NFA.
![[dfa-in-nfa.png]]

## Proposizioni
### NFA $\to$ DFA
> _Per ogni NFA è possibile costruire un DFA equivalente_.

Questa proposizione si dimostra con un algoritmo[^1] che consente di passare, effettivamente, da un qualunque NFA a un DFA: [[Costruzione per sottoinsiemi|costruzione per sottoinsiemi]].

## Referenze
[^1]: come una dimostrazione di [[Logica intuizionista|logica intuizionista]]!