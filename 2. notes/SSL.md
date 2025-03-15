---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 13:51:35
links:
  - "[[Lecture 25022025152711]]"
---
# SSL
---
## Introduzione
> L'**SSL** (**Secure Socket Layer**) e' un livello software appartenente al [[Modello ISO-OSI|modello ISO-OSI]] che si colloca tra il [[Livello trasporto|livello trasporto]] e il [[Livello applicazione|livello applicazione]] (come middleware), che _offre meccanismi di cifratura alle applicazioni per poter usare i protocolli [[TCP]]/[[UDP]] in modo [[Sicurezza di rete|sicuro]]_.

![[ssl-architecture.png]]

## Funzionamento
Di base, nel modello _Toy SSL_, avviene che:
1. le informazioni sulle [[Crittografia asimmetrica|chiavi pubbliche]] vengono scambiate durante il [[Three-way handshake|three-way handshake]]; ![[toy-handshake.png]]
2. avviene la _key derivation_, ossia gli attori si scambiano informazioni per ricavare la chiave simmetrica (o il set di chiavi simmetriche);
	- il set si compone di solito di 4 chiavi
		- $K_{c}$
		- $M_{c}$
		- $K_{s}$
		- $M_{s}$
	- che sono derivate usando una [[KDF]] (Key Derivation Function)
3. si trasferiscono i dati; ![[toy-ssl-data-records.png]]
4. si utilizzano messaggi speciali per assicurare la chiusura della connessione;

Per evitare attacchi replay inseriamo un _sequence number_ all'interno di $M_{c}$ (campo MAC). Mentre per evitare che un attaccante faccia il replay di tutti i records inviati, si utilizza il [[Nonce|nonce]]. Per evitare che un attaccante chiuda la connessione prima del necessario, si dividono i messaggi inviabili in tipi diversi (tra cui quello della chiusura della connessione) codificati nella chiave $M_{c}$.

![[toy-ssl-summary.png]]

## Referenze