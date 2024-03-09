---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
  - topic/programmazione
  - topic/analisi-I
date: 21-11-2023 20:43:48
links:
  - "[[Lecture 16112023092027]]"
---
# Binder
---
## Introduzione
> Un **binder** costituisce un'[[Sintassi|area sintattica]] all'interno della quale _una certa variabile è legata allo scope_. I binder si ritrovano in matematica, in informatica, e quindi anche in logica.

Una variabile legata a uno scope da un binder si dice **variabile legata**; una variabile apparentemente non legata da alcun binder si dice invece **[[Variabile libera|variabile libera]]**.

### Esempi
In programmazione un esempio di binder è la variabile `i` di un [[Comandi iterativi|ciclo]] `for`: essa itera nel corpo del ciclo modificando il suo valore, ed _è valida solo e solamente all'interno di quello scope_. Di fatto, lo [[Scope|scope delle variabili]] è ciò che fa il binding di esse con il proprio blocco di appartenenza. Vale infatti anche per le [[Funzione informatica|funzioni]] in generale.

In matematica un'[[Integrale|integrale]] definito lega $x$ al suo scope, che è la _funzione integranda_.

## Problemi
Sintatticamente i binder provocano un problema comune: lo **[[Shadowing|shadowing]]**. Questo avviene quando una variabile $x$ legata da un binder a uno scope non è più raggiungibile da sotto-binder che usano una stessa variabile $x$. Per esempio
$$\forall x. (P(x) \land \exists x. (Q(x)))$$
in questo caso, la variabile $x$ è prima legata dal [[Quantificatori|quantificatore]] $\forall$ al di fuori della parentesi. Di fatto la $x$ di $P(x)$ si riferisce a l'$x$ di $\forall$. Ma con $\exists x$ si sta generando un altro scope in cui la $x$ di $\forall$ viene persa! Infatti la $x$ di $Q(x)$ si riferisce a quella del quantificatore $\exists$, e **non c'è alcun modo di farla riferire al binder definito in precedenza** ($\forall x$).

### Soluzione
> Per risolvere lo shadowing è necessario, essendo a conoscenza del [[Diagramma di legame|diagramma di legame]] dell'espressione, _modificare il nome delle variabili sfruttando l'[[Alpha-convertibilità|alpha-convertibilità]]_ mediante l'operazione di [[Sostituzione|sostituzione]].

## Referenze