---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 20:09:41
links:
  - "[[Lecture 06112024132717]]"
  - "[[Lecture 08112024132550]]"
  - "[[Lecture 13112024133033]]"
---
# Subnet mask
---
## Introduzione
> La **subnet mask** è un _indirizzo di 32 bit che viene utilizzato per dividere una [[Rete|rete]] in sottoreti_. In particolare viene utilizzata per _definire la parte di rete e la parte di host_ di un [[Indirizzo IP|indirizzo IP]].

## Struttura
La rappresentazione è sempre in **notazione decimale puntata**, come l'[[IPv4]], ma dev'essere composta da _una sequenza di 1 seguita da una di 0_. Non possono esserci 0 tra i 1 e viceversa.

Con essa, a partire da una rete definita da un indirizzo IP, _si possono creare delle sottoreti_. In particolare, la subnet mask definisce _quanti bit sono dedicati alla parte di rete e quanti alla parte di host_:
- i bit dedicati alla parte di rete sono quelli che sono a 1 nella subnet mask;
- i bit dedicati alla parte di host sono quelli che sono a 0 nella subnet mask.

Attraverso la subnet mask possono fare:
- [[Subnetting|subnetting]] - rubo dei bit dalla parte di host per ottenere sottoreti; per esempio se rubo 1 bit alla parte di host, avrò 2 sottoreti; se rubo 2 bit, ne avrò 4, e così via;
- [[Supernetting|supernetting]] - accorpo più reti in un'unica rete più grande, rubando bit dalla parte di rete.

### CIDR
Il **CIDR** (_Classless Inter Domain Routing_) è una notazione che usa `/n` per indicare affianco a un indirizzo IP la sua subnet mask, dove `n` è il numero di bit a 1 della subnet. Questo permette di specificare in modo più chiaro e veloce la subnet mask associata a un indirizzo IP.

## Funzionamento
Una volta definite le reti e sottoreti, bisogna definire per ognuna di esse:
- _indirizzo di broadcast_: bit degli host tutti a 1;
- _indirizzo di rete_: bit degli host tutti a 0;
- _indirizzo del router_: indirizzo del broadcast -1.

Ogni sottorete (e rete) deve avere un router rappresentante, detto **default router**. Questo router è l'unico che può comunicare con le altre reti.

**Sia al router che agli host di una rete bisogna specificare sia il loro indirizzo IP che la subnet mask**. In questo modo sono a conoscenza della rete/sottorete in cui si trovano.

<u>Nota bene</u>: _con la sola maschera di rete si può solo sapere quanti host si possono indirizzare_; è con l'associazione all'indirizzo IP che si possono ottenere tutte le informazioni su rete e sottorete.

### Router
Quando un router riceve un pacchetto, deve capire se la destinazione è interna o esterna alla sua rete, e quindi se tenerlo dentro o inoltrarlo al di fuori di essa. Per farlo, esegue i seguenti passaggi:
1. _AND bit a bit_ tra il suo indirizzo e la subnet mask -> ottiene l'_indirizzo di rete in cui si trova_;
2. _AND bit a bit_ tra l'indirizzo di destinazione e la subnet mask -> ottiene l'_indirizzo di rete di destinazione_;
3. confronta i due risultati:
	- sono uguali --> il pacchetto è destinato a un host interno;
	- sono diversi --> il pacchetto è destinato a un host esterno.

In questo modo l'IP può essere sfruttato in modo gerarchico tra le sottoreti. Il router controlla se la destinazione è tra le sue sottoreti, e se non lo è lo inoltra al suo **default gateway** (di livello superiore nell'albero):
- o _manda su_ (al padre) il pacchetto;
- o _manda giù_ (cercando la sottorete giusta del pacchetto).

Infatti per ogni host e router è necessario specificare il default gateway, ossia il "padre" che gli consente di comunicare con l'esterno. Per gli host l'esterno è la sottorete, mentre per i router è una rete diversa.

## Casi speciali
Esistono due casi particolari di subnet:
- _rete degenere `/31`_: non può contenere host, neanche router, a meno che non si assegni il broadcast al router e lui sia l'unico ad appartenere alla rete, diventando l'indirizzo di una macchina sola;
- _rete con solo due host indirizzabili `/30`_: viene usata di solito per connettere due router, così da minimizzare lo spreco di reti.

## Referenze
- [[ARP]]