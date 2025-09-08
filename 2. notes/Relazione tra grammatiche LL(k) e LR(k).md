---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 08-09-2025 16:18:36
links:
---
# Relazione tra grammatiche LL(k) e LR(k)
---
## Introduzione
Di seguito il diagramma che mette in relazione le [[Grammatiche LL(k)|grammatiche]] $LL(k)$ e le [[Grammatiche LR(k)|grammatiche]] $LR(k)$:
![[relazione-grammatiche-llk-lrk.png]]

## Teoremi
### Potenza di $LR(k)$
> E' importante notare che:
> $LR(0) \subset LR(1) \subset \cdots \subset LR(k)$;
> $LALR(0) \subset LALR(1) \subset \cdots \subset LALR(k)$;
> $SLR(0) \subset SLR(1) \subset \cdots \subset SLR(k)$;
> 
> ma soprattutto che
> $$SLR(k) \subset LALR(k) \subset LR(k)$$
> ovvero **le grammatiche $LR(k)$ sono le piu' generali di tutte**.

### Rapporto tra $LL(k)$ e $LR(k)$
> Come da diagramma, **ogni grammatica $LL(k)$ e' anche $LR(k)$, ma non vale il viceversa**.

### Ambiguita' e determinismo
> Se **$G$ e' $LL(k)$ oppure $LR(k)$, allora $G$ non e' [[Grammatica ambigua|ambigua]] e $L(G)$ e' [[Linguaggio libero deterministico|libero deterministico]]**.

Esistono ovviamente linguaggi non ambigui ma non deterministici, come $L = \{ww^{R} | w \in \{a, b\}^{*}\}$, che quindi non sono ne' $LL(k)$ ne' $LR(k)$.

## Referenze
- [[Relazione tra linguaggi LL(k) e LR(k)]]