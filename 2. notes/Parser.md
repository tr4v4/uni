---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 19-08-2025 15:51:17
links:
  - "[[Lecture 24102024120228]]"
---
# Parser
---
## Introduzione
> Un **parser** costruito da [[YACC]] è fondamentalmente un [[DPDA]] che dalla lista di token prodotta dallo [[Scanner|scanner]] produce in output un [[Albero di derivazione|albero di derivazione]].

## Categorie
### Determinismo
I parser possono essere:
- **nondeterministici** --> se durante la ricerca di una [[Derivazione|derivazione]] si scopre che una scelta è improduttiva e non porta a riconoscere l'input, il parser fa _backtracking_, disfa parte della derivazione appena costruita e sceglie un'altra produzione, tornando a leggere l'input;
- **deterministici** --> leggono l'input una sola volta, ogni loro decisione è definitiva.

Entrambi _cercano di sfruttare informazioni dall'input per guidare la ricerca della derivazione_.

### Approccio
Poi, i parser possono essere:
- **top-down** --> ricostruiscono una [[Derivazione canonica sinistra|derivazione leftmost]] per $w$ a partire dal simbolo iniziale $S$ (all'inizio sulla pila);
- **bottom-up** --> ricostruiscono una [[Derivazione canonica destra|derivazione rightmost]] a partire da $w$ cercando di ridurla al simbolo iniziale $S$ (alla fine sulla pila).

In particolare vedremo:
- [[Parser top-down|parser top-down]] deterministici, ottenuti a partire da grammatiche $LL(k)$;
- [[Parser bottom-up|parser bottom-up]] deterministici, ottenuti a partire da grammatiche $LR(k)$ (in particolare $LR(0)$, $SLR(1)$, $LR(1)$, $LALR(1)$).

## Referenze