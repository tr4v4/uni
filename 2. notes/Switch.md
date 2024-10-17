---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 02-10-2024 13:44:03
links:
  - "[[Lecture 25092024132223]]"
---
# Switch
---
## Introduzione
> Uno **switch** è un componente hardware di [[Rete|rete]] usato come nodo centrale di una [[Infrastruttura di rete|infrastruttura]] realizzata con [[Topologia di rete#Stella|topologia a stella]].

## Caratteristiche
Lo switch:
- lavora a [[Livello fisico|livello fisico]] e a [[Livello MAC-LLC|livello MAC-LLC]], quindi sugli indirizzi di mittente e destinatario;
- quando riceve un frame, decodifica l'indirizzo MAC del destinatario e fa un _lookup_ su una tabella che associa ogni indirizzo MAC alla porta a cui è connesso, inoltrando il messaggio solo a quella porta --> questo risolve il problema delle collisioni, perché ci possono essere più comunicazioni allo stesso momento;
- se due host mandano un messaggio a uno stesso destinatario, lo switch li mette in coda usando un _buffer_.

## Referenze