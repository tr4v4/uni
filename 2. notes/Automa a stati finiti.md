---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 14-10-2024 10:43:06
links:
  - "[[Lecture 03102024120247]]"
---
# Automa a stati finiti
---
## Introduzione
In generale, possiamo definire un **automa a stati finiti** come una macchina composta da una _testina di lettura_ posizionata sul primo carattere di una stringa posta in input, e da un insieme finito di stati cui iniziale è $q_{0}$[^1].
![[automa-a-stati-finiti.png]]

Il principio di funzionamento è il seguente:
- fintanto che la stringa in input non è terminata
	1. leggi il carattere in input, e in base allo stato in cui si trova decide se:
		- cambiare stato;
		- cambiare stato e spostare la testina sul carattere successivo;
	2. se lo stato nuovo è finale allora la stringa fino a quel momento è riconosciuta;
	3. se invece non esiste uno stato specificato per la coppia (stato corrente, carattere in input) bloccati;

Per riassumere il comportamento di un automa solitamente si fa uso di [[Diagramma di transizione|diagrammi di transizione]].

## Tipologie
- [[NFA]]
- [[DFA]]

## Referenze
[^1]: è una sorta di [[Macchina di Turing|macchina di Turing]] ma che non può scrivere