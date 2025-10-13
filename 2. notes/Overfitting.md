---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 08-10-2025 18:27:00
links:
  - "[[Lecture 02102025131619]]"
---
# Overfitting
---
## Introduzione
> Per **overfitting** si intende quel fenomeno che avviene nel [[Machine learning|machine learning]] in cui _i modelli si allenano troppo su training set limitati, perdendo completamente la capacita' di generalizzare sui dati reali del problema_.
> Formalmente, fissata un'ipotesi (funzione) $h \in H$ ([[Spazio delle ipotesi|spazio delle ipotesi]]), e dati:
> - $error_{train}(h)$ come l'errore relativo sul training set,
> - $error_{\mathcal{D}}(h)$ come l'errore relativo sull'intero data set $\mathcal{D}$,
> 
> diciamo che $h$ **overfitta** il training set se esiste un'altra ipotesi $h'$ tale che
> $$error_{train}(h) < error_{train}(h')$$
> ma
> $$error_{\mathcal{D}}(h) > error_{\mathcal{D}}(h')$$

Il caso simmetrico e' l'[[Underfitting|underfitting]], in cui il modello e' troppo semplice e non cattura la natura del problema.

### Ottenere $\mathcal{D}$
Il vero problema alla base dell'overfit, ovviamente, e' la mancanza di $\mathcal{D}$: il data set reale. Se lo conoscessimo, _non ci sarebbe problema a fare overfit su di esso_!

Per simularlo, allora, si utilizza la seguente tecnica. Si suddivide il training set in 2/3 principali gruppi:
- **training set** vero e proprio;
- **validation set**, utilizzato per misurare l'accuratezza e overfitting;
- **test set**, per la valutazione finale.

Nel caso degli alberi di decisione, il _validation set si usa proprio per cercare di diminuire l'overfitting in fase di costruzione del modello_, applicando una delle regole che vedremo sotto.

## Casi specifici
### Albero di decisione
Prendiamo in esempio gli [[Albero di decisione|alberi di decisione]]. Nel loro caso la complessita' e' data dalla loro profondita', e vale che _piu' l'albero e' profondo, piu' riesce a modellare bene il training set_. Il problema, quindi, si pone quando si rende troppo profondo l'albero, e comincia a perdere di generalita': in questo caso _viene minimizzato l'errore sul training set, ma sul data set andra' malissimo_!
![[overfitting-e-complessità.png]]

Esistono delle tecniche per evitare l'overfitting degli alberi di decisione:
- [[Early stopping|early stopping]];
- [[Post-pruning|post-pruning]].

### Casi generici
Generalmente, per diminuire l'overfitting si usano le seguenti tecniche:
- [[Data augmentation|data augmentation]];
- [[Regolarizzazione|regolarizzazione]];
- [[Drop-out|drop-out]].

## Referenze