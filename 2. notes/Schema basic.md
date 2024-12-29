---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 26-11-2024 18:31:30
links:
---
# Schema basic
---
## Introduzione
> Lo **schema basic** è uno degli [[WWW-Authenticate|schemi di autenticazione]] [[HTTP]] più comuni. Si tratta di un metodo _semplice e poco sicuro_, che _richiede al client di inviare le credenziali in chiaro_.

## Funzionamento
Il server specifica il contesto di sicurezza al client, detto _realm_, nel momento dell'invio dell'[[Header HTTP|header]] `WWW-Authenticate`. Il client invia le credenziali in chiaro, codificate in [[Base64|base64]], tramite l'header `Authorization`.

## Limitazioni
Lo schema basic è ormai in disuso per i seguenti motivi:
- _la password è inviata in chiaro_;
- _non supporta il logout_ (chiusura della sessione);
- _il form di autenticazione non è personalizzato e integrato nell'applicazione, ma è un popup del browser_.

## Referenze