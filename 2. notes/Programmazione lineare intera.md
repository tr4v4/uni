---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 23-02-2025 15:30:57
links:
  - "[[Lecture 19022025091652]]"
  - "[[Lecture 24022025091339]]"
  - "[[Lecture 26022025091753]]"
---
# Programmazione lineare intera
---
## Introduzione
> Un **problema di programmazione lineare intera** (**PLI**) e' un [[Programmazione lineare|problema di programmazione lineare]] in cui le variabili $x \in \mathbb{Z}^{n}$, ossia _le soluzioni ammissibili sono vettori di numeri interi_.

Solitamente problemi del genere sono piu' complicati dei problemi di programmazione lineare!

## Caratteristiche
Nella programmazione lineare "standard", le _variabili rappresentano delle quantita'_. Nella programmazione lineare intera, invece, le variabili possono essere:
- **quantitative** --> come nella PL normale;
- **logiche** --> _rappresentano valori booleani_.

### Variabili logiche
> Una variabile $x$ si dice **logica** se vale che
> $$x \in \mathbb{N}, 0 \leq x \leq 1$$
> e possono essere utilizzate per modellare:
> - l'_assegnamento di una risorsa ad una task_;
> - il fatto che _una certa attività si debba eseguire oppure no_ (rappresentano un "se").

#### Problema dello zaino
Come modellizziamo il famoso [[Problema dello zaino|problema dello zaino]] in un problema di programmazione lineare intera? Usando le variabili logiche!

Se $E = \{1, \ldots, n\}$ e' l'insieme degli elementi disponibili; $a_{i}$ e' il peso dell'oggetto $i$-esimo; $c_{i}$ e' il costo dell'oggetto $i$-esimo e $b$ e' il peso massimo, allora in teoria il problema dello zaino si puo' modellizzare nel seguente modo:
$$F = \{S ⊆ E : \sum\limits_{i∈S} a_i ≤ b\}$$
$$c(S) = \sum\limits_{i∈S} c_{i}$$

Ma lavorare con i sottoinsiemi e' difficile... Allora introduciamo per ogni oggetto $i$ una variabile logica $x_{i} \in \{0, 1\}$, tale che:
- $x_{i} = 1$ --> l'oggetto $i$-esimo e' preso nel sottoinsieme;
- $x_{i} = 0$ --> l'oggetto $i$-esimo non e' preso nel sottoinsieme.

In questo modo, i vincoli diventano:
- $x_{i} \in \mathbb{Z} \ \ \ \forall i \in \{1, \ldots, n\}$
- $0 \leq x_{i} \leq 1 \ \ \forall i \in \{1, \ldots, n\}$
- $\sum\limits_{i} x_{i} a_{i} \leq b$

La funzione obiettivo, invece, risultera' essere:
$$(\max) \sum\limits_{i} x_{i}c_{i}$$

### Vincoli logici
Oltre alle variabili logiche, un problema puo' presentare dei vincoli espressi in [[Logica proposizionale|logica proposizionale]]. Infatti, attraverso le seguenti equivalenze, si dimostra che **con la programmazione lineare intera siamo in grado di catturare tutte le formule della logica proposizionale**:
- _negazione_: $y = \neg x$ --> $x = 1-y$
- _congiunzione_: $z = x \land y$ --> $z \leq x, z \leq y, z \geq x + y - 1$
- _disgiunzione_: $z = x \lor y$ --> $z \geq x, z \geq y, z \leq x + y$
- _implicazione_: $z = x \implies y$ --> $x+z \geq 1, z \geq y, x+z \leq 1 + y$

Come conseguenza si ha che **ogni problema di programmazione lineare intera su formule di logica proposizionale e' [[NP-Hard]]**[^1]!

Di fatti, _non esistono algoritmi "efficienti" (polinomiali) per risolvere problemi di programmazione lineare intera_.

## Referenze
- [[Vincoli di assegnamento]]
- [[Vincoli di semi-assegnamento]]
- [[Selezione di sottoinsiemi]]
- [[Variabili a valori discreti]]

[^1]: in quanto derivante dal [[SAT]]
