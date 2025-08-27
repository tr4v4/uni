---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 19-08-2025 19:42:56
links:
  - "[[Lecture 05112024110833]]"
---
# Semplificazione delle grammatiche
---
## Introduzione
Il motivo per cui e' fortemente richiesta la semplificazione di una [[Grammatiche|grammatica]], riguarda l'efficienza e la possibilita' stessa di creare dei [[Automa a pila|PDA]] che ne riconoscano il [[Linguaggio generato|linguaggio generato]].

## Casi
Nella pratica, semplificare le grammatiche si traduce in:
1. **eliminare le produzioni-$\epsilon$** ($A \to \epsilon$), inadatte al [[Parser bottom-up|bottom-up parsing]] --> [[Produzioni epsilon|produzioni epsilon]];
2. **eliminare le produzioni unitarie** ($A \to B$), che possono creare cicli ($A \implies^{+} A$) --> [[Produzioni unitarie|produzioni unitarie]];
3. **eliminare simboli inutili**, ossia terminali/nonterminali non raggiungibili/generabili a partire da $S$ --> [[Simboli inutili|simboli inutili]];
4. **eliminare le ricorsioni sinistre** ($A \to A\alpha$), inadatte al [[Parser top-down|top-down parsing]] --> [[Ricorsione sinistra|ricorsione sinistra]];
5. **fattorizzare la grammatica**, per ottenere grammatiche con meno nondeterminismo nel top-down parsing --> [[Fattorizzazione a sinistra|fattorizzazione a sinistra]].

## Forme normali
Studiamo ora delle forme di grammatiche standard che garantiscono certe proprieta':
- [[Forma normale di Chomsky|forma normale di Chomsky]];
- [[Forma normale di Greibach|forma normale di Greibach]].

## Referenze