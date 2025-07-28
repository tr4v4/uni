---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 11-07-2025 12:01:00
links:
  - "[[Lecture 14042025111851]]"
  - "[[Lecture 15042025152135]]"
  - "[[Lecture 28042025111320]]"
---
# Multiplexing wireless
---
## Introduzione
Nel wireless, a differenza che nelle reti cablate, il [[Canale di comunicazione|canale di comunicazione]] e' forzatamente ad accesso multiplo e condiviso (almeno nell'area di copertura della rete). E' quindi necessario sfruttare delle tecniche che consentano una _trasmissione efficiente ma senza collisioni tra i vari dispositivi_.

> Il **multiplexing wireless** è una tecnica che consente di _trasmettere più segnali contemporaneamente su un singolo canale di comunicazione_, migliorando l'efficienza e la capacità della rete.

## Dimensioni
Nella pratica questo consiste nella divisione del canale in 4 dimensioni:
- _spazio_
- _tempo_
- _frequenza_
- _codice_

### Frequenza
Si separa l'intero spettro in bande di frequenza, e ogni canale viene associato a una di queste. Tra una banda e l'altra si lasciano i cosiddetti _spazi di guardia_, per _mitigare effetti Doppler_ della propagazione del segnale (il gap e' minimo, ma serve).
![[frequency-multiplex.png]]

Gli interlocutori, per mettersi d'accordo su quale banda usare, devono prima utilizzare un _canale di default iniziale_.

Vantaggi:
- non serve una particolare coordinazione dinamica (avviene solo all'inizio);
- funziona su canali analogici;

Svantaggi:
- si sprecano bande di frequenza se il traffico e' distribuito inequamente;
- non e' flessibile;
- servono gli spazi di guardia;

### Tempo
Ad ogni canale viene associato l'intero spettro per un determinato periodo di tempo, poi si passa al canale successivo, in modo ciclico. Anche qui sono necessari _spazi di guardia_, ma stavolta in _direzione del tempo_ (e non della frequenza): si vuole aspettare che il segnale propagato finisca il suo "eco".
![[time-multiplex.png]]

Vantaggi:
- solo un trasmettitore nel mezzo alla volta;
- throughput estremamente alto anche con tanti dispositivi;

Svantaggi:
- serve un meccanismo di sincronizzazione tra i dispositivi (l'hop deve avvenire simultaneamente);

### Tempo + frequenza
Un canale ottiene una certa frequenza per un certo periodo di tempo, e poi si salta a una frequenza diversa, sempre per un certo periodo di tempo. Il ricevitore deve conoscere l'esatta sequenza delle frequenze ed essere sincronizzato.
![[time-frequency-multiplex.png]]

E' il funzionamento di [[GSM]].

Vantaggi:
- protezione migliore contro "spie";
- protezione migliore contro interferenze mirate su certe frequenze;
- migliore data rate rispetto al code multiplex (di seguito);

Svantaggi:
- richiede una coordinazione precisa tra i dispositivi;

### Codice
Sfrutta le _chip sequence_: ogni canale ha un codice, una sequenza di chip, e tutti i canali usano lo stesso spettro di frequenze.

Si usa chiaramente la tecnologia _spread spectrum_, e in particolare [[DSSS]].
![[code-multiplex.png]]

Vantaggi:
- bandwidth molto alta;
- non serve sincronizzazione precisa;
- buona protezione contro "spie" e interferenze;

Svantaggi:
- minore uso del data rate;
- piu' complesso e costoso rigenerare il segnale;

## Referenze
- [[OFDM]]