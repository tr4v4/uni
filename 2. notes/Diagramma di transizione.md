---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 14-10-2024 10:53:28
links:
  - "[[Lecture 03102024120247]]"
  - "[[Lecture 18102024090854]]"
---
# Diagramma di transizione
---
## Introduzione
> Un **diagramma di transizione** è un _diagramma_ a [[Grafo|grafo]] usato per descrivere in modo conciso il comportamento di un [[Automa|automa]] ([[Automa a stati finiti|a stati finiti]] o [[Automa a pila|a pila]]).

E' fondamentale capire che **da un diagramma di transizione è facile comprendere il [[Linguaggio formale|linguaggio]] riconosciuto dall'automa associato**.

## A stati finiti
I nodi rappresentano gli stati dell'automa, in cui vanno specificati:
- $q_{0}$, lo _stato/nodo iniziale_;
- $q_{l, m, n, \cdots}$, gli _stati/nodi finali_.

Gli archi sono i caratteri dell'alfabeto $A$ lette in input dalla testina: rappresentano le transizioni da uno stato all'altro alla lettura di un certo carattere.

### Esempi
Dal diagramma di transizione
![[diagramma-di-transizione-1.png]]
si capisce facilmente che il linguaggio riconosciuto dall'automa associato è
$$L = \{a^{2n+1} | n \geq 0\} = \{a^{n} | n \text{ è dispari}\} = \mathscr{L}[a(aa)^{*}]$$

<u>Nota bene</u>: _non è un caso che il linguaggio riconosciuto sia [[Linguaggio regolare|regolare]]_, [[Linguaggio denotato da un'espressione regolare|denotato]] quindi da un'[[Espressione regolare|espressione regolare]].

Da quest'altro diagramma di transizione
![[diagramma-di-transizione-2.png]]
si sta descrivendo l'automa che riconosce tutte le stringe denotato dall'espressione regolare
$$[0-9]^{+}(\epsilon|.[0-9]^{+})$$

## A pila
![[diagramma-di-transizione-npda.png]]

E' stato necessario **aggiungere per ogni arco al carattere letto anche il carattere top della pila e la sua sostituzione**.

## Referenze