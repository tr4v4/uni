---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 25-11-2024 13:19:58
links:
---
# Autenticazione
---
## Introduzione
> L'**autenticazione** è il processo tramite il quale un sistema verifica l'identità di un utente.

<u>Attenzione</u>: l'_autenticazione non è da confondere con l'[[Autorizzazione|autorizzazione]]_, che è _il processo tramite il quale un sistema verifica i permessi di un utente_.

## Web
Nel contesto del [[Web|web]], l'_autenticazione può avvenire tramite [[Cookie|cookie]]_. In particolare, questi possono essere utilizzati per _memorizzare le informazioni di login dell'utente_, per evitare di doverle reinserire ad ogni accesso.

Gli approcci più comuni per l'autenticazione web sono:
- _[[Autenticazione session-based|session-based]]_ - il server mantiene un ID di sessione, e informazioni sull'utente verificate ad ogni richiesta;
- _[[Autenticazione token-based|token-based]]_ - il client mantiene un token rilasciato dal server, che spedisce ad ogni richiesta per la verifica.

## Referenze