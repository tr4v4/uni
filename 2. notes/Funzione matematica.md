---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/analisi-I
  - topic/logica-per-informatica
date: 18-09-2023 21:42:25
links:
  - "[[Lecture 18092023093106]]"
  - "[[Lecture 28092023090721]]"
---
# Funzione matematica
---
## Definizione
> Una funzione di dominio $D$ e codominio $C$ è una qualunque [[Relazione|relazione]]
> $$f \subseteq D \times C$$
> tale che
> $$\forall X, (X \in D \implies \exists! Y, X f Y)$$
> 
> Una **funzione**/**mappa**/**corrispondenza** si dice allora definita da una _terna_
> $$(D, C, f)$$
> per cui
> $$f: D \to C$$
> dove:
> - $D$ è il _dominio_
> - $C$ è il _codominio_
> - $f$ è la _legge di associazione_

Per indicare $dfc$ e dire quindi $(d, c) \in f$, si usa la notazione
$$f(d)=c$$
dove
$$d \in D, c \in C$$

Si dice anche che $c$ sia **[[Immagine di funzione|immagine]]** di $d$ tramite $f$.

<u>Nota bene</u>: è quindi importante ricordare che una funzione non si definisce solo dalla sua legge, ma anche dagli insiemi _dominio_ e _codominio_. Infatti, due funzioni si dicono uguali se hanno:
- stesso dominio
- stesso codominio
- stessa legge

### Regola fondamentale
Una funzione, per essere considerata tale, deve rispettare la seguente legge:
$$\forall d \in D, \exists! c \in C : f(d) = c$$
il che significa che **ad ogni elemento del dominio deve corrispondere un solo elemento del codominio tale che la legge di associazione soddisfi l'uguaglianza**.
![[funzione-matematica.png]]

## Proprietà
- [[Funzione iniettiva]]
- [[Funzione suriettiva]]
- [[Funzione biiettiva]]
- [[Funzione inversa]]
- [[Grafico di una funzione]]
- [[Parità di una funzione]]
- [[Disparità di una funzione]]
- [[Spazio di funzione]]

## Referenze