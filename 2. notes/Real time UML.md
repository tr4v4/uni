---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 14-10-2025 12:24:49
links:
  - "[[Lecture 13102025151054]]"
---
# Real time UML
---
## Introduzione
Vogliamo estendere l'[[UML]] in modo che ci consenta di fare design di [[Sistema real-time|sistemi real-time]].

Le feature che supporta sono le seguenti:
- _change/time event_
	- `when` - keyword per specificare quando l'evento occorre e quindi quando passare di stato;
	- `after` - keyword per specificare dopo quanto tempo fare un'azione quando si è in un certo stato;
- _timing constraints_
	- `startTime`, `stopTime`, `executionTime`

E' stato introdotto [[ROOM]] che aggiunge stereotipi per specificare real time UML.

## Referenze