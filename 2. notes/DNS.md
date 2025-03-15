---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 23-02-2025 19:51:35
links:
  - "[[Lecture 29112024132404]]"
  - "[[Lecture 20122024133953]]"
---
# DNS
---
## Introduzione
> Il **DNS** (**Domain Name System**) e' un _servizio che traduce i [[Nome di dominio|nomi di dominio]] in [[Indirizzo IP|indirizzi IP]]_.

<u>Attenzione</u>: non e' necessario per navigare su [[Internet|internet]], e' solo comodo per gli esseri umani.

## Meccanismo
Il DNS e' basato su una catena di server DNS organizzati gerarchicamente: ogni server DNS conosce almeno un DNS di livello superiore, fino ad arrivare al server radice (_root server_, indicato con `.`).
![[dns.png]]

<u>Nota bene</u>: il vantaggio di avere un sistema distribuito, e' di **alleviare il carico di rete** e di garantire **scalabilita'**.

I root server in tutto il mondo sono circa 14, e fungono da smistatori di richieste.
Il meccanismo e' il seguente:
1. _la richiesta iniziale viene solitamente fatta direttamente a un root server_;
2. _sulla base del nome di dominio reindirizza la richiesta al server DNS di livello inferiore di riferimento_ --> **TLD DNS server**, che si risolvono i `.com`, `.org`, `.it`, ecc...;
3. _a sua volta questo ti reindirizza al server DNS di livello inferiore_ (**Authoritative DNS server**);
4. cosi' via, _fino ad arrivare al server DNS che conosce l'associazione con l'indirizzo IP_;

A volte, pero', nelle reti "fatte bene" **la prima richiesta viene fatta a un server DNS locale** (che agisce un po' da [[Proxy|proxy]] DNS!), che poi reindirizza la richiesta a un root server.

### Modalita' di reindirizzamento
Il reindirizzamento gerarchico delle richieste DNS puo' essere:
- **ricorsivo** --> se il server DNS $i$-esimo non riesce a risolvere il nome di dominio, genera lui stesso una richiesta al prossimo server --> vengono appesantiti i DNS di alto livello;
- **iterativo** --> se il server DNS $i$-esimo non riesce a risolvere il nome di dominio, risponde al client (o al DNS locale) con l'indirizzo del prossimo server a cui inviare la richiesta --> viene appesantito il client (o il DNS locale).

### Records
Ogni server DNS contiene dei record DNS
![[dns-records.png]]

## Protocollo
La richiesta e la risposta DNS hanno lo stesso formato:
- **header**, che contiene _identification_ e _flags_;
- **body**, che contiene _questions_, _answer_, _authority_, _additional_.

## Attacchi
E' possibile attaccare il DNS in vari modi:
- _[[DoS]] o [[DDoS]]_, bombardando i root server con del traffico (poco realizzabile) o il TLD server;
- _DNS poisoning_, inviando finte risposte ai DNS server, per sfruttare il loro meccanismo di caching (estremamente dannoso) --> e' il motivo per cui oggi si utilizza il DNS iterativo.

## Referenze