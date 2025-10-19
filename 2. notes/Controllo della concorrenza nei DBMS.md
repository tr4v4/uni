---
tags:
  - category/note
  - status/pending
  - topic/basi-di-dati
date: 19-10-2025 20:41:19
links:
  - "[[Lecture 16102025151651]]"
---
# Controllo della concorrenza nei DBMS
---
## Introduzione
Anche se le [[Transazione|transazioni]] di un [[DBMS]] appunto sono eseguite in "isolamento", _nella realtà non sono eseguite in sequenza_! Si cerca di parallelizzare il più possibile tali transazioni, ma per farlo nella maniera più corretta sono necessari dei meccanismi di controllo delle concorrenze.

In particolare, si vuole assicurere che:
> L'**ordine di esecuzione delle transazioni sia scelto in modo tale che l'effetto sia lo stesso del caso di esecuzione sequenziale** (una alla volta).

Questa proprietà si può ottenere usando un meccanismo di **lock**: _quando due query accedono alla stessa tabella, viene creato un lucchetto che fa passare una transizione alla volta_. Tuttavia, questo può portare addirittura a casi di [[Deadlock|deadlock]]!

Questo avviene per esempio quando due transazioni hanno stanno lavorando sulle proprie tabelle, lockandole, e tentano di accedere alle corrispettive tabelle:
![[Drawing 2025-10-19 17.21.48.excalidraw|800]]

In tal caso, il manager delle transazioni ha il compito d intervenire e fare il **rollback** o l'**abort** di una o piu' transazioni per sbloccare il deadlock, consentendo alle altre di procedere.

## Approcci
Ci sono 3 approcci:
- **restrictive** - guarda [[Schedule di un DBMS#Schedule serializzabile|schedule serializzabili]] che evitano i conflitti attraverso _protocolli di data-locking_;
- **optimistic** - esegue tutte le transazioni in concorrenza, _controllando la presenza di conflitti prima di committare_;
- **timestamping** - assegna dei timestamps alle transazioni che hanno scritto o letto degli oggetti del [[Database|database]] e confronta questi valori per determinare l'ordine delle operazioni nello scheduling.

### Restrictive
Ci si vuole fondamentalmente assicurare l'assenza di qualunque conflitto (dato da scheduling non serializzabile!) e di fare rollback di transazioni abortite.

La tecnica principe si chiama [[Strict 2PL]].

## Referenze