---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 07-09-2025 19:47:19
links:
---
# Parser LALR
---
## Introduzione
Abbiamo visto la potenza dei [[Parser LR|parser]] $LR(1)$, ma anche il fatto che anche per linguaggi di media grandezza possano venire fuori [[Tabella di parsing LR|tabelle di parsing]] con centinaia di migliaia di righe (stati del [[DFA dei prefissi viabili]]).

Allora $LALR(1)$ cerca un buon compromesso tra la semplicita' (e compattezza) delle [[Tabella di parsing SLR(1)|tabelle]] $SLR(1)$ e la selettivita' di $LR(1)$.

Di base, si ottiene il parser LALR attraverso una riduzione della tabella di parsing $LR(1)$, costruendo la [[Tabella di parsing LALR(1)|tabella di parsing LALR(1)]].

## Referenze