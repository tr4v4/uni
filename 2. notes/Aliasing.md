---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-02-2025 10:23:13
links:
  - "[[Lecture 20022025131602]]"
---
# Aliasing
---
## Introduzione
> Si parla di **aliasing** nel contesto dei [[Linguaggio di programmazione|linguaggi di programmazione]] quando _[[Nome|nomi]] diversi denotano lo stesso [[Oggetto denotabile|oggetto]]_.

Solitamente si realizza tramite [[Puntatore|puntatori]], ed e' da evitare per le seguenti ragioni:
- la _modifica di una variabile cambia automaticamente il valore a tutte le altre in aliasing_;
- se una variabile `X` viene liberata (`free(X)`), questa diventa `nil`, ma _un'altra variabile in aliasing `Y` continuera' a puntare alla zona di memoria liberata_, diventanto un **[[Dangling pointer|dangling pointer]]** (con gravi ripercussioni sulla sicurezza).

## Referenze