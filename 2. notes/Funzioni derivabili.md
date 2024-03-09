---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-10-2023 22:25:38
links:
  - "[[Lecture 23102023094009]]"
  - "[[Lecture 27102023135003]]"
  - "[[Lecture 06112023094954]]"
---
# Funzioni derivabili
---
## Introduzione
I presupposti teorici necessari a comprendere le funzioni derivabili sono il concetto di [[Funzioni monotone|funzione monotona]] e di [[Derivata|derivata]].

## Definizione
> Una [[Funzione matematica|funzione]] si dice **derivabile** in un [[Punto interno|punto interno]] $x_{0}$ del dominio se il limite del [[Derivata#Definizione|rapporto incrementale]] _esiste_ ed è _finito_. Ovvero
> $$\exists \lim_{h \to 0} \frac{f(x_{0} + h) - f(x_{0})}{h} \in \mathbb{R}$$

Se vale, allora esso si indica con $f'(x_{0})$, o $\frac{df}{dx}(x_{0})$ o $Df(x_{0})$.

## Regola
Analogamente a quanto avviene per la verifica della [[Funzioni continue#Regola|continuità]] di una funzione in un punto, anche la derivabilità di un punto interno $x_{0}$ è determinata dai risultati dei [[Limite destro e sinistro di funzione|limiti destro e sinistro]] della derivata: _se essi coincidono e sono uguali alla derivata della funzione per quel punto allora la funzione è derivabile in quel punto_.

Quindi si ha
$$f \text{ derivabile in } x_{0} \in \stackrel{°}{I} \iff \begin{cases} \exists \lim_{x \to x_{0}^{-}} \frac{f(x) - f(x_{0})}{x - x_{0}} \in \mathbb{R} & := f'_{-}(x_{0}) \\ \exists \lim_{x \to x_{0}^{+}} \frac{f(x) - f(x_{0})}{x - x_{0}} \in \mathbb{R} & := f'_{+}(x_{0}) \\ f'_{-}(x_{0}) = f'_{+}(x_{0}) \ (=f'(x_{0})) \end{cases}$$

In poche parole dobbiamo fare la **derivata destra** e la **derivata sinistra** della funzione per $x_{0}$, e verificarne l'esistenza e l'uguaglianza.

<u>Attenzione</u>: _guardare attentamente il dominio della funzione e della rispettiva derivata_. Ci sono infatti funzioni come $\sqrt{x}$ dove la derivata può assumere valori solo per $x > 0$.

## Funzione derivata
> Se una funzione $f$ è derivabile in ogni suo punto del dominio allora si può associare da $f$ la sua _funzione derivata_. Ovvero
> $$f \text{ derivabile } \forall x \in I \implies f': I \to \mathbb{R}, \ x \to f'(x)$$

Da questo otteniamo tutte le [[Regole di derivazione|regole di derivazione]] standard.

## Limite destro e sinistro
Anche in questo caso, come per le [[Funzioni continue|funzioni continue]], la derivata di una funzione per $x_{0}$ esiste <u>sse</u> esiste la sua **derivata destra** e **derivata sinistra**. Quindi se esiste ed è finito il _[[Limite|limite]] del rapporto incrementale_ della funzione a destra e sinistra.

In particolare questo _ci è utile quando stiamo studiando il punto di incollamento di una funzione spezzata_, o con un [[Valore assoluto|valore assoluto]] (per il quale quindi si _spezza la funzione in due rami_).

<u>Attenzione</u>: non per forza se non esiste il limite destro/sinistro del rapporto incrementale allora la funzione non ammette la derivata destra/sinistra.

### Osservazione
Se sappiamo che la _funzione è derivabile nell'[[Intorno|intorno]] di $x_{0}$ allora al posto di verificare le due derivate per il limite del rapporto incrementale possiamo direttamente confrontare le derivate prime_ (usando quindi le normali [[Regole di derivazione|regole di derivazione]]).

## Referenze
- [[Derivate di ordine superiore]]
- [[Rapporto tra continuità e derivabilità]]