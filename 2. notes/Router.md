---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 30-03-2025 22:47:25
links:
  - "[[Lecture 11032025152719]]"
  - "[[Lecture 17032025095233]]"
---
# Router
---
## Introduzione
> Il **router** è un dispositivo che _instrada i pacchetti tra reti diverse_, in base all'[[Indirizzo IP|indirizzo IP]] di destinazione e ai [[Protocollo di routing|protocolli di routing]].

## Funzionamento
Internamente un router si compone di:
- **switching fabric**;
- **routing processor**;
- **input ports**;
- **output ports**.

![[router-inside.png]]

### Switching fabric
Si tratta dei "binari" che consentono di attivare il percorso che collega un'interfaccia di input del router in una di output, sulla base della scelta di forwarding fatta dal _routing processor_. Opera in timeframes di nanosecondi, e se ne occupa il [[Data plane|data plane]].

Sono possibili 3 scelte implementative:
- _memoria_;
- _bus_, genera collo di bottiglia;
- _crossbar_, una matrice in cui ogni nodo d'intersezione può essere aperto o chiuso programmaticamente, consentendo di fare switch parallelo[^1].

![[switching-fabric.png]]

### Routing processor
E' il processore che compila la routing table e opera in timeframes di millisecondi, e se ne occupa il [[Control plane|control plane]]. Fondamentalmente consiste in una **forwarding table**, in cui a sinistra si ha un _intervallo di indirizzi di destinazione_ e a destra l'_interfaccia di output su cui fare il forwarding_.

![[forwarding-table.png]]

Nella realta' dei fatti, non si specifica l'intervallo degli indirizzi di destinazione, bensì il _prefisso comune a tutti gli indirizzi del range_:
![[forwarding-table-prefix.png]]

Di conseguenza, nei casi in cui più prefissi matchino con l'indirizzo di destinazione in questione, si usa la regola del _longest prefix matching_: **si considera il prefisso più lungo che matcha con l'indirizzo di destinazione**.

Il motivo per cui si usa il _longest prefix matching_ è perché così si può sfruttare il [[TCAM]], tabelle visitabili in 1 ciclo di clock!

<u>Nota bene</u>: di solito il campo "altrimenti" rappresenta il _default gateway_.

### Input ports
Ogni interfaccia di input al router è composta da:
- _line termination_ ([[Livello fisico|livello fisico]]);
- _link layer protocol_ ([[Livello MAC-LLC|livello MAC-LLC]]);
- _lookup_ (sbirci l'intestazione del pacchetto per capire chi è il destinatario), _forwarding_, _queueing_.

![[router-input-port.png]]

### Output ports
Serve anche qui un buffer di uscita: dal protocollo [[MAC]] dobbiamo stare in ascolto perché qualcun altro potrebbe star parlando, non possiamo fare collisioni.
![[router-outside-port.png]]

## Buffering
In definitiva:
- se perde pacchetti in buffer di input --> buffer [[Congestione di rete|congestionato]];
- se perde pacchetti in buffer di output --> le linee di uscita sono sempre occupate dalle comunicazioni di altri.

Per determinare la grandezza ottimale del buffer si usa la _regola del pollice_: si usa il BDP, ossia _bandwidth delay product_, che è il prodotto della _larghezza di banda_ (in bit) e del _[[RTT]]_ (in secondi). Si tratta di un valore in bit, che va convertito in byte dividendo per 8.

## Referenze
- [[Network scheduling]]

[^1]: l'idea e' la stessa dei [[NOC]] (Network On Chip), ossia di circuiti che comunicano usando switch come se fossero su una rete
