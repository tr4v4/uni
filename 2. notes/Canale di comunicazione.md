---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 08-10-2024 19:07:53
links:
  - "[[Lecture 25092024132223]]"
---
# Canale di comunicazione
---
## Introduzione
> Il **canale di comunicazione** è una _virtualizzazione di un [[Mezzo di trasmissione|mezzo trasmissivo]]_ governabile via software. E' garantito dall'esistenza dei filtri passa-banda installati sulle [[Scheda di rete|schede di rete]].

Su _un unico mezzo trasmissivo possono avvenire più comunicazioni nello stesso spazio tempo_, senza collisioni né distorsioni del segnale: _queste singole comunicazioni sono detti canali di comunicazione_.

Per esempio una volta connessi a una [[Rete|rete]] Wi-Fi, i nostri dispositivi sentono solamente la frequenza di quella rete, isolandosi dalle altre.

## Tipologie
Di canali di comunicazioni ne esistono due paradigmi:
- **punto a punto**;
- **ad accesso multiplo** (broadcast);

### Punto a punto
Viene creato un canale apposito per la comunicazione tra due dispositivi della rete. E' poco interessante.

Questo è l'effettivo _metodo utilizzato nelle reti telefoniche_: quando si chiama qualcuno viene assegnato un canale punto a punto (una frequenza specifica) tra i due interlocutori.

Ma nella **rete internet, creare un canale punto a punto per ogni comunicazione tra due host, sarebbe impraticabile**.

### Ad accesso multiplo
Questo è il metodo di utilizzo corrente dei canali di comunicazione, ossia si utilizza su uno stesso mezzo trasmissivo _un unico canale di comunicazione condiviso tra tutti i dispositivi_.

Si ripresenta così il problema delle collisioni: infatti se due dispositivi parlano sullo stesso canale condiviso (stessa frequenza) contemporaneamente, allora avviene una collisione. In più bisogna gestire l'indirizzamento dei segnali in modo da poter specificare la comunicazione:
- con un gruppo di host - _multicast_
- con tutti gli host - _broadcast_

Il primo problema si risolve con il protocollo [[Ethernet|ethernet]], mentre il secondo con l'indirizzo [[MAC]].

## Referenze