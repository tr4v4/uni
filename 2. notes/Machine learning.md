---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 25-09-2025 21:52:27
links:
  - "[[Lecture 25092025131144]]"
---
# Machine learning
---
## Introduzione

## Approccio
I passi che definiscono l'apprendimento automatico sono:
- definizione di un **modello** (una classe di funzioni[^1]) che dipende da un insieme di **parametri** $\Theta$;
- definizione di una **metrica di performance**, di solito una **funzione d'errore** (loss), per valutare il modello;
- tuning dei parametri $\Theta$ per **minimizzare** l'errore su un certo **training set**.

Di fatto il machine learning è un processo di ottimizzazione, ossia che risolve [[Problema di ottimizzazione|problemi di ottimizzazione]]. Eppure si chiama "learning" e non "optimizing" proprio perché:
1. si impara dal training set;
2. la soluzione non è analitica, ossia non c'è una formula chiusa per ottenere la soluzione, ma bisogna usare tecniche iterative che la approssimino --> questo processo di avvicinamento alla soluzione può essere visto come una forma di learning;

## Tasks
Le tipologie di machine learning sono:
- **supervised learning** - il dataset è formato da coppie $(input, output)$ (es. classificazione, regressione, ecc...);
- **unsupervised learning** - il dataset è formato da solo input (es. clustering, component analysis, autoencoding, ecc...);
- **reinforcement learning** - non c'è dataset, solo azioni e ricompense basate sulle azioni (es. learning long-term gains, "model-free" planning).

## Tecniche
Ci sono tantissimi modelli:
- [[Albero di decisione|alberi di decisione]]
- [[Modello lineare|modelli lineari]]
- [[Rete neurale|reti neurali]]

e tantissime funzioni d'errore:
- [[MSE|mean squared errors]]
- logistic loss
- cross entropy
- cosine distance
- maximum margin

## Relazioni
![[apprendimento-automatico-relazione-aree.png]]

## Referenze
- [[Features di un dato]]
- [[Deep learning]]

[^1]: per esempio i coefficienti di un polinomio