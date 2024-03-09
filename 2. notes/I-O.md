---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/architettura-degli-elaboratori
date: 22-09-2023 19:09:21
links:
  - "[[Lecture 20092023151652]]"
  - "[[Lecture 25092023130405]]"
---
# I-O
---
## Introduzione
I dispositivi di input e output, anche dette **periferiche**, interagiscono con l'elaboratore per mezzo di speciali _controllori_, che fungono da mediatore per l'invio e/o la ricezione di dati da un senso verso l'altro.

Alcuni controller accedono direttamente alla memoria attraverso il meccanismo [[DMA]] (Direct Memory Access), inviando al termine della scrittura/lettura un _[[Interrupt|interrupt]]_ alla [[CPU]].

### Esempi
- tastiera
- mouse
- monitor (richiede scheda video con [[GPU]])
- stampanti
- schede di rete

## Referenze