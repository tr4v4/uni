---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 06-10-2025 15:05:25
links:
  - "[[Lecture 06102025105214]]"
---
# Diagramma di stato
---
## Introduzione
> I **diagrammi di stato** dimostrano _come un oggetto evolve nel suo stato e in che modo può cambiarlo_.

## Definizioni
### Stato
> Lo **stato** di un oggetto sono quelle _caratteristiche che permettono di definirne in modo univoco il comportamento di un oggetto_.

Nella [[OOP]] lo stato è composto dai campi dell'oggetto.

<u>Nota bene</u>: non tutti i campi sono fondamentali per definire lo stato... sono solo le caratteristiche rilevanti.

Nel diagramma [[UML]] lo stato si compone delle seguenti proprietà:
- _entry_ - azione da fare quando si entra in quello stato
- _do_ - attività da fare per tutta la durata dello stato, in costante funzionamento
- _on_ - azione da fare in un certo evento
- _exit_ - azione da fare quando si esce

## Diagramma
![[diagramma-di-stato-1.png]]

dove:
- _event_ - messaggio inviato;
- _guard_ - condizione (`if`);
- _action_ - processi veloci e non interrompibili[^1];

![[diagramma-di-stato-2.png]]
![[diagramma-di-stato-3.png]]

## Referenze

[^1]: [[Azione atomica|azioni atomiche]]
