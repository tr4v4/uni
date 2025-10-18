---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-09-2025 18:11:37
links:
  - "[[Lecture 23042025111218]]"
---
# Covarianza e controvarianza
---
## Introduzione
Assumiamo di avere i 4 [[Tipo prodotto#Record|record]]:
```rust
type Animal: {
	name: string
}
type Dog: {
	name: string,
	bark: string
}

type AnimalHouse: {
	tenant: Animal
}
type DogHouse: {
	tenant: Dog
}
```

Sappiamo che `Dog` $<:$ `Animal` in larghezza (aggiunge un campo), e che `DogHouse` $<:$ `AnimalHouse` in profondita'.

In particolare si dice che `DogHouse` e `AnimalHouse` sono **covarianti** rispetto a `Dog` e `Animal`, perche' **mantengono la stessa direzione di sottotipaggio dei tipi di riferimento**.

Ma attenzione: possiamo usare `DogHouse` al posto di `AnimalHouse`, e quindi _in maniera covariante_, **SOLO in lettura**!

Invece, se vogliamo accedere in scrittura, dobbiamo usare `DogHouse` e `AnimalHouse` **in maniera controvariante**! Ossia nel senso opposto rispetto al sottotipaggio dei tipi di riferimento. Infatti possiamo dare `AnimalHouse` al posto di `DogHouse` se vogliamo scrivere nel campo `tenant` un `Dog`, perche' `AnimalHouse` vuole un `Animal`, e quindi `Dog` va bene.

### Con funzioni
Lo stesso ragionamento si puo' fare con i [[Tipo funzione|tipi funzione]]:
- se consumo (_input_) --> **controvariante**;
- se produco (_output_) --> **covariante**.

In particolare, i tipi funzione in consumo (il contesto richiede di dare un input a una funzione) sono controvarianti rispetto ai tipi di riferimento:
```rust
type A2B: Animal -> Bool
type D2B: Dog -> Bool
```

Si ha che `A2B` $<:$ `D2B`, quindi in controvarianza rispetto a `Dog` $<:$ `Animal` perche' se il contesto fornisce un `Dog` a `D2B`, possiamo sostituire `D2B` con `A2B` (in quanto `Dog` $<:$ `Animal`).

Invece i tipi funzione in produzione (cioe' quando il contesto si aspetta una funzione da cui avere un valore in output) sono covarianti rispetto ai tipi di riferimento:
```rust
type U2A: Unit -> Animal
type U2D: Unit -> Dog
```

Si ha che `U2D` $<:$ `U2A`, quindi in covarianza rispetto a `Dog` $<:$ `Animal` perche' se il contesto si aspetta un `Animal` come output di `U2A`, allora possiamo sostituire `U2A` con `U2B` in quanto questo restituisce un `Dog`, sottotipo di `Animal`.

## Rapporto
![[covarianza-controvarianza.png]]

Per le funzioni:
![[covarianza-controvarianza-2.png]]

## Esempi
### Record
Qui spieghiamo veramente il motivo per cui la covarianza e' pericolosa in scrittura nei record sottotipati, e quindi la ragione dietro all'introduzione della controvarianza, che nei tipi record e' implementata solo come un vincolo catturabile dal compilatore se si accorge che la struttura e' acceduta in scrittura.

Assumiamo
```rust
type Animal: {
	name: string
}
type Dog: {
	name: string,
	bark: string
}
type Cat: {
	name: string,
	meow: string
}

type AnimalHouse: {
	tenant: Animal
}
type DogHouse: {
	tenant: Dog
}
type CatHouse: {
	tenant: Cat
}
```

Ora facciamo:
```rust
AnimalHouse ah = new DogHouse();
print(ah.tenant.name);
```

Il compilatore lo accetta: infatti accediamo alla `AnimalHouse` in lettura, per cui `DogHouse` $<:$ `AnimalHouse` in covarianza con `Dog` $<:$ `Animal`.

Il problema comincia qui:
```rust
Cat c = { name: "Marco", meow: "Maiooo!" };
ah.tenant = c;
```

A questo punto, cosa contiene `AnimalHouse`? Sappiamo che in realta' e' un `DogHouse`, con campo `tenant` che contiene un `Dog`... Ma ora ci abbiamo appena assegnato un `Cat`! Abbiamo **messo un `Cat` all'interno di una `DogHouse`**!

Questo non dovrebbe succedere... E' per questo che il compilatore se si accorge che si accede ad `AnimalHouse` in scrittura, subito inverte il senso del sottotipaggio instaurando un regime di controvarianza!

<u>Nota bene</u>: nei tipi record la controvarianza non si nota tanto; e' solo un controllo fatto dal compilatore. Si nota invece molto nei tipi funzione!

### Funzioni
Assumiamo
```rust
type A2B: Animal → Bool
type D2B: Dog → Bool
```

E dimostriamo che serve la controvarianza `A2B` $<:$ `D2B`, ossia che possiamo solo sostituire una funzione di tipo `A2B` a una `D2B`.

Proviamo con la covarianza: immaginiamo che il codice si aspetti una funzione `A2B` ma che noi la sostituiamo con una di tipo `D2B` (covarianza). A questo punto il chiamante potrebbe fare
```rust
funzione_attesa(new Cat());
```
e rompere tutto! Infatti la funzione attesa e' `A2B` e accetta un `Cat`, ma assumendo valesse la covarianza l'abbiamo implementata come `D2B`, che sa gestire solo i `Dog`! Quindi abbiamo messo un `Cat` come input a una funzione che accetta i `Dog` --> errore!

Con la controvarianza ci basta sostituire una funzione `D2B` con una `A2B`. Questo funziona sempre, perche' il contesto passera' in input sempre un `Dog`, che essendo $<:$ `Animal` sara' sempre accettata dalla funzione di tipo `A2B`.


Assumiamo invece ora
```rust
type U2A: Unit → Animal
type U2D: Unit → Dog
```

Qui si capisce meglio: e' esattamente la situazione del `tenant` dei record di prima! Infatti leggere da una variabile e prendere l'output di una funzione e' assolutamente equivalente, quindi risulta ovvio che `U2D` $<:$ `U2A`, in covarianza!

## Java e C++
In [[Java]] e [[C++]] gli [[Array|array]] sono [[Generics|tipi parametrici polimorfi]], ma per ragioni storiche hanno reso le scritture e le letture covarianti!

Il sistema di tipi accetta quindi:
```java
Animal[] aa = new Dog[ 1 ];
aa[ 0 ] = new Dog(); // in consumo, usato come Array< ? super Dog >
Animal a = aa[ 0 ]; // in produzione, usato come Array< ? extends Dog >
aa[ 0 ] = new Cat(); // non dovrebbe compilare! E' sbagliato!
```

Tuttavia a runtime da' errore.

## Referenze