---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-07-2025 18:09:56
links:
  - "[[Lecture 06052025152121]]"
---
# CSMA-CA
---
## Introduzione
> Il **Carrier Sense Multiple Access with Collision Avoidance (CSMA-CA)** è un [[Protocollo di rete|protocollo]] [[MAC]] di accesso al [[Canale di comunicazione|canale]] utilizzato nelle [[Rete wireless|reti wireless]] per evitare le collisioni tra le trasmissioni. Si tratta di un'unione di piu' protocolli sviluppati negli anni.

E' usato principalmente nella fase [[DCF]] per l'accesso con contesa al canale. Implementa:
- **carrier sensing** - ascolta prima di trasmettere;
- **binary exponential backoff** - meccanismo di attesa di ritrasmissione in caso di canale occupato;
- **ACK** - per confermare la ricezione dei dati;
- **[[RTS-CTS]]** (opzionale, dipende dalla modalita' operativa) - per evitare il [[Problema del terminale nascosto|problema del terminale nascosto]].

## Binary exponential backoff
E' un sistema che si differenzia dal semplice _random k backoff_ tipico di [[ALOHA]] (e quindi anche [[CSMA]]). Funziona cosi': subito dopo la fine di un DIFS, viene fatto slotting temporale del canale (sincronizzato automaticamente tra tutti gli host), e un host per trasmettere sceglie uno slot casuale tra $0$ e $CW$, dove $CW$ e' il **contention window**.

Ogni volta che, scaduto il backoff, provando a trasmettere l'host si rende conto che il canale e' occupato, raddoppia $CW$ e risceglie uno slot casuale tra $0$ e $CW$ da aspettare.

Formalmente, il tempo di attesa e' dett **backoff time**, ed e' calcolato come segue:
$$\text{BackOffTime(i)} = \text{CW(i)} \cdot \text{random(0, CW(i))} \cdot \text{SlotTime}$$
dove $i$ e' il numero di tentativi di trasmissione.

Si dice esponenziale perche' $CW$ raddoppia ogni volta:
![[binary-exponential-backoff-cw.png]]
(chiaramente il meccanismo del raddoppio serve per diminuire la probabilita' che piu' host scelgano lo stesso slot casuale).

Il backoff time (il timer) viene decrementato nel seguente modo:
- ad **ogni DIFS** (tempo lungo in cui nessuno trasmette) viene **decrementato del tempo di uno slot** ($\text{SlotTime}$);
- se il canale e' occupato, il timer viene **interrotto** e **ripreso quando il canale e' libero**.

<u>Attenzione</u>: si puo' benissimo presentare il problema del terminale nascosto! Per esempio, un host potrebbe non accorgersi che il suo ricevente sta gia' ricevendo dati da un altro host, e quindi alla fine del suo backoff time inizia a trasmettere, creando una collisione. E' per questo motivo che CSMA-CA prevede anche l'uso di RTS-CTS!

## Referenze