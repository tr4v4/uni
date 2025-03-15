---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 02-03-2025 19:40:00
links:
  - "[[Lecture 18122024132024]]"
  - "[[Lecture 17022025110943]]"
---
# NAT
---
## Introduzione
All'interno delle [[Classi di rete|classi]] di [[Indirizzo IP|indirizzi IP]] esistono delle reti cosiddette _virtuali_:
- `10.0.0.0`
- `192.168.0.0`

Queste sono **reti assegnate univocamente per reti private**. Cio' che consente a indirizzi privati di comunicare su [[Internet|internet]] (popolato di indirizzi pubblici), sono i [[Router|router]], che tra le altre cose possono fungere da [[Gateway|gateway]].

<u>Attenzione</u>: se un pacchetto destinato alla rete locale privata dovesse uscire per sbaglio dal router dalla rete NAT, esso _teoricamente girerebbe all'infinito in rete_ (perche' non troverebbe mai una destinazione corretta). Nella realta', interviene il campo [[TTL]] del [[Pacchetto|pacchetto]], che arrivato a $0$ lo farebbe cestinare.

> Il _meccanismo di traduzione da indirizzi IP privati a indirizzi IP pubblici_ si chiama **NAT** (**Network Address Translation**).

![[nat-1.png]]

## Funzionamento
Ogni rete privata, per poter comunicare su internet, ha bisogno di un gateway che traduca gli indirizzi privati in indirizzi pubblici. In modo particolare, l'IP della rete privata che vuole comunicare su internet viene tradotto nell'IP pubblico della rete locale (dell'interfaccia del router rivolta verso l'esterno); il router, per poter ricordarsi dell'host che ha fatto la richiesta nella rete locale, deve implementare il NAT.

![[nat-2.png]]

In poche parole, **il NAT permette che un unico indirizzo IP** (pubblico, dell'interfaccia del router visibile all'esterno), **incorpori vari indirizzi IP** (privati, che fanno riferimento all'interfaccia del router locale).

<u>Nota bene</u>: si possono avere _reti NAT nidificate all'interno di altre reti NAT_! Piu' layer di NAT nidificati, piu' layer di mascheramento si avra' per le macchine nella rete locale.

Per poter permettere ad una macchina all'interno di una rete NAT, di essere raggiungibile dall'esterno, e' necessario configurare il [[Port forwarding|port forwarding]]. Il router, inoltre, puo' applicare delle _regole di filtraggio_:
- **deny** --> rifiuta la comunicazione;
- **pass** --> accetta la comunicazione;
- **detour** --> il router prima di inoltrare la richiesta fa degli accertamenti per assicurars che la macchina non sia un eventuale attaccante.

Per poter capire com'e' fatta una rete NAT al suo interno, si esegue un [[Port scanning|port scanning]]: una macchina dall'esterno prova ogni porta del NAT finche' non ha completamente capito come e' fatta l'architettura della rete e quali sono le potenziali debolezze di essa. Per evitare questo fenomeno, il router controlla se una macchina sta controllando tutte le porte in maniera sequenziale. Una volta individuato il comportamento sospetto, il router filtra la macchina in modo che non possa piu' comunicare con la rete (_blacklist_).

## Motivazioni
Il NAT e' diventato un'esigenza dal momento che si e' compreso come gli indirizzi [[IPv4]] sarebbero presto terminati. Infatti, **con NAT si identificano tantissimi dispositivi con un unico IP pubblico**, mitigando il problema della terminazione degli indirizzi IP.

## Limiti
Il NAT presenta comunque dei limiti:
- nonostante gli indirizzi IP delle due classi private siano tantissimi, in realta' **il numero di connessioni TCP istanziabili dal NAT contemporaneamente sono massimo $\approx$ 60.000** --> perche' e' il massimo numero di porte a 16 bit;
- il router si deve occupare di qualcosa del [[Livello trasporto|livello trasporto]], quando dovrebbe arrivare al massimo fino al [[Livello rete|livello rete]];
- il NAT risolve il problema della mancanza degli indirizzi IP, quando dovrebbe farlo l'[[IPv6]];

## Referenze