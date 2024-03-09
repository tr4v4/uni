---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 15-10-2023 18:33:00
links:
  - "[[Lecture 11102023131154]]"
---
# Insieme quoziente
---
## Introduzione
> Si definisce **insieme quoziente** l'insieme che comprende tutte le [[Classe di equivalenza|classi di equivalenza]] di una [[Relazione di equivalenza|relazione di equivalenza]] $\equiv \subseteq A \times A$. Si definisce quindi come
> $$A_{/\equiv}= \{[x]_{\equiv} | x \in A\}$$

### Esempi
Se prendiamo la relazione di equivalenza _avere la stessa età_ di un insieme $A$ di persone, una possibile classe di equivalenza potrebbe essere
$$[\text{Nicola Travaglini}]_{\equiv} = \{\text{Nicola Travaglini}, \text{Davide Cavallo}, \text{Matteo Rossi}, ...\}$$

ovvero l'insieme contenente tutte le persone che hanno la stessa età di $\text{Nicola Travaglini}$.

L'insieme quoziente della relazione _avere la stessa età_ per l'insieme $A$ conterrà allora tutte le classi di equivalenza per ogni persona identificate dalla stessa età:
$$A_{/\equiv} = \{[\text{Nicola Travaglini}]_{\equiv}, [\text{Francesca Cupido}]_{\equiv}, [\text{Gualtiero Rambaldi}]_{\equiv}, ...\}$$

## Utilizzi
> Gli insiemi quozienti sono strumenti molto potenti per applicare una sorta di [[Principio di astrazione-implementazione|principio di astrazione-implementazione]] su concetti pre-esistenti.

Per esempio, _con gli insiemi quozienti dai numeri naturali possiamo dimostrare l'esistenza degli interi, da cui a sua volta otteniamo i razionali_.

### Creazione dei numeri interi
[[Costruzione dei numeri naturali|Costruiti i numeri naturali]], con le classi di equivalenza e l'insieme quoziente siamo in grado di costruire l'insieme dei [[Numeri interi|numeri interi]].

Prendiamo allora
$$Z = \mathbb{N} \times \mathbb{N}$$
Per ora l'insieme $Z$ contiene tutte le coppie ordinate che combinano tutti i numeri naturali tra di loro. Possiamo dare un'interpretazione al significato delle coppie ordinate: la _sottrazione_ tra il primo e il secondo elemento.

La sottrazione infatti non è concessa per ogni coppia di numero naturale, per questo entriamo così facendo negli interi. Ad ogni modo, _formalizziamo il significato delle coppie ordinate creando una relazione di equivalenza_:
$$\equiv \subseteq R \times R : (u_{1}, l_{1}) \equiv (u_{2}, l_{2}) \stackrel{\text{def}}{=} u_{1} + l_{2} = u_{2} + l_{1}$$

Abbiamo creato una relazione che rende equivalenti due coppie ordinate di $R$ nel momento in cui viene rispettata la "legge"
$$u_{1} + l_{2} = u_{2} + l_{1}$$

Questo perché se prendiamo per esempio la coppia $(2, 4)$, essa è in equivalenza di sottrazione con la coppia $(3, 5)$, perché $2-4 = 3-5$. Sappiamo che siamo ancora nel "dominio" dei naturali, per cui per scrivere tale equivalenza dobbiamo usare le somme: usiamo le regole delle espressioni matematiche per portare il $-5$ a sinistra dell'uguale e il $-4$ a destra dell'uguale, cambiando il segno. Otteniamo sempre un'uguaglianza: $2+5 = 3+4$.

Da questa relazione di equivalenza possiamo creare tutte le classi di equivalenza che vogliamo, per esempio
$$[(2, 4)]_{\equiv} = \{(2, 4), (3, 5), (9, 11), ...\}$$

Per ottenere $\mathbb{Z}$ ci basta allora raccogliere tutte le possibili classi di equivalenza in un insieme quoziente:
$$\mathbb{Z} \stackrel{\text{def}}{=} Z_{/\equiv} = \{..., [(0, 2)]_{\equiv}, [(0, 1)]_{\equiv}, [(0, 0)]_{\equiv}, [(1, 0)]_{\equiv}, [(2, 0)]_{\equiv}, ...\}$$

<u>Nota bene</u>: è importante notare che quindi **i numeri positivi degli interi non corrispondono ai numeri naturali**. $+2 \neq 2$.

## Referenze