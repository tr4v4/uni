---
tags:
  - category/note
  - status/finished
  - topic/
date: 26-09-2023 13:56:57
links:
  - "[[Lecture 26092023093828]]"
---
# Costante informatica
---
## Introduzione
Talvolta nella programmazione se si deve riscrivere il valore di un numero particolare più volte nel codice, al posto di inserirlo in una normale [[Identificatore|variabile]], se si sa che rimarrà invariato è preferibile dichiaralo come **costante**.

Una costante per essere tale deve seguire 2 regole:
- _dev'essere inizializzata nel momento in cui viene dichiarata_
- _non può mai cambiare valore_

## Dichiarazione
Le costanti si possono dichiarare in 2 modi in [[C++]]:
- `const`
	- si tratta di un'identificatore a tutti gli effetti, che sarà quindi allocato in memoria occupando spazio
	- se dichiarato dentro il main vale come variabile _locale_, se fuori come _globale_
- `#define`
	- è una direttiva per il _pre-processore_, che scansiona il codice e per ogni occorrenza rimpiazza il nome con il valore ad esso associato, non occupando alcuno spazio in memoria 

### Es.
#### `const`
```cpp
const double pi = 3.14;
```

#### `#define`
```cpp
#define PI 3.14
```

## Referenze