---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 06-04-2025 15:16:34
links:
  - "[[Lecture 17032025095233]]"
---
# Pacchetto
---
## Introduzione
> Il **pacchetto** [[IP]] e' l'unita' di dati trasmessa sulle reti dal [[Livello rete|livello rete]] del [[Modello ISO-OSI|modello ISO-OSI]].

## Composizione
Il pacchetto si compone di:
- **header**: contiene informazioni di routing e controllo;
- **payload**: contiene i dati da trasmettere.

### Header
L'header IP identifica:
- _versione_ (4 o 6) del protocollo IP usato;
- _lunghezza dell'header_ in bytes;
- _TOS_ (Type Of Service) --> ideato per dare priorità ai flussi (ma e' in disuso);
- _lunghezza del pacchetto_ in bytes;
- informazioni per la frammentazione:
	- _identificatore del pacchetto_ --> serve per identificare un frammento di pacchetto per capire di quale pacchetto fa realmente parte, se è avvenuta frammentazione;
	- _flag per la frammentazione_ --> se è frammentato o meno;
	- _offset di frammento_ --> per capire l'ordine del frammento;
- _TTL_ (Time To Live) --> serve a evitare che un pacchetto rimanga in circolo indefinitamente; viene decrementato ad ogni passaggio di router e se arriva a 0 il pacchetto viene scartato;
- _livello superiore_ --> il protocollo di livello superiore a cui far destinare il pacchetto ([[TCP]] o [[UDP]]);
- _header checksum_ --> serve a capire se c'è un bit errato all'interno dell'header;
- _[[Indirizzo IP|indirizzo IP]] sorgente_;
- _indirizzo IP destinatario_;
- opzioni, tra cui
	- _timestamp_
	- _record route taken_ (un traceroute fatto dal destinatario)
	- _lista dei router da visitare_

#### Overhead
Senza considerare le opzioni, in totale un **header IP e' di 20 bytes**. Lo stesso vale per il segmento TCP (20 bytes), per cui _in totale per una trasmissione funzionante e affidabile avremo bisogno di 40 bytes di overhead_.

Bisognerebbe ridurre questo overhead il piu' possibile, eliminando magari campi non necessari. Ma questo non ha senso: ormai e' lo standard usato da tutte le [[Scheda di rete|schede di rete]], da tutti i [[Sistema operativo|sistemi operativi]] e da tutti i [[Router|router]]!

Di conseguenza si cerca di **massimizzare la dimensione del payload**, cercando cosi' di _inviare segmenti e pacchetti solo quando la quantita' di dati trasmessa raggiunge una certa dimensione_. Ma questo **potrebbe fare a pugni con le esigenze dell'applicazione**: una chat non puo' sostenere questo ragionamento; invece un file transfer funziona bene con questo approccio.

### Payload
Il payload contiene proprio il [[Segmento|segmento]] TCP o UDP.

## Frammentazione
> L'idea di base e' quella di **prendere un pacchetto IP e di dividere il suo payload in piu' piccoli pacchetti da inviare separatamente**.

Chiaramente il destinatario dovra' riassemblare i pacchetti.

### Motivazioni
Questo risulta estremamente utile in quei _casi in cui certi collegamenti possono essere piu' deboli, attaccabili o fragili_, dove conviene dividere un pacchetto grande in pacchetti piu' piccoli.

La quantita' di dati (bytes) inviabili su un [[Mezzo di trasmissione|mezzo trasmissivo]] e' indicato dall'[[MTU]], un _campo che identifica il piu' grande [[Frame|frame]]_ ([[Livello MAC-LLC|livello MAC-LLC]]) _inviabile in una sola volta_.

<u>Nota bene</u>: collegamenti diversi avranno MTU diverso.

### Funzionamento
![[ip-frammentazione.png]]

Si mostra da esempio che un pacchetto da 4000 bytes se dev'essere inviato su un collegamento con MTU di 1500 bytes viene diviso in 3 pacchetti:
- primo pacchetto da 1500 bytes --> 20 bytes di header + 1480 bytes di payload; offset a 0;
- secondo pacchetto da 1500 bytes --> 20 bytes di header + 1480 bytes di payload; offset a 185 (1480/8);
- terzo pacchetto da 1040 bytes --> 20 bytes di header + 1020 bytes di payload; offset a 370 (2960/8).

<u>Nota bene</u>: l'offset, per una questione di risparmio di spazio, non e' propriamente il numero del byte del payload da cui riprendere, ma questo diviso 8.

<u>Nota bene</u>: in totale devono essere inviati 3980 bytes di payload, per questo l'ultimo pacchetto non e' semplicemente da 1000 bytes ma da 1040 bytes!

## IPv6
![[ipv6-pacchetto.png]]

Fondamentalmente il pacchetto IPv6 prevede:
- _priorita'_ --> un campo di 4 bit che indica la priorita' del pacchetto;
- _flow_ --> un campo di 20 bit che identifica il flusso (non ben definito);
- _lunghezza del pacchetto_;
- _next header_ --> un campo di 8 bit che identifica il protocollo di livello superiore (TCP o UDP);
- _hop limit_ --> il TTL del pacchetto;
- _indirizzo IP sorgente_ --> a 128 bit;
- _indirizzo IP destinatario_ --> a 128 bit;

Fondamentalmente quindi le differenze con l'IPv4 stanno nel fatto che:
- il _checksum_ e' completamente rimosso;
- non esiste la _frammentazione_;
- le opzioni sono state rimosse, o meglio incorporate in next header;
- l'header ha dimensione fissa di 40 bytes;

## Referenze