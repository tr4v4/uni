---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 02-12-2023 13:22:53
links:
  - "[[Lecture 29112023131955]]"
  - "[[Lecture 30112023091742]]"
---
# Strutture algebriche
---
## Introduzione
> Una **struttura algebrica** è una tupla (o ennupla) formata da
> - uno o più _[[Insieme|insiemi]]_ (chiamati _supporto_ o _sostegno_);
> - zero o più _elementi_;
> - zero o più _[[Funzione matematica|funzioni]]_ su tali insiemi (chiamate _operazioni_);
> - zero o più _[[Assioma|assiomi]]_ (chiamate _proprietà_) che devono essere soddisfatte.

Delle strutture algebriche ci interessa conoscere secondo quali possibilità è possibile preservare le loro proprietà durante la trasformazione dei dati: questo si chiama [[Morfismo|morfismo]], o [[Isomorfismo|isomorfismo]].

## Categorie
- [[Magma]]
- [[Semigruppo]]
- [[Monoide]]
- [[Gruppo]]
- [[Semianello]]
- [[Anello]]

![[diagramma-strutture-algebriche.png]]

### Proprietà
- [[Abelianità]]
- [[Sottoinsieme chiuso]]
- [[Sottostruttura algebrica]]

## Operazioni
### [[Prodotto cartesiano]]
Di due strutture algebriche è possibile fare il prodotto cartesiano. Si ha che infatti, prese due strutture algebriche $\mathcal{A}$ di sostegno $\mathbb{A}$ e $\mathcal{B}$ di sostegno $\mathbb{B}$ dello stesso tipo, il prodotto cartesiano $\mathcal{A} \times \mathcal{B}$ è la struttura algebrica dello stesso tipo t.c.:
- il sostegno è $\mathbb{A} \times \mathbb{B}$
- le costanti $e_{\mathcal{A} \times \mathcal{B}}$ sono [[Coppia ordinata|coppie]] $(e_\mathcal{A}, e_\mathcal{B})$
- le operazioni $\circ_{\mathcal{A} \times \mathcal{B}}$ agiscono applicando l'operazione corrispondente sugli elementi della coppia, ovvero $(x_{1}, y_{1}) \circ_{\mathcal{A} \times \mathcal{B}} (x_{2}, y_{2}) = (x_{1} \circ_\mathcal{A} x_{2}, y_{1} \circ_\mathcal{B} y_{2})$

## Referenze