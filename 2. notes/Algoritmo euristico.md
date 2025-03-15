---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 23-02-2025 15:14:42
links:
  - "[[Lecture 19022025091652]]"
---
# Algoritmo euristico
---
## Introduzione
> Un **algoritmo euristico** determina una qualsiasi soluzione ammissibile al [[Problema|problema]] $\mathcal{P}$, quindi implicitamente calcolano:
> - un'approssimazione superiore del valore ottimo (se $\mathcal{P}$ e' di minimo);
> - un'approssimazione inferiore del valore ottimo (se $\mathcal{P}$ e' di massimo);

Non danno garanzie, e addirittura potrebbero concludere che non esiste una soluzione ammissibile anche se il problema non è vuoto ($\mathbb{F}_{\mathcal{P}} \neq \varnothing$).

## Metriche
Si utilizzano come metriche di valutazione di una soluzione data da un algoritmo euristico:
- _errore assoluto_ --> $$\upepsilon_{\mathcal{P}}(g) = |c_{\mathcal{P}}(g) - Z_{\mathcal{P}}|$$
- _errore relativo_ --> $$R_{\mathcal{P}}(g) = \frac{\upepsilon_{\mathcal{P}}(g)}{|Z_{\mathcal{P}}|} = \frac{|c_{\mathcal{P}}(g) - Z_{\mathcal{P}}|}{|Z_{\mathcal{P}}|}$$

Una soluzione $g$ si dice **$\epsilon$-ottima** se $$R_{\mathcal{P}}(g) \leq \epsilon$$
e un algoritmo euristico si dice **$\epsilon$-approssimato** se produce soluzioni $\epsilon$-ottime.

## Referenze