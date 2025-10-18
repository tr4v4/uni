---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 11-10-2025 15:40:21
links:
  - "[[Lecture 07052025110754]]"
---
# Tipi esistenziali
---
## Introduzione
> I **tipi esistenziali** sono uno strumento della [[Teoria dei tipi|teoria dei tipi]] per fare _information hiding_. Consentono di implementare gli [[Tipi di dato astratto|ADT]] e gli [[Oggetti esistenziali|oggetti esistenziali]].

Un tipo come
```Rust
trait Counter { fn new…; fn get…; fn inc…; }
```
corrisponde al tipo esistenziale
$$CounterADT = \{\exists X. \{new: () \to X, get: X \to int, inc: X \to X\}\}$$
Infatti il tipo non vede il tipo concreto, ma assume che esista. Quindi si ottiene la [[Type safety|type safety]] senza conoscere l'implementazione, i dettagli interni, dei tipi.

Per esempio, dato il tipo esistenziale $CounterADT$, possiamo definire
$$\{Counter, c\} = \{*int, \{new = 1, get = fn(i:int)\{i\}, inc=fn(i:int)\{i+1\}\}\} \text{ as } CounterADT$$

Qui facciamo una serie di cose:
- definiamo un'implementazione concreta di $CounterADT$, ossia un puntatore a intero ($*int$);
- quindi definiamo l'implementazione concreta delle operazioni su quel tipo;
- specifichiamo che stiamo implementando il tipo esistenziale $CounterADT$;
- "spacchettiamo" l'ADT in $Counter$, il tipo che prende il posto del tipo concreto, e in $c$, il record delle operazioni del tipo $Counter$.

Una volta fatto lo spacchettamento, _$Counter$ rimarra' vincolato alla sua implementazione $*int$ per tutto il resto del programma_. Ma il programma vedra' solo il suo dato astratto $Counter$, non l'implementazione! E stessa cosa per $c$: il programma potra' accede ai metodi $c.new, c.get, c.inc$, ma non sapra' come sono implementati.

Ora, _potremmo sostituire l'implementazione dell'ADT senza incorrere in errori nel resto del codice che usa $Counter$ e $c$_! Infatti, **se anche cambiassimo l'implementazione con $*string$, il programma rimarrebbe type safe**: perche' lavora sui tipi astratti, e non direttamente con la loro implementazione concreta!

## Referenze
- [[Oggetti esistenziali]]