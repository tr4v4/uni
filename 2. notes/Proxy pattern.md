---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 18:14:36
links:
---
# Proxy pattern
---
## Introduzione
> Il **proxy** è un [[Design patterns strutturali|design pattern strutturale]] simile al [[Bridge pattern|bridge]], che cerca di nascondere l'implementazione di un oggetto reale e che si fa da "presentatore".

Sono usati per l'_accesso remoto_, per l'_accesso virtuale_ e per la _protezione_.

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[proxy-uml.png]]

Quindi, fondamentalmente, l'entità reale (che sia [[Classe|classe]] o [[Oggetto|oggetto]]), **si nasconde dietro al proxy, che implementa la stessa interfaccia, e contiene l'entità**.

## Referenze