---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-03-2025 16:44:23
links:
  - "[[Lecture 27022025131944]]"
  - "[[Lecture 05032025111458]]"
---
# Variabile
---
## Introduzione
> Una **variabile** e' un'entita' che _rappresenta un'area di memoria in cui e' possibile memorizzare un valore_.

## Modelli
### Linguaggi imperativi
Nei [[Linguaggio di programmazione imperativo|linguaggi imperativi]] le variabili sono **modificabili**.

### Linguaggi funzionale
Nei [[Linguaggio di programmazione funzionale|linguaggi di programmazione funzionale]] le variabili **denotano un valore** che non può essere modificato.

### Linguaggi logici
Nei [[Linguaggio di programmazione logico|linguaggi di programmazione logici]] le variabili **denotano sempre un valore**, ma **sono modificabili** entro certi limiti.

### A riferimento
In alcuni linguaggi di programmazione, invece, una variabile costituisce un riferimento a un valore, che ha un [[Nome|nome]]. E' analogo alla nozione di [[Puntatori|puntatore]], ma non si può modificare la loro locazione.

In modelli di variabili del genere, ovviamente, è facile che si verifichi [[Aliasing|aliasing]].

## Operazioni
Le operazioni elementari sulle variabili, in particolare su quelle _modificabili_, sono:
- [[Assegnamento|assegnamento]]

## Ambiente
Per rappresentare lo stato di un programma si potrebbe pensare che sia sufficiente mantenere un'associazione tra _nomi --> valori_. Ma se si usa il modello delle variabili a riferimento, il fenomeno dell'aliasing non viene catturato.

Per risolvere questo problema si introducono 3 importanti domini semantici:
- _valori denotabili_, a cui si può dare un nome;
- _valori memorizzabili_, si possono memorizzare;
- _valori esprimibili_, risultato della valutazione di un'[[Espressione|espressione]].

Allora, la semantica dei linguaggi imperativi si può esprimere attraverso 2 funzioni:
- `AMBIENTE`: _nome --> valore denotabile_ (che saranno locazioni);
- `MEMORIA`: _locazione --> valore memorizzabile_.

Se quindi eseguiamo l'assegnazione `X = 3`, il sistema procede in due fasi:
1. **aggiornamento dell'ambiente**:
    - si assegna ad `X` una nuova locazione, ad esempio `l1`.
    - quindi, l'ambiente diventa: `AMBIENTE`: _X --> l1_.
2. **aggiornamento della memoria**:
    - si memorizza il valore `3` nella locazione `l1`.
    - quindi, la memoria diventa: `MEMORIA`: _l1 --> 3_.

<u>Nota bene</u>: i linguaggi funzionali utilizzano solo `AMBIENTE`.

## Referenze