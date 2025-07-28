---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-07-2025 17:49:36
links:
  - "[[Lecture 07042025111854]]"
---
# Zona di Fresnel
---
## Introduzione
> La **zona di Fresnel** e' una regione ellissoidale che circonda la [[LOS]] di un segnale radio di un'[[Antenna altamente-direzionale|antenna altamente-direzionale]].

I segnali subiscono la diffrazione, ma parte di quella diffrazione riconverge nella direzione originale, _in addizione o in opposizione di fase_. La **maggior parte della potenza del segnale difratto e poi ricongiunto a quello originale in modo additivo si concentra nella zona di Fresnel**.
![[zona-di-fresnel.png]]

E' importante tenere libera questa zona per evitare proprio di perdere la maggior parte del segnale. Per esempio, un blocco della zona di Fresnel rischia seriamente di interrompere la comunicazione tra le due antenne. In particolare, **se si vuole mantenere una comunicazione stabile, bisogna tenere la zona di Fresnel libera per almeno il 60% della sua area**.

## Calcolo della zona di Fresnel
Per calcolare il massimo raggio della zona di Fresnel tale che almeno il 60% della sua area sia libera da ostacoli (e di seguito il 100%), si usa la seguente formula:
$$R_{60\%} = 43.3 \cdot \sqrt{\frac{d}{4f}}$$
$$R_{100\%} = 72.2 \cdot \sqrt{\frac{d}{4f}}$$

dove
- $d$ e' la distanza tra le due antenne in miglia;
- $f$ e' la frequenza del segnale in GHz.

<u>Attenzione</u>: il raggio e' dato in piedi!

<u>Nota bene</u>: non serve né potenza né tipo di antenna, perché la diffrazione è un fenomeno che vale sempre.

## Osservazioni
In ambienti chiusi la zona di Fresnel non si applica, perché i segnali radio rimbalzano sulle pareti e si ricava l'energia da tali rimbalzi.

La stessa _curvatura terrestre può dimezzare la zona di Fresnel, quindi in caso di comunicazioni a lungo raggio bisogna tenere conto di questo fattore_.

## Referenze