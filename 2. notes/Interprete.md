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

## Definizione
> Un **interprete** è un programma scritto in [[Linguaggio di programmazione|linguaggio]] $L_{O}$ (ed eseguito dalla [[Macchina astratta|macchina astratta]] $M_{O}$) che realizza una [[Funzione parziale|funzione parziale]]
> $$I_{L}^{L_{O}} : (P_{r}^{L} \times D) \to D \ \ : \ \ I_{L}^{L_{O}}(P_{r}^{L}, \text{input}) = P^{L}(\text{input})$$

ovvero l'_interprete deve calcolare la [[Semantica|semantica]] corretta del programma_!
![[traduzione-interprete.png]]

Pros:
- _flessibilità_
- _facilità di realizzazione_
- _poca occupazione di memoria_

Cons:
- _scarsa efficienza di $M_{L}$_

Questo perché l'interprete decodifica ogni istruzione prima di eseguirla, per cui **al tempo di esecuzione va aggiunto quello di decodifica ogni qualvolta si incontri un'istruzione**: il _body di un ciclo viene decodificato tante volte quanto viene eseguito_!

## Referenze