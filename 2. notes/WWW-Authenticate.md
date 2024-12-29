---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 26-11-2024 18:26:32
links:
---
# WWW-Authenticate
---
## Introduzione
> **WWW-Authenticate** è un [[Header HTTP|header]] [[HTTP]] utilizzato per _richiedere l'[[Autenticazione|autenticazione]] dell'utente_ da parte del server.

## Funzionamento
Quando il client prova ad accedere a una [[Risorsa|risorsa]] protetta, il server risponde con un codice di stato `401` (_Unauthorized_) e un header `WWW-Authenticate` che specifica il metodo di autenticazione richiesto.
Si tratta quindi di un meccanismo del tutto generico, che specifica quale schema di autenticazione è richiesto.

Gli schemi più comuni sono:
- [[Schema basic|basic]]: il client invia le credenziali in chiaro;
- [[Schema digest|digest]]: il client invia un hash delle credenziali;
- [[Schema bearer|Bearer]]: il client invia un token di autenticazione.

## Referenze