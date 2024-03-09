---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 18-10-2023 20:28:57
links:
  - "[[Lecture 18102023131238]]"
  - "[[Lecture 19102023092110]]"
  - "[[Lecture 31102023161330]]"
  - "[[Lecture 09112023131356]]"
  - "[[Lecture 16112023092027]]"
---
# Regole di inferenza
---
## Introduzione
Le **regole d'inferenza** servono per dimostrare gli [[Albero di deduzione naturale|alberi di deduzione naturale]], e consistono in _passi standard da seguire_.

## Composizione
Una regola di inferenza si compone di:
- _barra orizzontale_
- _premesse_ sopra barra
- _conclusione_ sotto barra
- _nome della regola_ utilizzata a destra della barra

![[regole-di-inferenza.png]]

### Casi particolari
Ci sono casi in cui una regola non ha bisogno di premesse in quanto presa per vera: gli [[Assioma|assiomi]], che quindi hanno una barra orizzontale senza alcuna premessa sopra.

## Tipologie
Le regole d'inferenza sono principalmente 2:
- [[Regole di introduzione]]
- [[Regole di eliminazione]]

## Letture
Le regole d'inferenza possono essere lette in 2 modi diversi:
- **bottom-up**[^1], per cui da una serie di premesse si giunge ad una conclusione
	- _pro_: non si commettono mai errori
	- _cons_: è difficile vedere le prove così, ci sono troppe strade che non portano alla conclusione cercata
- **top-down**[^2], per cui dalla conclusione si arriva ad una serie di premesse che la provano
	- _pro_: più facile trovare le dimostrazioni se si sta attenti a non sbagliarsi
	- _cons_: è possibile sbagliarsi quando si applicano regole non invertibili

Solitamente _i matematici usano l'approccio top-down per dimostrare dei teoremi_, ma una volta terminate le prove _le presentazioni le fanno in bottom-up_ (per questione di eleganza).

## Regole
- [[Regole di inferenza dell'AND]]
- [[Regole di inferenza dell'OR]]
- [[Regole di inferenza del BOTTOM]]
- [[Regole di inferenza del TOP]]
- [[Regole di inferenza dell'implica]]
- [[Regole di inferenza del NOT]]
- [[Regole di inferenza del per ogni]][^3]
- [[Regole di inferenza dell'esiste]][^3]

### Speciali
- [[Regole di inferenza del RAA]]
- [[Regole di inferenza di EM]]

## Correttezza
Dobbiamo chiederci: _le regole di inferenza sono corrette_? O meglio, sono corrette o meno rispetto alla valenza logica?

> Una regola è [[Teorema di correttezza|corretta]] se:
> $$F_{1}, F_{2}, F_{3}, ... \vdash F \ \ \implies \ \ F_{1}, F_{2}, F_{3}, ... \Vdash F$$
> ovvero, **se una regola da una serie di ipotesi $\Gamma$ conclude $F$, essa è corretta se si dimostra che $F$ è [[Conseguenza logica|conseguenza logica]] di $\Gamma$**.

<u>Nota bene</u>: se una delle premesse ($F_{1}, F_{2}, F_{3}, ...$) contempla ipotesi scaricate, allora bisogna integrarle come [[Implicazione|implicazioni]].
Per esempio:
![[correttezza-regole-di-inferenza.png]]

## Completezza
Dobbiamo chiederci: _le regole di inferenza sono complete_? Ovvero, abbiamo tutte le regole che ci servono per fare dimostrazioni sulla logica di riferimento?

La risposta è che nel caso della [[Logica classica|classica]] no, **le regole non sono complete**. Per capirlo ci basta comprendere che non è possibile dimostrare le seguenti due [[Tautologia|tautologie]]:
- $\nvdash \neg \neg A \implies A$
- $\nvdash A \lor \neg A$

Sappiamo, _intuitivamente_, che sono vere (per mezzo della [[Semantica classica#Definizione|definizione di semantica classica]]), ma non riusciamo a dimostrarle con le regole definite finora. Per questo è necessario aggiungere **RAA**, con cui si ottiene anche **EM**.

Altrimenti, l'unica altra alternativa sarebbe quella di _chiedersi se esista una logica che sia completa rispetto alle regole base_: sarà la [[Logica intuizionista|logica intuizionista]].

## Referenze
- [[Invertibilità di una regola di inferenza]]
- [[Derivabilità di una regola di inferenza]]
- [[Armonia delle regole di inferenza]]

[^1]: vedi [[Approccio bottom-up|approccio bottom-up]]
[^2]: vedi [[Approccio top-down|approccio top-down]]
[^3]: in [[Logica del primo ordine|logica del prim'ordine]]