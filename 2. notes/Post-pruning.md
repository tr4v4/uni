---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 08-10-2025 18:49:30
links:
  - "[[Lecture 02102025131619]]"
---
# Post-pruning
---
## Introduzione
> Il **post-pruning** e' una tecnica usata per evitare l'[[Overfitting|overfitting]] degli [[Albero di decisione|alberi decisionali]].

## Funzionamento
L'idea di base e' quella di **costruire l'intero albero**, terminando il training set, **per poi potarlo all'indietro**.

Formalmente:
1. costruisco l'intero albero per il training set;
2. ripeto la seguente operazione finche' ogni ulteriore pruning non migliora l'accuratezza della predizione:
	1. per ogni sottoalbero valutare, usando il validation set, l'impatto della sua rimozione sull'accuratezza della classificazione;
	2. effettuare (in modo [[Algoritmi greedy|greedy]]) il pruning del sottoalbero che ottimizza l'accuracy;

Questo contrasta l'overfit: _se migliora l'accuratezza dopo la potatura nel validation set, significa che l'albero era in overfitting nel training set_[^1].

## Referenze

[^1]: per la definizione stessa di overfitting!
