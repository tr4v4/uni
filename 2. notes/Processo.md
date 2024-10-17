---
tags:
  - category/note
  - status/pending
  - topic/sistemi-operativi
date: 15-10-2024 16:58:39
links:
  - "[[Lecture 10102024092110]]"
---
# Processo
---
## Introduzione
> Per **processo** si intende un'attività controllata da un programma che si svolge su un [[CPU|processore]].

### Processo vs. programma
Un **processo non è un programma**:
- un programma è un'_entità statica_, che specifica una sequenza di istruzioni (e non la durata nel tempo dell'esecuzione);
- un processo è un'_entità dinamica_, che rappresenta l'attività dell'esecuzione di un programma.

## Caratteristiche
Una delle proprietà fondamentali dei processi è descritta da un'[[Assioma|assioma]]: l'[[Assioma di finite progress|assioma di finite progress]].

## Stato
Ad ogni istante un processo è descritto da:
1. _la sua immagine in [[RAM|memoria]]_ (la memoria assegnata e le strutture dati del sistema operativo associate al processo);
2. _la sua immagine nel processore_ (contenuto dei [[Registro|registri]] [[Registro#Registri generali|generali]] e [[Registro#Registri speciali|speciali]]);
3. _lo stato di avanzamento_ (il suo stato corrente, se è in esecuzione o in attesa di qualche evento).

## Referenze