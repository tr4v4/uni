---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 24-03-2024 22:11:02
links:
  - "[[Lecture 21032024091145]]"
---
# Collisione hash
---
## Introduzione
> Una **collisione hash** è un _fenomeno inevitabile_ che avviene nel contesto delle [[Tabella hash|tabelle hash]] quando una _[[Funzione hash|funzione hash]] restituisce uno stesso valore di output per due chiavi $k_{1}, k_{2}$ differenti_.

Non si è in grado matematicamente di eliminarle, ma si possono e anzi devono limitare e gestire. Si pensi agli [[Attacco informatico|attacchi informatici]] basati sul cracking delle tabelle hash per provocare [[DoS]].

## Probabilità
La _probabilità_ di una qualsiasi funzione hash di generare una _collisione tra due chiavi è più alta di quanto si possa credere_: assumendo _hashing uniforme semplice_ ($\frac{1}{m}$), il problema delle collisioni è equivalente al [[Paradosso del compleanno|paradosso del compleanno]].

## Soluzioni
Esistono una serie di provvedimenti e tecniche che si utilizzano per mitigare il problema delle collisioni, tra cui:
- [[Concatenamento separato]]
- [[Indirizzamento aperto]]

## Referenze