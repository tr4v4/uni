---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 29-02-2024 16:35:16
links:
  - "[[Lecture 28022024111804]]"
  - "[[Lecture 29022024091237]]"
  - "[[Lecture 04032024091423]]"
---
# Java
---
## Introduzione
> **Java** è un [[Linguaggio di programmazione|linguaggio di programmazione]] [[OOP|object-oriented]] sviluppato negli anni '90.

Il suo punto di forza sta nella [[Compilazione a 2 livelli|compilazione a 2 livelli]] attuata dalla [[JVM|Java Virtual Machine]] (_JVM_), che lo rende _indipendente dalla piattaforma e portabile_ ([[WORA]]).

## Tipi di dati
Java divide i [[Tipi di dati|dati]] in due principali categorie:
- _primitivi_
	- `int`, `boolean`, `char`, `short`, `long`, `float`, `double`
	- per ognuno dei quali esiste una _rispettiva classe wrapper_, con operazioni di _boxing_ e _unboxing_ automatiche
- _classi_
	- definite dall'utente o incluse in librerie

### Classi utili
In particolare si ricordano classi di fondamentale importanza tra cui:
- `String`, per la manipolazione di stringhe;
- `Arrays` (_statica_) per la manipolazione di [[Array|array]] (come l'[[Algoritmo di ordinamento|ordinamento]])
	- in particolare il metodo `sort` è la combinazione tra [[Insertion sort|insertion sort]], [[Merge sort|merge sort]] e [[Quick sort|quick sort]];
	- il quick sort implementato usa due pivot, per diminuire la probabilità di beccarne uno pessimo (_DualPivot QuickSort_)
	- l'insertion sort è usato su istanze piccole, $\leq 47$
		- ed è usato nei `merge` e nei `partition` di merge sort e quick sort
	- il merge sort è preferito al quick sort su istanze grandi, $\geq 286$

## Caratteristiche
Java basa la sua struttura sull'[[Ereditarietà|ereditarietà]] e sul [[Polimorfismo|polimorfismo]]. In particolare ricordarsi che:
- in caso di _overwriting_ bisogna specificare l'annotazione `@Override`;
	- di solito si fa l'override di metodi base come `toString()` e `equals()`;
		- in particolare per `equals()` un metodo potrebbe essere
		```java
		  if (obj == null || !(obj isinstanceof NomeClasse))
			  return false;
			else
				return ... // confronta tutti gli attributi
		```
		- ma attenzione, fare il _typecasting_ su `obj` per poter confrontare gli attributi di `NomeClasse`
- `super` è la _key-word_ per accedere a metodi e attributi della superclasse;
- la classe `Object` è la superclasse di tutte le classi in Java;
- le _eccezioni_ sono tutti oggetti, solitamente sottoclassi della classe `Exception`
	- c'è una gerarchia di eccezioni ![[java-exceptions.png]]
	- per il lancio delle eccezioni ci sono `throws` (nella firma del metodo) e `throw` (all'interno del metodo);
	- per la presa delle eccezioin c'è il costrutto `try & catch`;
	- si possono definire eccezioni estendendo `Exception` o qualunque altra classe che implementi l'[[Interfaccia|interfaccia]] `throwable`;

## Comandi
- `javac NomeFile.java` per la _[[Compilatore|compilazione]]_ di primo livello;
- `java NomeFile` per l'_[[Interprete|interpretazione]]_ di secondo livello;
- `javadoc NomeFile.java` per la generazione della documentazione automatica Java (_JavaDoc_)

## Referenze