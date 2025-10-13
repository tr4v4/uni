---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-09-2025 15:29:20
links:
  - "[[Lecture 16042025110927]]"
---
# Coercizione di tipo
---
## Introduzione
> Per **coercizione di tipo** si intende la conversione _implicita_ di tipo canonica/arbitraria, da un [[Tipi di dato|tipo]] a un altro. Questo puo' avvenire solo se _i due tipi sono [[Compatibilita' di tipo|compatibili]]_!

Un esempio possibile e' una [[Funzione informatica|funzione]] `sum` che accetta due tipi `float`, e un programma che la [[Invocazione di procedura|invoca]] passandoci due `int`: il **[[Compilatore|compilatore]]/[[Interprete|interprete]] inserisce le conversioni necessarie in modo implicito**, senza sollevare alcun errore di compatibilita'.
```C
float x = 1 + 1.5;  // quell'1 diventa 1.0
printf("%f", x);    // --> 2.5
```

## Referenze