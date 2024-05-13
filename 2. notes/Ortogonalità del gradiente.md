---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 03-05-2024 20:48:23
links:
  - "[[Lecture 02052024141201]]"
---
# Ortogonalità del gradiente
---
## Introduzione
> Data $f: \mathbb{R}^{n} \to \mathbb{R}$ una [[Funzione a più variabili|funzione a più variabili]] e dato un suo [[Insieme di livello|insieme di livello]] $L_{b} = \{x \in \mathbb{R}^{n} | f(x) = b\}$, considero $\bar{x} \in L_{b}$ e suppongo di poter costruire una [[Curva|curva]] $r: ]-1, 1[ \to \mathbb{R}^{n}$ tale che
> 1. $r(t) \in L_{b} \ \ \forall t$
> 2. $r(0) = \bar{x}$
> 3. $r'(0) \neq \underline{0} \in \mathbb{R}^{n}$[^1]
> 
> allora ho che
> $$f(r(t)) = b \ \ \forall t \in ]-1, 1[ \ \ \implies \ \ \frac{\partial}{\partial t} f(r(t)) = 0 \ \ \forall t \ \ \implies \ \ < \nabla f(r(t)), r'(t) > = 0$$
> con l'ultimo passaggio giustificato dal [[Derivata lungo una curva|secondo teorema del gradiente]].
> Posto $t = 0$ ottengo
> $$< \nabla f(\bar{x}), r'(0) > = 0$$
> ed essendo allora il _[[Prodotto scalare|prodotto scalare]] tra il gradiente di $f$ in $\bar{x}$ e la derivata di $r(t)$ in $0$, ossia la tangente dell'insieme di livello nel punto $t = 0$, uguale a 0_, significa che **i due sono [[Ortogonalità|ortogonali]]**!

## Referenze
[^1]: ovvero che $r$ sia [[Curva regolare|regolare]] su $0$