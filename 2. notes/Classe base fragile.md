---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 21-10-2025 11:33:25
links:
  - "[[Lecture 14052025105842]]"
---
# Classe base fragile
---
## Introduzione
> Per **classe base fragile** si intende, nel contesto della [[OOP]], un problema di _compatibilita' tra [[Sottotipaggio|sottoclassi]] e superclassi che hanno subito una modifica_.

Se `B::A` e `A` viene modificata, sara' necessario ricompilare anche `B` per _evitare di incorrere in errori spiacevoli_. Tuttavia questo non e' sempre possibile farlo: chi scrive `A` non ha sempre accesso a tutte le possibili sottoclassi `B`.

Si tratta a tutti gli effetti di un problema di [[Ingegneria del software|ingegneria del software]].

## Caso vtable
Applicato al caso delle [[VTable|vtable]], questo problema e' noto come **problema dell'interfaccia binaria fragile**. In generale, il problema dell'interfaccia binaria fragile si presenta solo per il modo in cui il compilatore rappresenta la gerarchia in memoria!
Assumiamo di essere nel seguente caso:
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
che sappiamo produrre le vtable associate a `o1` e `o2`:
![[vtable-1.png]]

Ora, se modifichiamo `A` aggiungendo un metodo `i`:
```Java
class A {
	int a;
	void f(){...}
	void g(){...}
	void i(){...}
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

e ricompiliamo solo `A`, avviene che **il metodo `h()` di `B` sovrascrive completamente `i()` di `A`**.
![[vtable-2.png]]

Questo avviene per il modo in cui funzionano gli offset calcolati nelle vtable: Se creo un nuovo oggetto `B`, questo copia la vtable di `A` (senza sapere nulla di `i` perche' non `B` non e' stato ricompilato), sovrascrive `f()`, eredita `g()` e aggiunge `h()` al terzo offset dove dovrebbe esserci `i()`.

## Soluzioni
Una soluzione proposta da [[Java]] e' il [[Dynamic Method Dispatch]], implementato dalla [[JVM]].

## Referenze