---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 29-12-2023 12:18:32
links:
  - "[[Lecture 05122023161837]]"
---
# Proprietà dei connettivi
---
## Introduzione
I connettivi della [[Logica proposizionale|logica proposizionale]], compresi i [[Quantificatori|quantificatori]] della [[Logica del primo ordine|logica del prim'ordine]], rispettano una serie di proprietà. Di fatto, ricordando il concetto di [[Equivalenza logica|equivalenza logica]], si ottengono una serie di equivalenze su:
- _[[Implicazione|implicazione]]_ ($\implies$) --> [[Teorema di deduzione semantica|teorema di deduzione semantica]]
- _[[Sostituzione|sostituzione]]_ ($A/B$) --> [[Teorema di sostituzione|teorema di sostituzione]]
- _connettivi_ ($\land, \lor, \neg$)
- _quantificatori_ ($\forall, \exists$)

## Proprietà
### Connettivi
Rispecchiano le leggi dell'[[Algebra di Boole|algebra di Boole]]
- commutatività
- associatività
- idempotenza
- distributività
- assorbimento
- elemento neutro
- annichilamento
- doppia negazione
- [[Leggi di De Morgan|De Morgan]]
- risoluzione

<u>Attenzione</u>: alcune valgono solo per la [[Logica classica|logica classica]], altre anche per l'[[Logica intuizionista|intuizionista]].

### Quantificatori
- commutatività:
	- $\forall x, \forall y. P \equiv \forall y, \forall x. P$
	- $\exists x, \exists y. P \equiv \exists y, \exists x. P$
	- <u>attenzione</u>: non vale per quantificatori di tipo diverso
- distributività
	- $\forall x. (P \land Q) \equiv (\forall x. P) \land (\forall x. Q)$
	- $\exists x. (P \lor Q) \equiv (\exists x. P) \lor (\exists x. Q)$
	- $\forall x. P \equiv P \iff x \notin FV(P)$[^1]
	- $\exists x. P \equiv P \iff x \notin FV(P)$[^1]
	- $\forall x. (P \lor Q) \equiv (\forall x. P) \lor Q \iff x \notin FV(Q)$[^1]
	- $\exists x. (P \land Q) \equiv (\exists x. P) \land Q \iff x \notin FV(Q)$[^1]
- De Morgan
	- $\neg \forall x. P \equiv \exists x. \neg P$
	- $\exists x. \neg P \Vdash \neg \forall x. P$
	- $\neg \exists x. P \equiv \forall x. \neg P$
	- $\forall x. \neg P \equiv \neg \exists x. P$
- altre proprietà
	- $(∀x.P) ⇒ Q ≡ ∃x.(P ⇒ Q)$
	- $∃x.(P ⇒ Q) ⊩ (∀x.P) ⇒ Q$
	- $(∃x.P) ⇒ Q ≡ ∀x.(P ⇒ Q)$
	- $Q ⇒ (∃x.P) ≡ ∃x.(Q ⇒ P)$
	- $Q ⇒ (∀x.P) ≡ ∀x.(Q ⇒ P)$

## Referenze
[^1]: $FV(P)$ è la funzione definita per [[Ricorsione strutturale|ricorsione strutturale]] che calcola tutte le [[Variabile libera|variabili libere]] di $P$