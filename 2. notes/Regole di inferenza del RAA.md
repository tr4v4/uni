---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 15-11-2023 18:42:39
links:
  - "[[Lecture 09112023131356]]"
---
# Regole di inferenza del RAA
---
## Introduzione
Il **RAA** è la [[Regole di inferenza|regola di inferenza]] che ci permette di dimostrare la [[Tautologia|tautologia]] $\neg \neg A \implies A$, e anche [[Regole di inferenza di EM|EM]], rendendo completa la [[Logica classica|logica classica]]. Non ha [[Regole di introduzione|regole di introduzione]] né di [[Regole di eliminazione|eliminazione]], e si presenta così:
![[RAA.png]]

e si legge **per dimostrare $F$ assumiamo $\neg F$ e dimostriamo un assurdo**.

### [[Teorema di correttezza|Correttezza]]
Dalla definizione di correttezza dobbiamo dimostrare
$$\neg F \implies \bot \Vdash F$$
quindi, in [[Semantica classica#Definizione|semantica classica]] fissato un mondo $v$ abbiamo $\max \{1 - [[\neg F]]^{v}, [[\bot]]^{v}\} = \max \{1 - (1 - [[F]]^{v}), 0\} = \max\{[[F]]^{v}, 0\} = [[F]]^{v} = 1$, da cui $[[F]]^{v} = 1$.

**Qed**.

### [[Invertibilità di una regola di inferenza|Invertibilità]]
Dalla definizione di invertibilità dobbiamo dimostrare
$$F \Vdash \neg F \implies \bot$$
quindi, fissato un mondo $v$ abbiamo $[[F]]^{v} = 1$ e (da prima) $\max\{[[F]]^{v}, 0\}$ deve fare 1, ed essendo $[[F]]^{v} = 1$ si ha sempre 1 come risultato.

**Qed**.

## Differenze con [[Regole di inferenza del NOT|regole del NOT]]
Attenzione a **non confondere il RAA con la regola di introduzione del NOT**:
- _con il RAA per dimostrare $F$ assumiamo $\neg F$ per dimostrare l'assurdo_
- _con il NOT per dimostrare $\neg F$ dimostriamo che $F$ porta all'assurdo_

La matematica, che si fonda sulla logica classica, spesso confonde le due regole, ma c'è una grande differenza: **l'introduzione del NOT vale anche in altre logiche, mentre il RAA è unicamente applicabile alla logica classica**.

Infatti le dimostrazioni senza il RAA sono considerate **più pregiate**, perché valgono, per esempio, anche in [[Logica intuizionista|logica intuizionista]].

## Referenze