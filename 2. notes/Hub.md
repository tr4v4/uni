---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 02-10-2024 13:30:39
links:
  - "[[Lecture 25092024132223]]"
---
# Hub
---
## Introduzione
> Un **hub** è un componente hardware di [[Rete|rete]] usato come nodo centrale di una [[Infrastruttura di rete|infrastruttura]] realizzata con [[Topologia di rete#Stella|topologia a stella]].

## Caratteristiche
Un hub:
- lavora a [[Livello fisico|livello fisico]], quindi solo e unicamente sui segnali;
- fa sempre un broadcast di ciò che riceve in input;
- rigenera il segnale, indebolito dalla distanza;
- è un _dominio di collisione_, quindi se due host parlano contemporaneamente l'hub sparge entrambi i segnali, mandando in broadcast un segnale compromesso[^1].

## Referenze
[^1]: il protocollo [[Ethernet]] risolve il problema, dando alle [[Scheda di rete|schede di rete]] la capacità di ascoltarsi mentre trasmettono, così da fermarsi non appena sentono una distorsione del proprio segnale