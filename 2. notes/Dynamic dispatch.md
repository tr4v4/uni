---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 18-10-2025 11:27:04
links:
  - "[[Lecture 14052025105842]]"
---
# Dynamic dispatch
---
## Introduzione
> Il **dynamic dispatch** e' il [[Dispatch|dispatch]] che avviene a _run-time_. E' fondamentalmente il [[Late binding|late binding]] per la [[OOP]].

E' la conseguenza della proprieta' [[Polimorfismo|polimorfica]] dell'[[Sottotipaggio|overriding]].

## Comportamento
Il comportamento dei metodi virtuali cambia a seconda del contesto:
- se il metodo virtuale è invocato su un oggetto di cui si riconosce il tipo a compile-time $\implies$ si comporta come se fosse non-virtuale;
- viceversa
	- assumiamo di invocare `f` su oggetto `o::D` e `D extends B`, allora
		1. se `f` è definita solo in `D` $\implies$ `D.f()`;
		2. se `f` è definita solo in `B` $\implies$ `B.f()` per via dell'[[Ereditarietà|ereditarietà]];
		3. se `f` è _ridefinita_ in `D` $\implies$ `D.f()` per via dell'overriding;

Il caso complesso si ha quando `o::B` ma `o = new D()`. In questo caso infatti:
1. se `f` è definita solo in `B` $\implies$ `B.f()`;
2. se `f` è definita solo in `D` $\implies$ `errore` (non c'è in `B`);
3. se `f` è _ridefinita_ in `D` $\implies$ `D.f()`;

## Java e C++
### Java
Tutti i metodi non-statici sono virtuali, non serve mettere la keyword `virtual`. Se non si vuole rendere virtuale si usa la keyword `final` (vale anche per le classi).

Serve tuttavia la **keyword `@Override` per fare l'override di un metodo nella sottoclasse**.

### C++
Bisogna dichiarare esplicitamente i metodi virtuali con `virtual`. Non c'è keyword `final`. Senza `virtual` il **late-binding semplicemente non viene realizzato**.

In C++ sono **necessari i puntatori**[^2]! Altrimenti non si potrebbe fare l'overriding! Infatti C++, in un caso come `Animal a = *new Dog()` esegue le seguenti operazioni:
1. cerca l'operatore di assegnamento tra `Animal` e `Dog`;
2. se non lo trova cerca la funzione di copia di struttura definita dall'utente;
3. se non trova neanche quella, fa la _copia bitwise_, copiando `Dog` in `Animal` --> il comportamento è impredicibile perché `Dog` è più grande!
	- se invece si copiasse `Animal` in `Dog` sarebbe giusto, perché `Animal` è più piccolo

## Referenze