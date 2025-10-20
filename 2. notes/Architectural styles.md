---
tags:
  - category/note
  - status/pending
  - topic/ingegneria-del-software
date: 20-10-2025 19:13:35
links:
---
# Architectural styles
---
## Introduzione
> Per **architectural styles**, nel contesto dell'[[Architettura di sistemi software|architettura di sistemi software]], si intende la definizione di _7 famiglie di sistemi, in termini di pattern di strutture organizzative_. In particolare, ogni architectural style definisce:
> - un _vocabolario di componenti_;
> - dei _tipi di connettori_;
> - un _[[Insieme|insieme]] di vincoli_ e come questi si possono combinare.

## Stili
Ne esistono appunto 7:
- [[Pipes and filters]]
- [[Tipi di dato astratto|ADT]]
- [[Layering]] - letteralmente lo _schema a cipolla_, applicato per esempio molto nei [[Sistema operativo|sistemi operativi]]
- [[Invocazione implicita]] - anche detta _programmazione a eventi_, in cui i componenti presentano un'interfaccia con un insieme di procedure e un insieme di eventi
- [[Repositories]] - in cui c'è un sistema centrale di interscambio di informazioni e di centralizzazione del controllo; può essere a [[Database|database]], o a "blackboard"
- [[Interprete]] - in cui una [[Macchina virtuale|macchina virtuale]] è prodotta all'interno del software; un interprete include uno pseudoprogramma e l'_interpretation engine_
- [[Process control]]

## Referenze