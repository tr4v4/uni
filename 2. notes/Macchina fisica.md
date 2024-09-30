---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 22-09-2024 22:06:57
links:
  - "[[Lecture 17092024110611]]"
---
# Macchina fisica
---
## Introduzione
> Una _macchina fisica_ si concretizza nell'[[Architettura di von Neumann|architettura di Von Neumann]]: prevede parti fisiche ([[Memorie|memoria]], [[CPU]], bus, [[I-O]]), e il [[Ciclo di fetch-decode-execute|ciclo di fetch-decode-execute]] che esegue istruzioni all'infinito. Ogni macchina fisica esegue operazioni appartenenti a uno _specifico e preciso set di istruzioni_ ([[ISA]]), o in poche parole: **una macchina fisica esiste per eseguire il suo [[Linguaggio macchina|linguaggio]]**.

Il linguaggio di una macchina fisica è indissolubile da essa perché è parte stesso dell'architettura. Infatti una macchina fisica altro non è che un "_algoritmo a fili_" capace di eseguire programmi scritti in un unico linguaggio: il **linguaggio macchina**[^1].

## Macchina fisica come macchina astratta
La _macchina fisica_ può essere vista come _la [[Macchina astratta|macchina astratta]] più concreta_, ossia quella in cui la memoria è quella fisica, le operazioni sono quelle eseguibili direttamente dalla CPU e l'**interprete è il ciclo di fetch-decode-execute**!

### Microprogrammazione
Alcune macchine fisiche (non [[CISC e RISC|RISC]]) sono [[Microprogrammazione|microprogrammate]], per cui si ha che:
- il ciclo FDE non è realizzato in hardware;
- ogni istruzione $\in L_{M_{F}}$ è realizzata mediante istruzioni di livello più basso, le $\mu$istruzioni, interpretate da un $\mu$[[Interprete|interprete]].

Assumiamo $L_{M_{F}}$ come il linguaggio macchina della macchina fisica $M_{F}$, e $L_{M_{APF}}$ come il linguaggio della $\mu$macchina $M_{APF}$, allora si avrà che:
1. il programma scritto in $L_{M_{F}}$ viene interpretato da un interprete scritto in $L_{M_{APF}}$;
2. a sua volta il programma, ora composto da $\mu$istruzioni, viene eseguito dal $\mu$interprete di $M_{APF}$.

## Referenze
[^1]: attenzione: _per linguaggio macchina qui si intende linguaggio macchina fisica_
[^1]: non è [[Assembly]], ma proprio le stringhe di bit