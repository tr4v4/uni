---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 26-11-2024 19:48:18
links:
---
# CORS
---
## Introduzione
> **CORS** (_Cross-Origin Resource Sharing_) è una tecnica [[HTTP]] che permette di _effettuare richieste cross-origin_ utilizzando il [[Metodi HTTP|metodo]] `OPTIONS`.

E' di fatto molto comune che _all'interno di un dominio protetto_, come una [[Sessione|sessione]] [[Autenticazione|autenticata]], _vengano effettuate richieste [[JS|JavaScript]] verso un altro dominio_. Per questioni di sicurezza, **i browser si rifiutano di effettuare queste richieste**, dette _richieste cross-origin_.

CORS è una tecnica che permette di _superare questa limitazione_.
![[CORS.png]]

## Funzionamento
Si attiva solo per connessioni [[AJAX]] (non per connessioni HTTP normali), e prevede l'utilizzo di due nuovi [[Header HTTP|header]]:
- `Origin` (nella [[Richiesta HTTP|richiesta]]): specifica l'origine della richiesta;
- `Access-Control-Allow-Origin` (nella [[Risposta HTTP|risposta]]): per indicare gli altri domini da cui è permesso ricevere risposte.

Di solito si fa un _preflight_, ossia una verifica preliminare tramite richiesta `OPTIONS` per verificare se il server accetta un comando cross-scripting.

### Sessione
Supponiamo che `www.dominio1.com` voglia fare una richiesta ad `www.dominio2.com`:
1. `www.dominio1.com` fa una richiesta `OPTIONS` ad `www.dominio2.com`, specificando il proprio dominio nell'header `Origin`;
2. `www.dominio2.com` risponde con l'header `Access-Control-Allow-Origin`, specificando i domini da cui accetta richieste, e se tra questi rientra `www.dominio1.com` risponde con `200 OK`;

<u>Nota bene</u>: una eventuale risposta `Access-Control-Allow-Origin` con valore `*` indica che _il server accetta richieste da qualsiasi dominio_.

## Referenze