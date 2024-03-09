---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 24-10-2023 10:05:27
links:
  - "[[Lecture 19102023092110]]"
---
# Derivabilità di una regola di inferenza
---
## Introduzione
> Un'insieme di [[Regole di inferenza|regole di inferenza]] $\mathcal{R}$ si dicono **derivabili** a partire da un insieme di regole $\mathcal{S}$ quando per ogni regola in $\mathcal{R}$ le cui premesse sono $F_{1}, F_{2}, F_{3}, ..., F_{n}$ e la cui conclusione è $F$ si ha $F_{1}, F_{2}, F_{3}, ..., F_{n} \vdash F$ usando solamente le regole in $\mathcal{S}$.

Fondamentalmente la derivabilità ci consente di dimostrare che delle regole di inferenza sono [[Relazione di equivalenza|equivalenti]]. Per esempio è possibile dimostrare che le 2 [[Regole di inferenza dell'AND#Regole di eliminazione Eliminazione|regole di eliminazione dell'AND]] sono derivabili le une dalle altre.

## Teorema
> Se $\mathcal{R}$ è derivabile a partire da $\mathcal{S}$ allora per ogni dimostrazione ottenuta usando solo regole in $\mathcal{R}$ esiste una dimostrazione con le stesse premesse e conclusione che usa solo regole in $\mathcal{S}$.

## Referenze