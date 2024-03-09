---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 28-10-2023 12:44:24
links:
  - "[[Lecture 25102023150405]]"
  - "[[Lecture 02112023130607]]"
---
# ISA
---
## Introduzione
> L'**ISA** (_Instruction Set Architecture_) indica di una specifica [[Microarchitettura|microarchitettura]] l'_insieme delle istruzioni software eseguibili dall'hardware_.

Prendendo come riferimento il concetto di [[Macchina multilivello|macchina multilivello]], il livello ISA si occupa di **interfacciare l'hardware con il software**, associando (a seconda del tipo di microarchitettura) istruzioni di basso livello software a "comandi" computabili dalla [[CPU]].

![[livello-isa.png]]

Ogni microarchitettura ha il suo _instruction set_, cucito su misura per quel particolare processore[^2].

### Workflow
1. dai livelli superiori l'ISA riceve programmi ad alto livello
2. li traduce attraverso il [[Compilatore|compilatore]] in istruzioni di basso livello ([[Assembly|assembly]])
3. le traduce attraverso l'[[Assemblatore|assemblatore]] in [[Codice binario|codice binario]] eseguibile dalla CPU
[^1]

## Referenze
- [[ISA HACK]]
- [[Istruzioni ISA]]

[^1]: vedi [[Workflow di compilazione|workflow di compilazione]]
[^2]: si veda il dibattito [[CISC e RISC]]