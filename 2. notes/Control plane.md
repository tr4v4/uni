---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 30-03-2025 23:30:54
links:
  - "[[Lecture 11032025152719]]"
  - "[[Lecture 17032025095233]]"
---
# Control plane
---
## Introduzione
> Il **control plane** è uno dei due sottolivelli del [[Livello rete|livello rete]] e si occupa di _popolare la tabella di inoltro (forwarding) locale, sulla base delle informazioni passate con i [[Router|router]] circostanti, e serve per il [[Routing|routing]]_.

## Funzionamento
Del control plane ci possono essere due implementazioni:
- **distribuita** - i router si scambiano informazioni tra loro per popolare le tabelle di inoltro;
	- e' una soluzione necessaria in caso di sistemi dinamici (come le reti wireless);
	- la soluzione trovata dai router non e' assicurata essere l'ottimale, perche' la visibilita' della rete e' ridotta;
	- ![[control-plane-distribuito.png]]
- **centralizzata** - si ha un _controller_, un sistema super-partes, che si occupa di popolare le tabelle di inoltro dei router;
	- trova la soluzione ottimale, garantendo massima efficienza;
	- il problema e' che se cade il controller cade tutto il sistema;
	- ![[control-plane-remote-controller.png]]

Un esempio di controller e' il [[SDN]].

## Referenze