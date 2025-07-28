---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 18:25:36
links:
  - "[[Lecture 09102024132027]]"
  - "[[Lecture 23102024132952]]"
  - "[[Lecture 15112024133341]]"
  - "[[Lecture 20112024140334]]"
  - "[[Lecture 11032025152719]]"
---
# Livello rete
---
## Introduzione
> Il **livello rete** è il terzo dei 7 livelli del [[Modello ISO-OSI|modello ISO-OSI]] e si occupa della **trasmissione dei dati tra due dispositivi in reti diverse**. In particolare, il livello rete si occupa di _indirizzamento, instradamento e [[Commutazione|commutazione]]_, tra dispositivi che possono trovarsi in reti diverse.
> Dal punto di vista di questo livello, le _reti sono organizzate gerarchicamente in reti e sottoreti_.

L'idea è quindi di astrarre la rete locale, gestita già dal [[Livello MAC-LLC|livello MAC-LLC]], e di _trattare la rete come una rete di reti_.

## Caratteristiche
Il livello rete presenta le seguenti caratteristiche:
- _[[Servizio non orientato alla connessione|connectionless]]_ -> non viene stabilita una connessione tra i dispositivi che si scambiano dati
- _best-effort_ -> non viene garantita la consegna dei dati (pacchetti) al destinatario (né l'ordine di arrivo)

## Sottolivelli
Il livello rete è composto da due sottolivelli:
- [[Data plane|data plane]] - determina la porta di uscita su cui inoltrare i datagrammi, guardando la tabella di inoltro (forwarding).
- [[Control plane|control plane]] - popola la tabella di inoltro locale, sulla base delle informazioni passate con i router circostanti, e serve per il routing.

## Protocolli
I protocolli che operano a questo livello sono:
- [[IP]];
- [[Protocollo di routing|protocolli di routing]];
- [[ICMP]];
- [[ARP]] e [[RARP]];
- [[DHCP]];

Il livello rete lavora con i [[Pacchetto|pacchetti]] IP.

## Modelli di servizio
Il livello rete puo' offrire due tipi di servizio:
- [[Internet|internet]]
	- _best-effort_;
	- _nessuna garanzia di banda, perdita, ordine e timing_;
	- _nessun feedback di [[Congestione di rete|congestione]]_ (capito solo dalla perdita);
- [[ATM]] (Asynchronous Transfer Mode)
	- _modello diverso, ha uno stack suo_;
	- _CBR_ (Constant Bit Rate);
	- _modello usato per il voice transfer_.

## Dispositivi
I dispositivi che operano a questo livello sono:
- [[Router|router]]: dispositivo che _instrada i pacchetti tra reti diverse_, in base all'indirizzo IP di destinazione e ai protocolli di routing;

## Referenze