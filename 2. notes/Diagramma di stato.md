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
> Lo **stato** di un oggetto sono quelle _caratteristiche che permettono di definirne in modo univoco il suo comportamento_.

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
- _event_ - messaggio inviato, e' la specificazione di un'occorrenza che ha posizione nello spazio e nel tempo;
- _guard_ - condizione (`if`);
- _action_ - processi veloci e non interrompibili[^1];

La freccia si chiama _transizione_.

![[diagramma-di-stato-2.png]]
![[diagramma-di-stato-3.png]]

### Composti
Esistono anche i diagrammi composti:
![[diagramma-degli-stati-composto.png]]

Tra questi si ha che:
- _ogni transizione dal bordo dello stato composto a un altro stato parte in realta' da tutti i sottostati dello stato composto_;
- _si possono definire delle transizione da sottostato a stato_;

Questi sono utili per rappresentare la [[Concorrenza|concorrenza]], mediante una linea tratteggiata orizzontale che divide lo stato in due parti.

### Sincronizzazione
Questi diagrammi si possono unire a [[Diagramma delle attività|quelli delle attivita']]:
![[diagramma-degli-stati-sincronizzazione.png]]

## Referenze
- letteralmente sono dei [[DFA]]/[[NFA]]

[^1]: [[Azione atomica|azioni atomiche]]
