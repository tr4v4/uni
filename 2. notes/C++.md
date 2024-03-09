---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/programmazione
date: 20-09-2023 19:18:37
links:
  - "[[Lecture 20092023091613]]"
  - "[[Lecture 26092023093828]]"
---
# C++
---
## Storia
Nasce come estensione di [[C]] con oggetti, sviluppato nel 1983 ai Bell Labs.

## Main

## Librerie
Le principali [[Libreria|librerie]] di C++ sono:
- `iostream`
- `cmath`
- `cstdlib`
- `ctime`

### iostream
Per poter stampare a schermo o richiedere input dall'utente è necessario importare la libreria `iostream` per utilizzare le funzioni `cout` e `cin` facenti parte del [[Namespace|namespace]] `std`.

In questo modo:
```cpp
#include <iostream>

int main() {
	std::cout << "Hello World!" << std::endl;
	return 0;
}
```
(_o utilizzando il comando `using` per usare `std` e rendere meno verboso il codice_)

#### `<<`
Operatore "componibile" che redireziona lo stream di destra a sinistra, accoppiato di solito con `cout`. Si possono redirezionare più output in sequenza, rispettando sempre la [[Espressione|precedenza degli operatori]].

#### `>>`
Operatore sempre "componibile" che redireziona lo stream di sinistra a destra, accoppiandolo con `cin`. Si possono redirezionare più input in sequenza, ma bisogna tener conto che `cin` si adatterà a seconda del tipo di [[Identificatore|identificatore]] che gli viene posto all'ingresso.

##### Es.
```cpp
char x;
int y;
cin >> x >> y;
```

Essendo `x` un `char` (che occupa _1 byte_), di una qualsiasi stringa inserita in ingresso verrà presa in considerazione il primo carattere: la parte restante sarà inserita in `y` (da _4 byte_).

### cmath
Contiene tutte le funzioni matematiche principali.
- `double abs(double)`
- `double sqrt(double)`
- `double pow(double, double)`
- `double cos(double)`
- `double sin(double)`

### cstdlib
Contiene tutte le funzioni necessarie alla generazione di numeri pseudo-casuali.
- `int rand()`
- `int srand(int)`
- `RAND_MAX`

#### Es.
```cpp
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
	srand(time(0));
	cout << rand() % 90 << endl;
	return 0;
}
```

dove:
- `srand(int)` inizializza il _seed_ (seme) di partenza del generatore
- `time(0)` è il numero di secondi passati a partire dal 1° gennaio 1970
- `rand()` genera un intero pseudo-casuale secondo un algoritmo

## Referenze