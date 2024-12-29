---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 26-11-2024 18:43:35
links:
---
# Schema bearer
---
## Introduzione
> Lo **schema bearer** è uno degli [[WWW-Authenticate|schemi di autenticazione]] [[HTTP]] più comuni. Si tratta di un metodo _sicuro e flessibile_, che _richiede al client di inviare un token di autenticazione_.

E' di fatto un meccanismo di [[Autenticazione token-based|autenticazione token-based]].

## Funzionamento
Il server produce un _token di autenticazione_, che viene inviato al client. Questo token viene poi inviato dal client ad ogni richiesta, tramite l'header `Authorization`, ed è _sufficiente per l'autenticazione_.

## Referenze