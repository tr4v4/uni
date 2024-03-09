---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 18-10-2023 10:53:43
links:
  - "[[Lecture 16102023125805]]"
  - "[[Lecture 06112023131103]]"
---
# CU HACK
---
## Introduzione
La **[[CU]] HACK** non è [[Microprogrammazione|microprogrammata]]: significa che _funziona a circuito_. La [[Microarchitettura HACK|sua microarchitettura]], quindi, prevede l'utilizzo di [[Circuiti combinatori|circuiti combinatori]].

## Input e output
- inputs:
	- [[ISA HACK#A-instruction|A-instruction]]
	- [[ISA HACK#C-instruction|C-instruction]]
- outputs:
	- _OP_ALU_ ([[Istruzioni ISA#Composizione|opcode]] della [[ALU HACK|ALU]])
	- _MUX_A_
	- _MUX_ALU_
	- _W_A_
	- _W_D_
	- _writeM_ ([[RAM#Implementazione|load]] della [[RAM]])
	- _W_PC_ (in caso di [[Salto informatico|salto]])

## Referenze