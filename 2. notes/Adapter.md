---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 17:10:49
links:
---
# Adapter
---
## Introduzione
> L'**adapter** è un [[Design patterns strutturali|design pattern strutturale]] usato per separare l'interfaccia di una classe dalla sua reale implementazione, _risolvendo i mismatch di nomi_.

Pensiamo al seguente caso. Abbiamo un client, che ha $n$ oggetti target su cui vuole fare delle richieste, ossia eseguire un particolare metodo. Se **ognuno di questi target ha un nome di questo metodo diverso, il client dovrebbe fare lui una distinzione dei nomi dei metodi da invocare sulla base del tipo di target**. Questo non ci piace. Allora, creiamo un "adattatore", che fa questo lavoro per il client.

Spesso viene usato quando si vuole **unire due interfacce incompatibili**. Per esempio quando si vogliono interfacciare sistemi già esistenti.

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
- con [[Ereditarieta' multipla|ereditarietà multipla]] ![[adapter-mul-uml.png]]
- senza ereditarietà multipla ![[adapter-uml.png]]

## Referenze