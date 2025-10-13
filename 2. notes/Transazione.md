---
tags:
  - category/note
  - status/finished
  - topic/basi-di-dati
date: 25-09-2025 22:17:45
links:
  - "[[Lecture 25092025151622]]"
  - "[[Lecture 26092025151541]]"
---
# Transazione
---
## Introduzione
> Una **transazione** in un [[Database|database]] è un _insieme non decomponibile/distaccabile di operazioni che devono essere eseguite atomicamente in un sistema concorrente_[^1].

Se implementate bene, ovviamente, risolvono le [[Race condition|race condition]] che si potrebbero verificare su accessi concorrenti al database.

Per esempio la _prenotazione contemporanea da parte di 2 persone su uno stesso posto su un treno deve essere gestita in modo da non generare 2 biglietti uguali_.

Inoltre, l'effetto delle transazioni dev'essere permanente: il _risultato finale dev'essere loggato e tracciato_ (anche se contiene un errore). Quest'operazione si chiama **commit**.

## Referenze

[^1]: letteralmente un'[[Azione atomica|azione atomica]]
