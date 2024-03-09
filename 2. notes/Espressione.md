---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 26-09-2023 09:12:41
links:
  - "[[Lecture 25092023151613]]"
---
# Espressione
---
## Definizione
> Un'**espressione** è una _sequenza di operazioni che restituiscono un valore_.

### Composizione
Un'espressione può essere:
- una [[Identificatore|variabile]]
- una [[Costante informatica|costante]]
- una [[Funzione informatica|chiamata di funzione]]
- una combinazione di tutte quelle elencate sopra

In ogni caso, **il tipo di un'espressione è determinato dalle operazioni e dal tipo degli operandi**.

## Ordine di valutazione
Ci sono diversi criteri per i quali un'espressione valuta l'ordine di esecuzione delle operazioni che contiene:
- parentesi
- precedenza tra operatori
- operatori con stessa precedenza
	- se binari (+, -, ...) da sx a dx
	- se unari (!, &, \*) da dx a sx
- per `&&` e `||` usa [[Short-circuit evaluation|short-circuit evaluation]]

## Referenze