---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 14-10-2024 11:11:12
links:
  - "[[Lecture 03102024120247]]"
  - "[[Lecture 08102024111650]]"
---
# NFA
---
## Introduzione
> Un **NFA** (_Automa a stati Finiti Nondeterministico_) è un [[Automa a stati finiti|automa a stati finiti]] definito da una quintupla
> $$(\Sigma, Q, \delta, q_{0}, F)$$
> dove:
> - $\Sigma$ è un _alfabeto finito di simboli in input_
> - $Q$ è un _insieme finito di stati_
> - $q_{0} \in Q$ è lo _stato iniziale_
> - $F \subseteq Q$ è l'_insieme degli stati finali_
> - $\delta$ è la _funzione di transizione_ del tipo $$\delta: Q \times (\Sigma \cup \{\epsilon\}) \to \mathscr{P}(Q)$$

## Caratteristiche
E' fondamentale capire la funzione di transizione $\delta$, perché è ciò che contraddistingue gli NFA dai [[DFA]]. $\delta$ infatti prende in input una coppia composta da uno stato $\in Q$ e un carattere $\in \Sigma \cup \{\epsilon\}$, ovvero un carattere dell'alfabeto o la stringa nulla; in output fornisce invece un [[Definizione di essere sottoinsieme|sottoinsieme]][^1] degli stati.
Questo perché, in quanto automa non deterministico:
- devono esistere le **transizioni-$\epsilon$**, ossia _dev'essere possibile per l'automa spostarsi di stato senza leggere un carattere_;
- devono esistere **più stati in cui andare per una stessa coppia (stato corrente, carattere in input)**.

Come conseguenze delle loro proprietà, gli automi finiti nondeterministici sono:
- _comodi_ --> facili da costruire;
- _inefficienti_ --> accettare $w$ significa cercare un [[Cammino|cammino]] su un [[Grafo|grafo]] nondeterministico, ossia con tante potenziali strade alternative da provare, con conseguente _necessità di fare backtracking_.

[^2]

### Esempi
L'automa descritto dal suo diagramma di transizione
![[nfa-1.png]]
_non è deterministico_. Infatti
$$\delta(q_{0}, b) = \{q_{0}, q_{1}\}$$
per cui è possibile prendere due strade differenti per una singola coppia (stato, input). Ad ogni modo, il linguaggio accettato dall'automa è quello [[Linguaggio denotato da un'espressione regolare|denotato]] dall'[[Espressione regolare|espressione regolare]] $\mathscr{L}[(a|b)^{*}ba]$.

Anche l'automa
![[nfa-2.png]]
è nondeterministico. Infatti c'è la transizione-$\epsilon$, che consente all'automa di spostarsi da $q_{0}$ a $q_{1}$ senza leggere alcun carattere in input. Il linguaggio accettato in questo caso è $\mathscr{L}[a^{*}b^{*}]$.

E' possibile deterministicizzare quest'ultimo automa con
![[nfa-deterministicizzato.png]]
che accetta lo stesso linguaggio. E' importante notare lo $q_{2}$, chiamato **stato pozzo**, che consiste in uno stato di errore dell'automa: _può leggere all'infinito $a$ o $b$ senza mai terminare in uno stato finale_.

## Rappresentazione
Solitamente, la funzione di transizione viene rappresentata tramite una tabella di transizione:
![[tabella-di-transizione-1.png]]

A sua volta, dalla tabella è facile ottenere il [[Diagramma di transizione|diagramma di transizione]], che riassume l'intero automa:
![[diagramma-di-transizione-3.png]]

## Referenze
- [[Linguaggio accettato]]
- [[Equivalenza tra NFA ed espressioni regolari]]

[^1]: perché è l'[[Assioma dell'insieme potenza|insieme delle parti]] di $Q$
[^2]: sulla falsa riga della [[Sintassi astratta|sintassi astratta]], che è facile da costruire ma [[Grammatica ambigua|ambigua]]