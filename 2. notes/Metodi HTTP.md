---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 12-11-2024 20:33:09
links:
  - "[[Lecture 10102024151443]]"
---
# Metodi HTTP
---
## Introduzione
> I **metodi HTTP** indicano di una [[Richiesta HTTP|richiesta]] [[HTTP]] l'azione che richiede il client al server, la sua intenzione.

## Proprietà
Le proprietà dei metodi sono in particolare:
- _sicurezza_ (intesa come "safety"[^1]) --> non genera cambiamenti sullo stato del server;
- _idempotenza_ --> l'effetto sul server di più richieste identiche è lo stesso di quello di una sola richiesta;

<u>Nota bene</u>: un metodo "safe" può essere eseguito da un nodo intermedio (come un [[Proxy|proxy server]] per il [[HTTP caching|caching]]) senza effetti negativi.

## Metodi
Sono:
- `GET` - per la ricezione dei dati, sicuro e idempotente
- `HEAD` - simile al GET ma senza ricevuta del body, sicuro e idempotente
- `POST` - per la spedizione dei dati, né sicuro né idempotente
- `PUT` - per la modifica dei dati, non sicuro ma idempotente
- `DELETE` - per la cancellazione dei dati, non sicuro ma idempotente
- `PATCH` - per aggiornare parzialmente una risorsa
- `OPTIONS`- per ricevere solo gli header

## Referenze
[^1]: esattamente come le [[Proprietà safety|proprietà safety]]