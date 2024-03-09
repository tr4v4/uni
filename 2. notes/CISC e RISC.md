---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/architettura-degli-elaboratori
date: 22-09-2023 19:57:37
links:
  - "[[Lecture 21092023130150]]"
---
# CISC e RISC
---
## Differenze
- **CISC** (_Complex Instruction Set Computer_)
	- con la [[Microprogrammazione|microprogrammazione]] si realizzano CPU in grado di compiere operazioni complesse
	- es. _fare somma tra due celle di RAM_
- **RISC** (_Reduced Instruction Set Computer_)
	- evita la microprogrammazione
	- istruzioni più semplici e quindi più veloci
	- es. _fare somma tra due registri_

Questo spiega come la [[Macchina multilivello#Elaboratore a 6 livelli|microarchitettura]] possa essere _implementata_:
- via **hardware** - con [[Circuiti combinatori|circuiti logici]] per insiemi fissati di istruzioni (RISC)
- via **software** - con la [[Microprogrammazione|microprogrammazione]] per costruire operazioni più complesse (CISC)

## Riflessione
> Dove è più semplice l'hardware, è più difficile il software;
> Dove è più semplice il software, risulta più complesso l'hardware.

## Referenze