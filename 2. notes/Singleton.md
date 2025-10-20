---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 16:58:15
links:
---
# Singleton
---
## Introduzione
> Il **singleton** è un [[Design patterns creazionali|design pattern creazionale]] usato per creare un'unica istanza di una [[Classe|classe]]. Si usa proprio quando ci si vuole assicurare che di quella classe esiste uno e un solo oggetto.

## Implementazione
```Java
class Singleton {
	private static Singleton theInstance = null;
	
	private Singleton() {}
	
	public static Singleton getInstance() {
		if (theInstance == null)
			theInstance = new Singleton();
		return theInstance;
	}
}
```

## Osservazione
Ma _perché non possiamo semplicemente implementare il singleton attraverso una classe statica_? Perché perdiamo tutti i vantaggi della [[OOP]]!
Per esempio, una classe statica non può implementare delle [[Interfaccia|interfacce]]! Inoltre non puoi minimamente usare il [[Polimorfismo|polimorfismo]] di [[Sottotipaggio|sottotipo]].

## Referenze
- ricorda molto il concetto di [[Assioma del singoletto|singoletto]]