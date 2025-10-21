---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 18-10-2025 12:13:24
links:
  - "[[Lecture 14052025105842]]"
---
# VTable
---
## Introduzione
> Le **vtable** (**virtual function table**) sono una [[Struttura dati|struttura dati]] usata per gestire l'[[Sottotipaggio|overriding]] nei [[Linguaggio di programmazione orientato a oggetti|linguaggi a oggetti]] con [[Ereditarietà|ereditarieta' singola]]. In particolare e' l'implementazione primaria del [[Dynamic dispatch|dynamic dispatch]].

## Funzionamento
Ogni definizione di [[Classe|classe]] corrisponde a una vtable, e tutte le istanze ([[Oggetto|oggetti]]) di quella classe puntano alla stessa vtable. Questa **contiene i puntatori ai metodi della classe**.

Se `A` e' una classe con la sua vtable, e definiamo `B::A` (sottoclasse di A), allora **la vtable di `B` copiera' quella di `A` andando pero' a ridefinire i metodi overriddati da `B`** (funzioni virtuali di `A`), e poi aggiungendo ovviamente i nuovi metodi introdotti da `B`.

Per esempio, il codice:
```Java
class A {
	int a;
	void f(){...}
	void g(){...}
}
class B extends A {
	int b;
	int c;
	void f(){...}
	void h(){...}
}

A o1 = new A();
A o2 = new B();
```
apparira' nelle vtable in questa maniera:
![[vtable-1.png]]

## Complessita' computazionale
Questa implementazione fornisce effettivamente dei vantaggi in termini di [[Complessità computazionale|complessita' computazionale]] rispetto alla [[Lista#Liste concatenate|lista concatenata]] di classi e sottoclassi (la seguente)?
![[oggetti-implementazione.png]]

La risposta e' si': l'invocazione di un metodo avviene al prezzo costante di 2 accessi. Infatti **il suo offset e' noto staticamente** ([[Early binding|early binding]])! Questo sembra strano, perche' abbiamo detto che l'overriding e' risolvibile solo dinamicamente ([[Late binding|late binding]]). Ma possiamo far si' che il compilatore calcoli uno stesso offset di ogni metodo, sia che questo appartenga ad `A` che a `B`. Per intenderci, la funzione `f` e' in `A` ed e' ridefinita in `B`: **l'offset tuttavia e' lo stesso all'interno della vtable, per cui se si accede ad `f` il compilatore staticamente sa che questo metodo si trova ad un certo offset**, indipendentemente dal fatto che sia la vtable di `A` o di `B`.

In altri termini, **i metodi devono rimanere nello stesso posto all'interno delle vtable per far funzionare il meccanismo staticamente**!

## Referenze
- [[Classe base fragile]]