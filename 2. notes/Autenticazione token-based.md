---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 26-11-2024 19:27:24
links:
---
# Autenticazione token-based
---
## Introduzione
> L'**autenticazione token-based** è un metodo di [[Autenticazione|autenticazione]] [[HTTP]] che _richiede al client di inviare un token di autenticazione_ al server.

## Funzionamento
Dopo l'autenticazione dell'utente, il server rilascia al client un _token di autenticazione_, formato con la propria chiave. Il client lo memorizza e _lo invia tramite [[Schema bearer|schema bearer]]_ nel campo `Authorization` dell'[[Header HTTP|header HTTP]] per tutte le successive richieste. Il server verifica la propria firma sul token e le informazioni sull'utente: se valide restituisce la [[Risorsa|risorsa]].

## Vantaggi
Si tratta di un approccio più scalabile rispetto all'[[Autenticazione session-based|autenticazione basata su sessione]], in quanto _non richiede la memorizzazione di informazioni lato server_.

## Applicazioni
Meccanismi di autenticazione token-based comuni sono:
- [[JWT]]

## Referenze