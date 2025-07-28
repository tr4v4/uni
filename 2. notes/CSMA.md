---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-07-2025 17:07:05
links:
  - "[[Lecture 05052025111914]]"
---
# CSMA
---
## Protocollo
![[csma.png]]

Il CSMA (Carrier Sense Multiple Access) ha come idea quella di ascoltare il canale radio prima di trasmettere, e quindi di trasmettere solo quando questo e' libero. In caso contrario, un po' come [[ALOHA]], si attende un tempo casuale prima di riprovare a trasmettere.

![[csma-collision-domain.png]]

Il tempo di vulnerabilita' dei frame, cosi' facendo, si riduce addirittura a solo **2 volte il propagation delay**!

## Referenze