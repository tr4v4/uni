---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-09-2025 17:12:52
links:
  - "[[Lecture 23042025111218]]"
---
# Overloading
---
## Introduzione
> Per **overloading** si intende un tipo di [[Polimorfismo|polimorfismo]] in cui _si "sovraccarica" la definizione di un'operazione su diversi tipi specifici_.

Sfrutta la capacita' del [[Compilatore|compilatore]]/[[Interprete|interprete]] del linguaggio di _distinguere dal contesto di chiamata definizioni alternative di operazioni con lo stesso nome_.

L'esempio piu' lampante sono gli operatore aritmetici: l'_operatore `+` fa un sacco di overloading_. Somma interi, float e in alcuni linguaggi anche [[Stringhe|stringhe]] (concatenazione): **cambia l'implementazione a seconda dei tipi degli operandi**.

Quindi il compilatore/interprete hanno bisogno di capire quale implementazione della funzione chiamare effettivamente! Come?

## Funzionamento
Nella pratica l'overloading e' un'abbreviazione sintattica che scompare non appena risolviamo l'invocazione. Di fatto l'overloading e' un meccanismo di **dispatch** (indirizzamento).

### Static dispatch
Se il dispatch viene fatto staticamente (a compile-time), _sostituiamo ogni simbolo sovraccaricato con un nome non ambiguo che denota la specifica implementazione_.

### Dynamic dispatch
Se invece viene fatto dinamicamente (a run-time), si capisce che implementazione eseguire mediante tabelle di ricerca.

### Legame con coercizione
**Overloading e [[Coercizione di tipo|coercizione]] vanno di pari passo**: `float x = 1 + 2.0` diventa mediante coercizzazione `float x = 1.0 + 2.0`, e quindi si utilizza la definizione di `+` per i float.

In altre parole, _e' la coercizione/[[Casting di tipo|casting]] a fornire le informazioni necessarie al compilatore/interprete per disambiguare l'implementazione overloaddata_.

## Esempi
### `max`
```java
int max(int i, int j) {
	return i > j ? i : j;
}
float max(float i, float j) {
	return i > j ? i : j;
}
```

## Referenze