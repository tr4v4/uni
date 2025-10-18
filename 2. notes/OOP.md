---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 20-09-2023 18:55:50
links:
  - "[[Lecture 20092023091613]]"
  - "[[Lecture 29112023092601]]"
  - "[[Lecture 30112023091742]]"
  - "[[Lecture 14052025105842]]"
---
# OOP
---
## Definizione
> Per **OOP** (_Object Oriented Programming_) intendiamo un approccio alla programmazione basata sull'utilizzo di [[Oggetto|oggetti]], definiti da [[Classe|classi]], che contengono _attributi_ e _metodi_. La cosiddetta, quindi, _programmazione a oggetti_ è usata in molti dei moderni [[Linguaggio di programmazione|linguaggi di programmazione]] per via dei netti vantaggi che offre in confronto alla classica [[Programmazione imperativa|programmazione imperativa]].

## Caratteristiche
- **encapsulation** ([[Incapsulamento|incapsulamento]])
- **inheritance** ([[Ereditarietà|ereditarietà]])
	- possiamo creare oggetti che ereditano metodi e attributi di altri oggetti, con possibilità di "personalizzarli"
- **polymorphism** ([[Polimorfismo|polimorfismo]])
	- un nome di un metodo può far riferimento a diversi metodi a seconda del contesto in cui è definito
- **abstraction** ([[Interfaccia|interfacce]])
	- la possibilita' di obbligare una classe a implementare dei metodi definiti da un contratto (interfaccia), senza fornire in esso l'implementazione

E' fondamentale catturare la differenza tra sottotipaggio ed ereditarieta':
- [[Sottotipaggio|sottotipaggio]] -> possibilita' di usare un'oggetto in un altro contesto (suo supertipo) --> e' una relazione tra le interfacce di due classi;
- ereditarieta' -> possibilita' di riutilizzare il codice che manipola un oggetto --> relazione tra le implementazioni di due classi.

La confusione si fa per via delle convenzioni: **l'estensione da classe a classe, e quindi l'ereditarieta', di solito implica anche la relazione di sottotipaggio**! Ma non e' per forza detto.

## Referenze