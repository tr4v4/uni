---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 29-09-2025 22:21:14
links:
  - "[[Lecture 29092025103533]]"
---
# Diagramma dei casi d'uso
---
## Introduzione
> Il **diagramma dei casi d'uso** in [[UML]] è un diagramma degli [[Use case|use cases]] di un sistema software. E' in particolare il risultato dell'**[[Analisi dei requisiti|analisi dei requisiti]]** come raccoglimento di use cases.

![[diagramma-use-case-1.png]]

## Composizione
Un diagramma dei casi d'uso si compone di:
- **attori** - hanno il ruolo dell'utente, ma non devono per forza essere umani;
- **relazioni** - tra casi d'uso e casi d'uso;
	- _extends_ - quando uno use case è simile a un altro ma fa un po' di più
		- in particolare, ad ogni step ci si deve chiedere cosa potrebbe andare storto/diversamente
		- e quindi si estende lo use case con un suo caso limite, per ogni variazione possibile
	- _includes_ - quando ci sono alcune parti condivise nel comportamento di più use cases
		- serve per ridurre la duplicazione di comportamenti di use case diversi
- **casi d'uso**

## Referenze