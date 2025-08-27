---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-08-2025 18:10:12
links:
  - "[[Lecture 05112024110833]]"
---
# Forma normale di Greibach
---
## Introduzione
> La **forma normale di Greibach** consiste in una forma di una [[Grammatiche|grammatica]] in cui tutte le produzioni sono della forma
> $$A \to aBC \ \ \ \ \ A \to aB \ \ \ \ \ A \to a$$
> con $\epsilon$ trattato a parte, nella fattispecie $S \to \epsilon | aBC$. Le proprieta' sono le seguenti:
> - _una grammatica $G$ in forma normale di Greibach non ha produzioni-$\epsilon$ ne' produzioni unitarie_;
> - _una grammatica $G$ in forma normale di Greibach non e' mai ricorsiva sinistra_;
> - _ogni produzione applicata in una [[Derivazione|derivazione]] allunga il prefisso di terminali $\implies$ i [[Parser|parser]] costruiti a partire da grammatiche in questa forma sono meno nondeterministici_;
> - _ogni grammatica $G$ [[Grammatiche libere|libera]] puo' essere trasformata in una [[Grammatiche equivalenti|equivalente]] $G'$ in forma normale di Greibach_.

## Referenze