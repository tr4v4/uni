---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 10-03-2024 21:59:32
links:
  - "[[Lecture 07032024091439]]"
---
# Prototipo vs Implementazione
---
## Introduzione
> Il modello **prototipo vs implementazione**, nel campo della [[Programmazione|programmazione]] e delle [[Struttura dati|strutture dati]], è un modello astratto di visione concettuale che tenta di _separare i dettagli implementativi di un qualunque oggetto da come esso interagisce con l'esterno_.

E' molto simile al [[Principio di astrazione-implementazione|principio di astrazione-implementazione]], e si sposa perfettamente con le [[Interfaccia|interfacce]] di [[Java]].

### Esempio
Le classi `ArrayList` e `LinkedList` in Java sono implementazioni differenti dello stesso prototipo di [[Lista|lista]]. Offrono gli stessi metodi e attributi al programmatore nascondendo i dettagli implementativi, ma possono avere efficiente diverse a seconda dei problemi su cui sono applicate.

Si prenda come caso di studio la struttura dati [[Dizionario|dizionario]].

## Referenze