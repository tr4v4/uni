---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 07-10-2023 12:01:16
links:
  - "[[Lecture 06102023134057]]"
---
# Dimostrazione esistenza numero di Nepero
---
## Introduzione
Del [[Numero di Nepero|numero di Nepero]] (o di Eulero)
$$e = 2.718281828459...$$

si dimostra l'esistenza a partire da un limite:
$$\lim_{n \to +\infty} {(1 + \frac{1}{n})}^{n}, \ \ n \in N^{*}$$

che di per sé si presenta come una [[Forme indeterminate|forma indeterminata]] ($1^{+\infty}$).

## Dimostrazione
Vogliamo quindi dimostrare che
$$a_{n} = {(1 + \frac{1}{n})}^{n}$$
è **convergente**.

Per farlo sfruttiamo le [[Dimostrazione successioni monotone hanno limite#Corollario|conseguenze del limite delle successioni monotone]], che ci dicono che se $a_{n}$ è _crescente_ e _superiormente limitata_ allora converge.

### $a_{n}$ crescente
Se $a_{n}$ dev'essere crescente, significa che
$$a_{n+1} \geq a_{n}$$
da cui
$$\frac{a_{n+1}}{a_{n}} \geq 1$$

Dobbiamo dimostrare questa disuguaglianza. Partiamo con le trasformazioni
$$\frac{a_{n+1}}{a_{n}} = \frac{(1 + \frac{1}{n+1})^{n+1}}{(1 + \frac{1}{n})^{n}} = \frac{n+2}{n+1}(1 - \frac{1}{n^{2}+2n+1})^{n}$$

Ora, grazie alla [[Disuguaglianza di Bernoulli|disuguaglianza di Bernoulli]] sappiamo che
$$\frac{n+2}{n+1}(1 - \frac{1}{n^{2}+2n+1})^{n} \geq \frac{n+2}{n+1}(1 - \frac{n}{n^{2}+2n+1})$$
e a noi va bene trovare un valore più piccolo per cui valga la disuguaglianza iniziale: se vale per questa espressione, allora varrà per forza per l'espressione iniziale.

Quindi
$$\frac{n+2}{n+1}\left(1 - \frac{n}{n^{2}+2n+1}\right) = 1 + \frac{1}{n^{3}+3n^{2}+3n+1}$$

da cui
$$1 + \frac{1}{n^{3}+3n^{2}+3n+1} > 1$$

La disequazione vale, per cui abbiamo dimostrare che $a_{n}$ è crescente. **Cvd**.

### $a_{n}$ sup. limitata
Per provare che $a_{n}$ è superiormente limitata sfrutteremo il [[Binomio di Newton|binomio di Newton]].

La successione
$${(1 + \frac{1}{n})}^{n}$$
può infatti essere scritta anche come binomio di Newton, ovvero nella forma
$$\sum\limits_{k = 0}^{n} \binom{n}{k} 1^{n-k} \cdot (\frac{1}{n})^{k}$$

Estendiamo la definizione del [[Coefficiente binomiale|coefficiente binomiale]] $\binom{n}{k}$ e togliamo $1^{n-k}$
$$\sum\limits_{k = 0}^{n} \frac{n!}{(n-k!)k!} \cdot \frac{1}{n^{k}}$$

Riscriviamo il coefficiente binomiale, così da ottenere
$$\sum\limits_{k = 0}^{n} \frac{n \cdot (n-1) \cdot (n-2) \cdot ... \cdot (n-(k-1))}{n^{k}} \cdot \frac{1}{k!}$$

In questo modo sia al numeratore che al denominatore avremo _k-elementi_. Quindi scomponiamo la frazione in prodotti di _k-frazioni_:
$$\sum\limits_{k = 0}^{n} \frac{n}{n} \cdot \frac{n-1}{n} \cdot \frac{n-2}{n} \cdot ... \cdot \frac{n-(k-1)}{n} \cdot \frac{1}{k!}$$

Ora, il prodotto dei termini divisi per $n$ sicuramente sarà $\leq 1$, per cui eliminandoli otterremo una sommatoria di valore maggiore. A noi non causa un problema ciò: se dimostriamo che una successione "più grande" è superiormente limitata, allora per forza anche quella di partenza lo sarà.

Per cui
$$\sum\limits_{k = 0}^{n} \frac{n}{n} \cdot \frac{n-1}{n} \cdot \frac{n-2}{n} \cdot ... \cdot \frac{n-(k-1)}{n} \cdot \frac{1}{k!} \leq \sum\limits_{k = 0}^{n} \frac{1}{k!}$$

Ora possiamo concentrarci solo su
$$\sum\limits_{k = 0}^{n} \frac{1}{k!} = 1 + 1 + \sum\limits_{k = 2}^{n} \frac{1}{k!}$$
($\frac{1}{0!} = 1, \ \frac{1}{1!} = 1$)

Adesso, $\frac{1}{k!}$ per $k$ che parte da 2 è dimostrabile essere $\leq \frac{1}{k-1} - \frac{1}{k}$, da cui
$$2 + \sum\limits_{k = 2}^{n} \frac{1}{k!} \leq 2 + \sum\limits_{k = 2}^{n} \frac{1}{k-1} - \frac{1}{k}$$

Quest'ultima sommatoria è detta **telescopica**, il che significa che di essa sopravvivono soltanto il primo e l'ultimo valore, perciò:
$$\sum\limits_{k = 2}^{n} \frac{1}{k-1} - \frac{1}{k} = 2 + 1 - \frac{1}{n} = 3 - \frac{1}{n} < 3$$

Infine, quindi, abbiamo dimostrato che la successione sicuramente non supera 3 $\implies$ è _superiormente limitata_. **Cvd**.

### Conclusione
Dalle due dimostrazioni e il corollario dimostriamo quindi che
$$a_{n} = {(1 + \frac{1}{n})}^{n} \text{ è convergente}$$

## Referenze