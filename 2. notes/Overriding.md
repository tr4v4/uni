---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
  - topic/linguaggi-di-programmazione
date: 22-09-2025 14:07:54
links:
  - "[[Lecture 22092025100902]]"
  - "[[Lecture 23042025111218]]"
---
# Overriding
---
## Introduzione
L'overriding nasce dalla necessità dei programmatori di **determinare il comportamento degli oggetti il più tardi possibile**, se possibile addirittura a run-time.

Questo è in linea con le metodologie "agili": _le specifiche del cliente si definiscono iterazione dopo iterazione_[^1]. Per questa ragione le funzioni virtuali sono un modello elegante e flessibile per gestire il cambiamento delle specifiche del cliente.

Data la sua vicinanza al concetto di [[Ereditarietà|ereditarieta']][^4], di solito si usa molto nei [[Linguaggio di programmazione orientato a oggetti|linguaggi orientati agli oggetti]].

## Definizione
> Una **funzione virtuale** è un metodo di una classe che può essere _ridefinito in una classe derivata_. Tale ridefinizione è chiamata **overriding**, o **[[Polimorfismo|polimorfismo]] di sottotipo**.
> Si basa sulla [[Relazione|relazione]] binaria $<:$, tale per cui $S <: T$ significa "$S$ sottotipo di $T$" o "$S$ specifica $T$". Infatti $S$ e' un tipo piu' specifico di $T$ e possiamo quindi usare $S$ in qualsiasi posto che necessiti $T$[^3].

Un tipico esempio e' il tipo `Animale` e i suoi sottotipi `Gatto` e `Cane`. Possiamo usare tipi `Gatto` e `Cane` qualora ci fosse bisogno di un `Animale`.

### Relazione $<:$
Di solito $<:$ e' un **preordine**, ossia e' [[Riflessività di una relazione|riflessivo]] e [[Transitività di una relazione|transitivo]], ma non [[Simmetria di una relazione|simmetrico]]. Anzi, e' spesso [[Antisimmetricità di una relazione|antisimmetrico]], e quindi un **preordine parziale**! Ossia $S <: T \land T <: S \implies S = T$. Proprio per questo dove e' necessario `Gatto` non possiamo metterci `Animale` (perche' `Gatto` e' piu' specifico).

### Condizioni
L'overriding avviene se:
- il metodo sovrascritto è _virtuale_ (di solito lo sono di base se non diversamente specificato);
- il metodo nuovo ha la _stessa firma_ e lo _stesso tipo di ritorno_ del metodo.

<u>Nota bene</u>: si sa solo a run-time quale metodo verrà eseguito!

<u>Nota bene</u>: i metodi statici non possono essere sovrascritti.

## Fenomeni
Il polimorfismo di sottotipo puo' essere letto in **larghezza** o in **profondita'**.

### Sottotipaggio in larghezza
Per sottotipaggio in larghezza si intende il caso in cui _i record dei sottotipi aggiungono piu' campi dei loro supertipi_.

Immaginiamo i seguenti [[Tipo prodotto#Record|record]]:
```rust
type Animal: {
	name: string
}
type Dog: {
	name: string,
	bark: string
}
```

Allora `Dog` $<:$ `Animal`, e il sottotipaggio e' in larghezza: aggiunge un nuovo campo `bark`.

### Sottotipaggio in profondita'
Per sottotipaggio in profondita' si intende il caso in cui _avviene una sostituzione dei tipi dei campi del sottotipo_.

Immaginiamo i seguenti record:
```rust
type AnimalHouse: {
	tenant: Animal
}
type DogHouse: {
	tenant: Dog
}
```

Allora `DogHouse` $<:$ `AnimalHouse` in profondita', ovviamente perche' `Dog` $<:$ `Animal`!

### Relazione
La relazione tra sottotipaggio in larghezza e in profondita' e' studiato nella [[Covarianza e controvarianza|covarianza e controvarianza]]. L'atto di decidere se $S <: T$ si chiama [[Sussunzione|sussunzione]].

## Soluzioni
Per implementare a questo punto una funzione generica `max` tale che sia la piu' generica possibile, possiamo scrivere:
```rust
Integer <: Float
max( Float i, Float j ) -> Float { … }
```

Il problema di questa soluzione e' che all'interno di `max` perdiamo informazioni sui sottotipi, aka `Integer`, e soprattutto restituiamo solo `Float` (valore del super-tipo), e non quello specifico chiamato (per esempio `Integer`). Bisogna forzare il [[Casting di tipo|casting]]!

Possiamo allora fare:
```rust
Integer <: Comparable
Float <: Comparable
max( Comparable i, Comparable j ) -> Comparable { … }
```

Qui perdiamo ancora di piu', e si pone lo stesso problema del casting forzato.

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

### C++
Bisogna dichiarare esplicitamente i metodi virtuali con `virtual`. Non c'è keyword `final`. Senza `virtual` il **late-binding semplicemente non viene realizzato**.

In C++ sono **necessari i puntatori**[^2]! Altrimenti non si potrebbe fare l'overriding! Infatti C++, in un caso come `Animal a = *new Dog()` esegue le seguenti operazioni:
1. cerca l'operatore di assegnamento tra `Animal` e `Dog`;
2. se non lo trova cerca la funzione di copia di struttura definita dall'utente;
3. se non trova neanche quella, fa la _copia bitwise_, copiando `Dog` in `Animal` --> il comportamento è impredicibile perché `Dog` è più grande!
	- se invece si copiasse `Animal` in `Dog` sarebbe giusto, perché `Animal` è più piccolo

## Referenze

[^1]: la comprensione è incrementale...
[^2]: in realtà anche in Java si usano i puntatori
[^3]: [[Principio di sostituzione di Liskov|principio di sostituzione di Liskov]]
[^4]: non e' la stessa cosa, ma una sua raffinazione!
