---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 22-09-2025 13:52:56
links:
  - "[[Lecture 22092025100902]]"
  - "[[Lecture 29092025103533]]"
  - "[[Lecture 06102025105214]]"
---
# Linguaggio di programmazione orientato a oggetti
---
## Introduzione
L'approccio _orientato a oggetti_ costringe il programmatore a modellizzare il mondo secondo un modello ben preciso: proprio quello a oggetti. In particolare usando i principi di:
- [[Information hiding|information hiding]]
- [[Astrazione|astrazione]]
- [[Modularizzazione|modularizzazione]]
- riuso

Quando si parla di _oggetti_ si intendono 2 significati:
1. la classe come [[Strutture dati|struttura dati]] che contiene _campi_ e _metodi_;
2. la computazione come interazione tra gli oggetti;

All'inizio le due parti erano un tutt'uno, ma negli anni '70 la parte di computazione tramite interazione si è scissa dalla definizione di oggetto --> è diventata parte della _programmazione ad attori/agenti_.

## Modello
Il modello a oggetti prevede:
- **classi** e **gerarchia di classi**, che contengono
	- attributi
	- metodi
	- ereditarietà
	- relazioni con altre classi
- **oggetti** o **istanze delle classi**, che contengono
	- attributi inizializzati a dei valori
	- relazioni con altre classi istanziate (oggetti)

Il modello di processo per l'identificazione delle classi all'interno di un sistema software a partire dalle specifiche dell'utente è il seguente:
![[oo-process-model.png]]

In altri termini, è ciclico! Il _modello finale si definisce iterazione dopo iterazione_...

## Caratteristiche
I linguaggi orientati ad oggetti hanno:
- concetto di **classe**[^1];
- **[[Ereditarietà|ereditarietà]]**[^2];
- **[[Polimorfismo|polimorfismo]]**.

## Curiosità
Il primo linguaggi orientato agli oggetti è [[Simula66]] (1966).

Per poter stabilire a che classe appartiene un oggetto possiamo usare 2 modelli:
- _esplicito_/standard - per enumerazione, ossia dichiarando il [[Tipi di dato|tipo]] dell'oggetto;
- _implicito_ - dal nome dell'oggetto
	- è più raro
	- si usa per esempio nelle [[JUnit]]

E' possibile cambiare a runtime la classe di un oggetto, usando:
- in [[C++]]/[[Java]] il polimorfismo (in particolare l'[[Overriding|overriding]]);
- in [[C]] usando i puntatori void (`void*`).

## Referenze

[^1]: attenzione che esiste per esempio il linguaggio [[ADA]] che ha classi ma non è ad oggetti
[^2]: anche qui, esiste [[Rust]] (se lo si considera ad oggetti) e [[GO]] che non hanno l'ereditarietà
