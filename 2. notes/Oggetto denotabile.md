---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 20-02-2025 09:52:12
links:
  - "[[Lecture 19022025111150]]"
  - "[[Lecture 20022025131602]]"
---
# Oggetto denotabile
---
## Introduzione
> Un **oggetto denotabile** e' un oggetto a cui puo' essere associato un [[Nome|nome]].

## Operazioni
Su un oggetto denotabile possono essere svolte le seguenti operazioni:
- _creazione_;
- _accesso_;
- _modifica_ (solo se l'oggetto e' modificabile);
- _distruzione_;

## Lifetime
In realta', la vita di un oggetto denotabile prevede piu' fasi:
1. _creazione di un oggetto_;
2. _creazione di un [[Binding|binding]]_ tra nome e oggetto;
3. _riferimento all'oggetto_, tramite binding;
4. _disattivazione di un binding_;
5. _riattivazione di un binding_;
6. _distruzione di un binding_;
7. _distruzione di un oggetto_.

<u>Nota bene</u>: **la vita dell'oggetto e quella del binding non vanno di pari passo**. Per esempio, _la creazione e la distruzione di un oggetto non coincidono con la creazione e la distruzione del binding per esso_. Per esempio:
- **un oggetto puo' vivere di meno di un binding**, come avviene per i [[Dangling pointer|dangling pointers]];
- **un oggetto puo' vivere di piu' di un binding**, come avviene nel [[Passaggio per riferimento|passaggio per riferimento]] alle [[Funzione informatica|funzioni]].

## Referenze
- [[Binding]]