---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 30-03-2025 21:55:13
links:
  - "[[Lecture 10032025112014]]"
---
# Firewall
---
## Introduzione
> Un **firewall** e' una macchina (che puo' essere integrata nei [[Router|router]]), che implementa delle politiche di sicurezza per bloccare/filtrare certi [[Pacchetto|pacchetti]] provenienti dall'esterno, al fine di proteggere la [[Rete|rete]] [[LAN|locale]].

Serve per:
- _prevenire attacchi [[DoS]]_;
- _prevenire l'accesso illegale_ a dati interni;
- gestire l'_accesso autorizzato_ alla rete.

<u>Nota bene</u>: ci possono essere piu' firewall, strutturati talvolta ad albero.

## Tipologie
Esistono tre tipologie di firewall:
1. **stateless packet filters** - il filtraggio avviene pacchetto per pacchetto, senza salvare lo stato; si basano su:
	- _source/destination [[IP]] address_;
	- _[[TCP]]/[[UDP]] source/destination address_;
	- _[[ICMP]]_;
	- _TCP SYN e ACK bits_.
2. **stateful packet filters** - mantiene lo stato di ogni connessione TCP, e quindi ha necessita' di memorizzare un campo in piu' rispetto ai firewall stateless, relativo allo stato della connessione.
3. **application gateways** - sono delle macchine che fungono da tramite per far connettere un host interno ad un host esterno:
	- fondamentalmente in reti locali cosi' attrezzate i client si connettono direttamente a degli host esterni, ma passano obbligatoriamente dall'application gateway, che una volta verificate certe condizioni inoltra la richiesta di connessione;
	- questo puo' essere utile per concentrare il traffico in uscita verso un primo "smaltitore", appunto l'application gateway, e per evitare che la connessione verso l'esterno arrivi da un host non autorizzato;
	- ![[application-gateway.png]]

Ad ogni modo, per definire le regole di firewalling si utilizzano le [[ACL]].

## Problemi
L'idea di base e' che il firewall si fida degli interni, e non degli esterni. Di conseguenza _il punto debole del sistema potrebbe essere un attore malintenzionato interno alla rete_.

In particolare, se un utente esterno riesce ad ottenere l'accesso ad un utente interno, potrebbe riuscire a bypassare il firewall.

Inoltre presentano dei limiti:
- la mancanza di un modo per identificare l'_IP spoofing_;
- nel caso di application gateway, la necessita' di un ulteriore passaggio per la connessione e il fatto che il client debba sapere come connettersi all'application gateway (per esempio impostando un [[Proxy|proxy]] nel browser).

Per rimediare a queste mancanze, si possono utilizzare gli [[IDS]].

## Referenze