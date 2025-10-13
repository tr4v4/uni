---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 06-10-2025 14:29:43
links:
  - "[[Lecture 06102025105214]]"
---
# OOD
---
## Introduzione
> Per **OOD** (**Object-Oriented Design**) si intende lo studio del [[Design di sistemi software|design di un sistema software]].

A differenza della [[OOA]] (Object-Oriented Analysis), nella fase di design si _aumenta il livello di dettaglio_.

## Temi
Nella OOD si trattano:
- _scomponibilità_ - come posso scomporre un problema grande in tanti sottoproblemi più semplici da risolvere
	- non sempre è possibile farlo!
		- [[Divide et impera|divide et impera]] dei romani, ha funzionato soltanto in una battaglia (orazi e pugliazzi...) per Albalonga
	- presuppone quindi che un problema possa essere scomposto
	- per questo dobbiamo prendere il problema non nella sua generalità
- _componibilità_ - poter crescere, iterazione dopo iterazione, un sistema fino a renderlo più ampio
	- questo è uno dei motivi per cui occorre essere semplici nel design del sistema
- _comprensibilità_ - il sistema dev'essere leggibile, la miglior documentazione è il codice scritto bene
	- dopo debugging di solito non si aggiorna la documentazione...
- _continuità_ - il codice va prodotto in modo incrementale
- _protezione_ - il codice va prodotto in modo protetto --> eventuali errori non si devono propagare
	- torna il low coupling
	- nei sistemi operativi si ha alto coupling --> per esempio la variabile condivisa `errno`

## Diagrammi
Si hanno ancora i [[Diagramma delle classi|diagrammi delle classi]] e [[Diagramma degli oggetti|diagrammi degli oggetti]], ma sono raffinati per dare riferimento al design del sistema. In più, si presentano i:
- _diagrammi comportamentali_, di cui
	- diagrammi di interazione, in particolare i [[Diagramma delle sequenze|diagrammi di sequenza]];
	- [[Diagramma di stato|diagrammi degli stati]];
	- [[Diagramma delle attività|diagrammi delle attività]];

## Referenze