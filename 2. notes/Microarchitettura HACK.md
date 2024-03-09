---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 18-10-2023 10:52:17
links:
  - "[[Lecture 16102023125805]]"
  - "[[Lecture 18102023151217]]"
  - "[[Lecture 25102023150405]]"
---
# Microarchitettura HACK
---
## Introduzione
![[microarchitettura-hack.png]]

La [[Microarchitettura|microarchitettura]] HACK ([[CPU HACK]]) è una **macchina a 16-bit** molto simile a quella dei nostri computer: è solo, a parità di cicli di [[Clock|clock]], _estremamente più lenta perché non ottimizzata_. Essa dipende, ovviamente, dal linguaggio [[Assembly|assembly]] ([[ISA]]) con cui è implementata.

## Componenti
Sono presenti rispettivamente:
- [[ALU]] ([[ALU HACK]])
	- il secondo input può essere il registro `A` oppure un dato proveniente dalla [[RAM]]
- un [[Registro#Registri generali|registro generale]] `D`, che contiene uno dei due operandi della ALU e può memorizzare un precedente output
- un altro registro generale `A`, che contiene un dato che fa parte delle istruzioni, un precedente output o è utilizzato per puntare a un indirizzo di memoria
- un [[PC]], cui valore può essere impostato dal registro `A` (in caso di _salto_)

Il flusso di dati tra tutte queste componenti è regolato da [[Multiplexer]] e _bit di controllo_ (segnati con `c`): il tutto è **gestito da una microarchitettura composta da [[Circuiti combinatori|circuiti combinatori]]**.
Infatti il [[Ciclo di fetch-decode-execute|ciclo di fetch-decode-execute]] viene eseguito in un solo ciclo di clock: l'istruzione in ingresso al tempo `t` viene completamente eseguita al tempo `t+1`.

<u>Nota bene</u>: il bus indicato con `writeM` è il `load` della [[RAM]] (a `1` quando si scrive, a `0` quando si legge).

## Vantaggi e svantaggi
L'utilizzo di soli due registri generali `D` e `A`, pur semplificando l'architettura della ALU, di certo complica molto l'implementazione di alcune istruzioni di alto livello. Per esempio, _l'unica maniera per salvare risultati temporanei della ALU sarebbe quella di utilizzare celle di RAM "innocue"_.

## Referenze