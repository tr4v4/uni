---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 26-11-2024 18:45:58
links:
---
# Autenticazione session-based
---
## Introduzione
> L'**autenticazione session-based** è un metodo di [[Autenticazione|autenticazione]] [[HTTP]] che _si basa su una [[Sessione|sessione]] utente mantenuta dal server_.

## Funzionamento
Dopo aver verificato l'identità dell'utente, attraverso uno [[WWW-Authenticate|schema di autenticazione]], il server:
1. genera una sessione a cui associa un ID univoco e le informazioni relative all'utente;
2. invia al client un [[Cookie|cookie]] contenente l'ID di sessione;

Nelle successive richieste, il _client invia il cookie di autenticazione, contenente l'ID di sessione e altre informazioni per autenticarsi_. Il _server verifica queste informazioni, e anche la loro validità temporale_ (le sessioni scadono), _e autorizza o meno l'accesso alla [[Risorsa|risorsa]]_.
![[autenticazione-session-based.png]]

### Cookie di sessione
Sono appunto i cookie che contengono le informazioni relative alla sessione utente. Questi cookie sono _temporanei_ e _vengono cancellati dal client alla chiusura del browser_. Il server, oltre a memorizzarli per l'autenticazione dei client, si occupa di gestire la loro scadenza (_expire_).

Tutti i [[Linguaggio di programmazione|linguaggi di programmazione]] _server-side_ hanno una gestione automatica dei cookie di sessione.

## Referenze