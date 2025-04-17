---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 30-03-2025 23:10:25
links:
  - "[[Lecture 11032025152719]]"
---
# Network scheduling
---
## Introduzione
> Il **network scheduling** e' una serie di [[Algoritmo|algoritmi]] di [[Scheduling|scheduling]] che _determinano le politiche di scelta dei pacchetti in attesa (sia in input che in output) nei [[Router|router]]_.

Chiaramente, **lo scheduling ha senso se si assume che i pacchetti non abbiano la stessa importanza**.

## Funzionamento
In caso di buffer pieni, per esempio la coda di input del router, si possono avere i seguenti 3 comportamenti:
- _tail drop_ - viene droppato il pacchetto appena arrivato (classico);
- _priority_ - viene droppato il pacchetto con priorità più bassa per fare spazio al pacchetto in arrivo se ha priorità maggiore;
- _random_ - inutile, ma l'unico che implementa realmente la faireness.

### Priority
In teoria, la scelta migliore sarebbe quella di droppare il pacchetto con priorita' minore (priority scheduling), ma nella realta' non si usano router del genere, infatti il campo _TOS_ non viene proprio considerato: _[[Internet|internet]] non prevede reali politiche di priorita'_, a differenza di [[Internet2|internet2]], che di fatto pero' non e' lo standard.

Ma nel caso in cui si voglia implementare una politica di priorita' nello scheduling dei router, allora si gestisce su 2 livelli di priorita', mediante 2 code:
1. si va a vedere il campo _TOS_ nei pacchetti che indica la loro priorita', e si inserisce il pacchetto nella coda "rossa" o "verde" a seconda di quel valore;
2. poi il router guarda se la coda "rossa" non e' vuota, e se cosi' e' prende il pacchetto da li'; altrimenti lo prende dalla coda "verde".

#### Altre politiche
Ci sono anche altre politiche prioritarie:
- [[Round-Robin]] - si prende un pacchetto da una coda, poi da un'altra, e cosi' via, ciclicamente;
- [[Weighted Fair Queuing]] (generalizza il round-robin) - si da' un peso a ciascuna coda, ad ogni ciclo si prende un pacchetto da una coda in base al peso assegnato.

## Referenze