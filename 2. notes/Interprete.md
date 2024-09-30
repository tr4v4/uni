---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 22-09-2024 21:44:59
links:
  - "[[Lecture 17092024110611]]"
---
# Interprete
---
## Introduzione
> L'**interprete** è il componente che _interpreta le istruzioni_ di una [[Macchina astratta|macchina astratta]], ed è costituito da:
> 1. operazioni per l'_elaborazione dei dati primitivi_;
> 2. operazioni e strutture dati per il _controllo della sequenza di esecuzione delle operazioni_;
> 3. operazioni e strutture dati per il _controllo del trasferimento dei dati_;
> 4. operazioni e strutture dati per la _gestione della memoria_.

![[interprete.png]]

<u>Nota bene</u>: la struttura dell'interprete è la stessa per ogni macchina astratta, ciò che cambia sono i suoi diversi componenti.

Per esempio, nel caso in cui la macchina astratta in questione sia la [[Macchina fisica|macchina fisica]], allora gli elementi dell'interprete sono rispettivamente:
1. controllo e sfruttamento dell'[[ALU]];
2. incremento del [[PC]] e gestione dei [[Salto informatico|salti]];
3. gestione dei [[Modalità di indirizzamento|metodi di indirizzamento]];
4. indirizzamento e trasferimento dei blocchi.

## Referenze