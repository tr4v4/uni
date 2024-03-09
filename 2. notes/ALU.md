---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 22-09-2023 19:22:55
links:
  - "[[Lecture 20092023151652]]"
---
# ALU
---
## Introduzione
> La **ALU** (_Arithmetic Logic Unit_) è una delle principali componenti della [[CPU]] che ha il compito di _eseguire le operazioni_, come [[AND]], [[OR]], addizione, ecc.

Quella zona della CPU che comprende ALU e [[Registro|registri generali]] (quindi i suoi _input_ e _output_) viene chiamata **Data Path**.
![[data-path.png]]
In un **ciclo di data path** i valori scritti nell'_ALU output register_ si riscrivono nel registro del risultato (in cima a quelli generali). Questo suddetto ciclo è governato da un [[Clock|clock]].

## Referenze