---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 24-09-2024 17:49:39
links:
  - "[[Lecture 19092024151357]]"
  - "[[Lecture 10102024151443]]"
  - "[[Lecture 17102024151452]]"
---
# REST
---
## Introduzione
> Il paradigma di sviluppo **REST** (_REpresentational State Transfer_), è un modello "filosofico" con tanto di regole e suggerimenti usato per stabilire un'interazione tra client e server su [[Protocollo di rete|protocollo]] [[HTTP]] e su _naming_ [[URI]] che garantisca [[Interoperabilità|interoperabilità]], [[Scalabilità|scalabilità]], ecc... E' il modello architetturale che si cela dietro al [[Web|WWW]] e alle applicazioni web ben fatte.

<u>Nota bene</u>: è spesso tradito per praticità[^1].

Il pattern adottato da REST è il [[CRUD]].

## Principi
Il REST si basa su 4 principi fondamentali:
1. definire [[Risorsa|risorsa]] ogni concetto rilevante dell'applicazione web;
2. associare ad essa un URI come identificatore e selettore primario;
3. usare i [[Metodi HTTP|metodi HTTP]] per esprimere ogni operazione dell'applicazione secondo il modello CRUD;
4. esprimere in maniera parametrica ogni _rappresentazione dello stato interno di una risorsa_, attraverso l'[[Header HTTP|header]] `Content-Type`.

### Individui e collezioni
REST, inoltre, identifica due concetti fondamentali:
- _individui_ - singole risorse;
- _collezioni_ - insiemi di individui.

<u>Nota bene</u>: c'è un URI per ognuno di questi due!

Le collezioni possono contenere individui o altre collezioni. Solitamente si strutturano gli URI dell'[[API]] di riferimento in modo gerarchico.

### Filtri
Attraverso le _query string_ dell'URI si implementano i filtri di ricerca di risorse.

## Referenze
[^1]: state-ful!