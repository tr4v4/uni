---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 14-10-2025 17:27:48
links:
  - "[[Lecture 08052025131742]]"
  - "[[Lecture 14052025105842]]"
---
# Oggetto
---
## Introduzione
> In informatica, un **oggetto**, e' una _capsula che contiene dati e operazioni per manipolarli e che fornisce un'interfaccia per accedervi_.

Le operazioni sono chiamate **metodi**, mentre le variabili interne **campi**.

## Implementazione
Un po' come gli [[Tipi di dato astratto|ADT]], gli oggetti sono implementati come dei [[Tipo prodotto#Record|record]], e i metodi sono esterni, e prendono in ingresso `self`, ossia il record dell'oggetto su cui si vuole che siano eseguite le operazioni.

Inoltre, a differenza degli ADT, hanno lo stato interno (un po' come gli [[Oggetti esistenziali|oggetti esistenziali]]).

Piu' precisamente, il codice seguente viene rappresentato in memoria in questo modo:
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

A o;
o = new B();
```
![[oggetti-implementazione.png]]

Strutturando le cose in questa maniera, semplifichiamo molto la gestione del [[Tipaggio statico|tipaggio statico]] (assumendo [[Ereditarietà|ereditarieta' singola]]): per conoscere per esempio cos'e' `o.c`, ci basta _calcolare l'offset del blocco di partenza appartenente alla superclasse `A`_, e quindi ad esso sommare l'offset standard per arrivare a `o.c`.

Questo _e' anche il modo in cui viene semplicemente implementato il [[Dynamic dispatch|dynamic dispatch]]_! Tuttavia e' parecchio inefficiente: **bisogna scorrere la [[Lista#Liste concatenate|lista concatenata]]**! Per questo si preferiscono e si adottano le [[Vtable|vtable]].

### Late _self_ binding
Quando un metodo viene invocato, il procedimento e' lo stesso dell'[[Invocazione di procedura|invocazione di procedura]]: bisogna caricare sullo [[Stack|stack]] le variabili locali e altre cose...

Il problema e' che i metodi dell'oggetto devono anche poter accedere ai campi della sua istanza `this`! Per farlo allora quello che si fa e' caricare sullo stack il riferimento a `this` ([[Puntatore|puntatore]] all'oggetto), e poi da li' accedere ai suoi campi **sommandoci l'offset specifico di ogni campo**: questo **possiamo farlo perche' di ogni oggetto ne conosciamo staticamente la classe**!

## Allocazione
Tutti i [[Linguaggio di programmazione orientato a oggetti|linguaggi orientati agli oggetti]] allocano gli oggetti [[Allocazione dinamica della memoria dei programmi|dinamicamente]], e quindi tendenzialmente nell'[[Heap|heap]]. Altri linguaggi, come [[C++]], pero', consentono di allocare anche sullo [[Stack|stack]].

Questo si fa, per esempio, _quando si sa che l'oggetto ha una dimensione che non puo' crescere_: e' piu' efficiente gestirlo nello stack. Ma questo non si fa quasi mai, perche' questa certezza e' difficile da ottenere.

Prendiamo per esempio il [[Sottotipaggio|subtyping]]: ci si aspetta un `Counter`, ma si ottiene un suo sottotipo, che probabilmente occupa piu' memoria di quella allocata --> rischia di rompere lo stack!

In C++, infatti, _si puo' allocare sullo stack a patto che l'oggetto sia "normato"_, ossia senza subtyping.

## Interfaccia
L'interfaccia di un oggetto e' la stessa degli [[ADT]]: **i metodi e i campi che il codice client puo' utilizzare per interagire con il valore di un certo tipo**.

Si distinguono 2 viste:
- _vista privata_ - quella completa dell'oggetto, che vede tutti i metodi e tutti i campi;
- _vista pubblica_ - quella determinata proprio dall'interfaccia.

### Visibilita'
A tal proposito, i modificatori di visibilita' sono:
- `private`
- `public`
- `package` - la visibilita' dei campi/metodi della classe e' estesa a tutte le classi che appartengono a quel [[Package|modulo]] (ricorda la relazione tra [[ADT]] e moduli);
- `protected` - la visibilita' dei campi/metodi e' estesa a tutte le sottoclassi.

## Referenze