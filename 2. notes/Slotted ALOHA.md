---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-07-2025 17:01:57
links:
  - "[[Lecture 05052025111914]]"
---
# Slotted ALOHA
---
## Protocollo
![[slotted-aloha.png]]

A differenza del semplice [[ALOHA]], il tempo qui e' quantizzato in slot (intervalli di tempo fissi), e ogni invio e ricezione di frame avviene all'inizio di uno di questi. La grandezza degli slot e' calcolata come
$$\text{frame size} + \text{propagation delay}$$
dove il _propagation delay_ e' il tempo necessario al segnale per arrivare al destinatario. Questo e' di fondamentale importanza: il segnale del frame altrimenti potrebbe entrare nello slot successivo e generare una collisione.

![[slotted-aloha-collision-domain.png]]

Quindi, il tempo di vulnerabilita' dei frame si riduce a **1 volta la dimensione del frame** (o meglio la dimensione di uno slot). Per implementare questo protocollo, tuttavia, e' necessario sincronizzare tutti gli attori in gioco con gli slot di tempo.

## Referenze