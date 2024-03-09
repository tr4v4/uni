---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 03-12-2023 16:34:12
links:
  - "[[Lecture 29112023092601]]"
---
# Classe informatica
---
## Introduzione
> Per **classe** in informatica, nell'ambito della [[OOP|programmazione a oggetti]], si intende un [[Tipi di dati|tipo di dato]] che _specifica come i suoi elementi, detti [[Oggetto informatico|oggetti]], possono essere creati e usati_.

Storicamente il primo [[Linguaggio di programmazione|linguaggio di programmazione]] ad aver introdotto il concetto di classe è stato [[Simula67]].

## Composizione
Una classe si compone di:
- _attributi_/campi, ovvero le [[Identificatore|variabili]] della classe
- _metodi_, le [[Funzione informatica|funzioni]] della classe, tra cui il _[[Costruttore|costruttore]]_

In poche parole **la classe estende il concetto di [[Strutture dati|struttura]]**, racchiudendo in un unico costrutto sintattico la _definizione dei valori_ (attributi) e delle _operazioni attuabili su quei valori_ (metodi).

### Esempio
```cpp
class Rectangle {
	public:
		int base;
		int altezza;

		int area() {
			return base*altezza;
		}
		int perimetro() {
			return (base+altezza)*2;
		}
}

int main() {
	Rectangle r;
	r.base = 10;
	r.altezza = 30;
	cout << r.area() << "\t" << r.perimetro() << endl;
	
	return 0;
}
```

## Utilità
Oggigiorno le classi sono il _mattone elementare per costruire grossi programmi_.

## Referenze