---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 20-02-2025 10:06:58
links:
  - "[[Lecture 19022025111150]]"
---
# Ambiente
---
## Introduzione
> Per **ambiente** si intende l'_insieme dei [[Binding|bindings]] tra [[Nome|nomi]] e [[Oggetto denotabile|oggetti denotabili]] esistenti a run-time in uno specifico punto del programma ed in uno specifico momento dell'esecuzione_.

## Tipologie
In uno specifico [[Blocco|blocco]], l'ambiente e' suddiviso in:
- _ambiente locale_ --> associazioni create nel blocco (variabili locali e parametri formali);
- _ambiente non locale_ --> associazioni ereditate da altri blocchi;
- _ambiente globale_ --> ambiente non locale ma comune a tutti i blocchi, del blocco "supremo" (il più esterno).

## Operazioni
Su un ambiente, a run-time, sono svolte delle operazioni:
- _creazione_ --> basta la dichiarazione in un blocco (naming);
- _riferimento_ --> oggetto denotato tramite il suo nome (referencing);
- _disattivazione_ --> avviene quando c'è shadowing, ossia quando una dichiarazione maschera un nome;
- _riattivazione_ --> quando si esce dal blocco con la dichiarazione che maschera il nome;
- _distruzione_ --> quando si esce dal blocco con dichiarazione locale (unnaming);

<u>Nota bene</u>: c'e' una sorta di simmetria tra _creazione/disattivazione_ e _riattivazione/distruzione_.

## Referenze