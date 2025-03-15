---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 23-02-2025 13:43:20
links:
  - "[[Lecture 17022025090125]]"
---
# Problema
---
## Introduzione
> Un **problema** e' una _domanda espressa in termini generali_, ma la cui _risposta dipende da un certo numero di parametri e variabili_. Formalmente, un problema $\mathcal{P}$, viene descritto tramite:
> - _parametri e variabili_;
> - _caratteristiche delle soluzioni_;

## Istanze
Un'**istanza** del problema $\mathcal{P}$ si ottiene _specificando dei valori concreti per tutti i parametri del problema, ma non per le variabili_. Ricorda che infatti che:
- **i parametri sono i dati del problema**, che definiscono la sua istanza;
- **le variabili sono le incognite del problema**, che definiscono le sue soluzioni.

Per esempio, il problema $ax^2+bx+c=0$ puo' avere come istanza $5x^2+3x+1=0$.

## Descrizione
Per descrivere un problema $\mathcal{P}$ si costruisce l'**insieme delle sue soluzioni ammissibili $\mathbb{F}_{\mathcal{P}}$**. Di solito $\mathbb{F}_{\mathcal{P}} \subseteq \mathbb{G}$, e si trova specificando dei vincoli che un generico $g \in \mathbb{G}$ deve soddisfare per far parte di $\mathbb{F}_{\mathcal{P}}$. Gli elementi che appartengono a **$\mathbb{G} \setminus \mathbb{F}_{\mathcal{P}}$ sono detti soluzioni non ammissibili**.

Per esempio, la descrizione di un'istanza di un problema puo' essere la seguente:
$$5x^{2}-6x+1=0 \implies \begin{array}{align} \mathbb{G}=\mathbb{R} \\ \mathbb{F}_{\mathcal{P}} = \{x\in\mathbb{G}\ | \ 5x^{2}-6x+1=0\}\end{array}$$

## Referenze