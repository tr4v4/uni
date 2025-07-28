---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 27-09-2024 17:03:51
links:
  - "[[Lecture 18092024131539]]"
---
# Jitter
---
## Introduzione
> Il **jitter** è l'indice di [[Prestazione delle reti|prestazione]] di una [[Rete|rete]] legato alla _varianza del ritardo di arrivo dei pacchetti_.

Ogni pacchetto di rete, infatti, arriva a destinazione con un tempo misurabile (latenza). Possiamo calcolare la media di questi tempi di arrivo, e la media della distanza di ogni tempo da questa media si chiama **[[Varianza|varianza]]**[^1].

Questa varianza, e quindi il jitter, indica la **stabilità della connessione**:
- _più la varianza è bassa più la distanza di tempo di arrivo tra un pacchetto e l'altro è stabile_;
- _più la varianza è alta più significa che tra un pacchetto e l'altro è poco prevedibile il tempo di attesa_.

### Rapporto con latenza
Non bisogna confondere il jitter con la latenza. Per capirlo basti pensare che una latenza bassa non implica per forza una qualità della connessione alta: il jitter potrebbe essere alto, provocando discontinuità nella connessione. Viceversa una latenza alta potrebbe avere un jitter basso e garantire quindi una fluidità di trasmissione.

E' ovvio che anche qui dipenda dall'utilizzo della rete:
- per lo streaming è meglio una latenza alta con jitter basso;
- per i videogiochi online è meglio una latenza bassa con jitter alto.

<u>Nota bene</u>: una non esclude l'altra, si possono avere anche entrambe le cose!

<u>Nota bene</u>; spesso non ci rendiamo conto di un alto jitter perché le applicazioni utilizzano un _buffer di pacchetti che viene svuotato lentamente mano a mano che la trasmissione continua_. Così, in momenti di ritardo nella ricezione dei pacchetti, nel buffer ce ne sono comunque ancora da svuotare, dando l'impressione che la connessione sia fluida e continua. Questo ci dice che un cattivo jitter si paga in utilizzo di memoria!

## Referenze
[^1]: in realtà non si tratta proprio di una media, ma per fini didattici la semplifichiamo