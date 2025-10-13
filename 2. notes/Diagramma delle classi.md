---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 29-09-2025 22:41:08
links:
  - "[[Lecture 29092025150827]]"
  - "[[Lecture 06102025105214]]"
---
# Diagramma delle classi
---
## Introduzione
> Il **diagramma delle classi** in [[UML]] è un diagramma centrale per la _modellizzazione di sistemi software che usano il [[Linguaggio di programmazione orientato a oggetti|modello orientato agli oggetti]]_.

## Componenti
Il diagramma delle classi si compone di:
- **classi**, ovviamente, ricavabili dall'analisi dei requisiti --> sono i nomi!
- **associazioni**, ossia le relazioni tra le classi.

### Classi
E' importante considerare che _una classe può appartenere a più diagrammi_. Questo perché ogni diagramma descrive solo certe parti di una classe, ossia le sue associazioni con altre classi.

Le classi iniziano con la lettera maiuscola, in _camel case convention_.

Le classi contengono:
- **nome**;
- **attributi**;
- **metodi**;
- **responsabilità**.

#### Oggetti
Si possono definire così attraverso l'associazione `<<istanceOf>>` degli oggetti istanza di una classe (andando ad unire il diagramma delle classi con il [[Diagramma degli oggetti|diagramma degli oggetti]]).

### Associazioni
Ad ogni associazione tra 2 classi viene dato:
- un **nome** - che può essere parte di un verbo fraseologico, è scritto in _camel case convention_;
- una **direzione** - che può essere unilaterale come bilaterale;
- **2 ruoli** - ogni ruolo è associato alla direzione dell'associazione, ed è un _nome-istanza della classe che compie quella relazione nei confronti dell'altra_;
- una **molteplicità** - indica il numero di elementi che partecipano nell'associazione.

Un esempio riassuntivo è il seguente:
![[diagramma-classi-uml-1.png]]

#### Associazioni particolari
Esistono poi 4 tipi di associazioni particolari.

##### Aggregazione
- ci dice che un oggetto e' formato da un altro oggetto;
- per esempio: Motore e Ruote sono classi aggregate alla Macchina;
- e' una [[Transitività di una relazione|relazione transitiva]] (non un preordine perche' non vale neanche la [[Riflessività di una relazione|riflessivita']]);
- ![[diagramma-classi-aggregazione.png]]

##### Composizione
- simile all'aggregazione;
- l'oggetto e' parte integrante di un tuttuno, e muore se muore il tuttuno;
- ![[diagramma-classi-composizione.png]]

##### Generalizzazione
- anche detto sottotipaggio
- diversa da istanziazione
	- infatti la generalizzazione e' transitiva, mentre l'istanziazione no
	- le istanze appartengono alla classe, invece le generalizzazioni sono sottoinsiemi delle classi
	- ![[generalizzazione-vs-istanziazione.png]]
- la generalizzazione di solito si può concretizzare in:
	- _estensione_ - metodo standard, in cui la sottoclasse eredita tutto dalla superclasse;
	- _restrizione_ - di difficile realizzazione, in cui la sottoclasse vincola attributi o metodi della superclasse;

##### Contenimento

##### Ereditarietà
- ![[diagramma-classi-ereditarietà.png]]
- esiste anche l'ereditarietà multipla!
	- in tal caso può avvenire che le gerarchie si sovrappongano, come nel seguente caso:
		- ![[ereditarietà-multipla.png]]
		- il problema, di fatto, si pone quando una classe eredita da due classi che a loro volta vengono dalla stessa radice!
	- per questo motivo nasce l'_ereditarietà virtuale_
		- non ha niente a che vedere con le funzioni virtuali
		- serve per disambiguare il caso precedente
		- le derivazioni virtuali ereditano un'unica copia della superclasse (è un po' come `static`...)
	- ma è comunque scomoda --> per questo nasce la tecnica _delegation & aggregation_
		- ![[delegation-and-aggregation.png]]
		- fondamentalmente in questo caso `LandFeature` e `WaterFeature` contengono dei campi di `VehicleFeature` e cose loro; e vengono aggregati (in composition anche) all'intero del veicolo anfibio (in alto) --> in questo modo all'interno del veicolo anfibio ci saranno solo feature di terra e di acqua --> nessun conflitto!
		- un altro esempio è questo, con la composizione:
			- ![[delegation-and-aggregation-1.png]]

#### Classi di associazione
Ci sono casi in cui le associazioni sono così complesse da dover _contenere delle informazioni che non possono essere salvate in nessuna delle classi coinvolte_: le **associazioni diventano classi**!

## Cheat sheet
![[cheat-sheet-class-diagram.png]]

## Consigli
Si consiglia di partire nel modo più semplice possibile quando si deve fare un diagramma delle classi.

## Referenze