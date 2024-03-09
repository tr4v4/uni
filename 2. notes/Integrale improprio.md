---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 07-03-2024 16:18:04
links:
  - "[[Lecture 07032024141028]]"
---
# Integrale improprio
---
## Introduzione
> Un **integrale improprio** è un [[Integrale|integrale]] cui _uno degli estremi dell'intervallo d'integrazione non appartiene al dominio della funzione integranda (intervallo limitato) o è infinito (intervallo illimitato)_.

Per entrambi i tipi di intervalli vale che il valore di un integrale improprio può essere **convergente** o **divergente**.

## Tipologie
### Intervallo illimitato
> Sia $f: [a, +\infty[ \to \mathbb{R}$, si dice che l'integrale generalizzato $\int_{a}^{+\infty} f(x) \ dx$ è convergente se è finito il [[Limite|limite]] $$\lim_{r \to +\infty} \int_{a}^{r} f(x) \ dx$$

Se il limite è invece divergente (o anche oscillante) allora si dice che l'integrale generalizzato è divergente (o appunto oscillante);
<u>Nota bene</u>: la definizione di $\int_{-\infty}^{b} f(x) \ dx$ è costruita in modo analogo (cioè $\lim_{r \to -\infty} \int_{r}^{b} f(x) \ dx$).

### Intervallo limitato
> Sia $f: ]a, b] \to \mathbb{R}$ continua, si dice che l'integrale generalizzato $\int_{a}^{b} f(x) \ dx$ è convergente se è finito il limite $$\lim_{r \to a^{+}} \int_{r}^{b} f(x) \ dx$$

Se il limite è invece divergente (o anche oscillante) allora si dice che l'integrale generalizzato è divergente (o appunto oscillante);
<u>Nota bene</u>: anche in questo caso vale la versione speculare per $f: [a, b[ \to \mathbb{R}$.

## Referenze