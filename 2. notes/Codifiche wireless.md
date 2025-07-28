---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 11-07-2025 11:40:05
links:
  - "[[Lecture 08042025152354]]"
  - "[[Lecture 14042025111851]]"
  - "[[Lecture 15042025152135]]"
  - "[[Lecture 28042025111320]]"
---
# Codifiche wireless
---
## Introduzione
L'efficienza di trasmissione, anche nel mondo wireless, non dipende dalla banda di frequenze utilizzate, ma unicamente dal **tempo di codifica e decodifica dei segnali**, ossia dalla **durata nel tempo della rappresentazione di ogni singolo bit**.

### Copertura
Per comprendere le principali tecnologie di codifica wireless, è importante considerare la **copertura**: ogni dispositivo ha un raggio di copertura del segnale indipendente.

Questo significa che un dispositivo puo' essere in grado di sentire il segnale trasmesso da un dispositivo con ampio raggio, ma non viceversa (quest'ultimo potrebbe non sentirlo).
![[copertura-wireless.png]]

Oppure due dispositivi possono sentirsi a vicenda, ma avere tempi di codifica e decodifica differenti, e quindi non essere in grado di comunicare efficacemente.
![[copertura-wireless-2.png]]

## Tecnologie
Le principali tecnologie di codifica wireless includono:
- **Narrowband**
- **Spread Spectrum**
- **Infrared**

### Narrowband
Questa tecnologia prevede che la comunicazione avvenga usando una _stessa frequenza_, o meglio uno stesso _strettissimo intervallo di frequenze_.

Quindi, gli interlocutori devono mettersi d'accordo su quale frequenza usare, e inoltre per evitare le collisioni deve intervenire pesantemente il protocollo [[MAC]].

### Spread Spectrum
Al contrario della precedente, questa tecnologia adotta un ampio intervallo di frequenze, garantendo una **migliore sicurezza** e **efficienza**: per un attaccante diventa _piu' complesso compiere attacchi_ o _azioni di disturbo_.

Le tecniche principali sono:
- [[FHSS]]
- [[DSSS]]

## Interferenze
Sia che si usi narrowband che spread spectrum, le _interferenze sono un problema comune nelle comunicazioni wireless_. In particolare, le interferenze narrowband di una durata indefinita sono difficili da gestire.

Per esempio, se usiamo _narrowband diretto_ (quindi una sola frequenza per trasmettere), un'interferenza prolungata su quella stessa frequenza porterebbe a una _totale perdita di comunicazione_.

Ma anche con spread spectrum, per esempio con _FHSS_, un'interferenza prolungata su una frequenza specifica potrebbe portare a una _perdita parziale di comunicazione_.

### Soluzione
Per mitigare questo tipo di interferenze, di solito, si usa DSSS unito a [[CDMA]]: questo spalma i dati inviati in narrowband su tutta la banda di frequenza disponibile, rendoli meno suscettibili alle interferenze.
![[cdma.png]]

## Referenze
- [[Multiplexing wireless]]
- [[Modulazione]]
- [[Rilevamento degli errori]]