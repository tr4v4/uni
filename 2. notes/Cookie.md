---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 25-11-2024 11:50:21
links:
---
# Cookie
---
## Introduzione
> Un **cookie** è un'_informazione scambiata tra il server e il client, salvata nel browser del client, riguardo le connessioni precedenti_. Il client manda al server i cookie salvati ogni volta che richiede una risorsa, per consentire al server di avere informazioni relative al contesto.
> E' un meccanismo necessario nell'[[HTTP]] in quanto quest'ultimo è _stateless_, cioè non mantiene informazioni tra una connessione e la successiva.

![[cookies.png]]

Utilizzano quindi di fatto 2 [[Header HTTP|header]]:
- **Set-Cookie**: nella [[Risposta HTTP|risposta]] del server per inviare un cookie al client;
- **Cookie**: nella [[Richiesta HTTP|richiesta]] del client per inviare un cookie al server.

## Struttura
Un cookie è composto da:
- _Nome_: il nome del cookie;
- _Valore_: il valore del cookie;
- _Domain_: il dominio in cui il cookie è valido (es. nomesito.com);
- _Path_: il percorso in cui il cookie è valido all'interno del sito;
- _Max-Age/Expire_: la data di scadenza del cookie (durata in secondi del cookie);
- _Secure_: il cookie è valido solo su connessioni sicure ([[HTTPS]]);
- _Version_: la versione del cookie.

## Tipologia
Esistono diversi tipi di cookie:
- _cookie persistenti_: generalmente senza scadenza, vengono salvati nel browser e utilizzati per informazioni di login e preferenze utente;
- _cookie di sessione_: cookie relativi alle sessioni, con un ID sessione;
- _cookie di terze parti_: cookie utilizzati per lo scambio di informazioni tra siti, ad esempio per gli annunci personalizzati.

## Applicazioni
I campi di applicazione dei cookie sono:
- [[Autenticazione|autenticazione]];

## Referenze