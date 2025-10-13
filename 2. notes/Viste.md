---
tags:
  - category/note
  - status/finished
  - topic/basi-di-dati
date: 04-10-2025 20:07:56
links:
  - "[[Lecture 08102025101345]]"
---
# Viste
---
## Introduzione
> Le **viste** (o **views**) nei [[Database|database]] sono delle _[[Modello relazionale dei dati|relazioni]] costruite derivandole da altre relazioni_.
> Sono quella parte dell'[[DBMS#Architettura|architettura]] dei [[DBMS]] che compone gli _external schema_.

Sono costruite mediante l'[[Algebra relazionale|algebra relazionale]]!

## Utilizzi
Le viste possono essere usate in due modi:
- _viste materializzate_;
- _[[Viste virtuali|viste virtuali]]_.

### Viste materializzate
Sono delle _tabelle di vista temporanee o permanenti fisicamente salvate nel database_.

Pros:
- i dati sono già pronti per query future;

Cons:
- ridondanza dei dati;
- gli update del database sono rallentati --> bisogna aggiornare anche tali viste;
- i DBMS raramente le supportano.

## Utilità
In generale, le viste, sono molto utili:
- costituiscono gli **schemi esterni** del modello architetturale dei DBMS;
	- ![[dbms-architettura-standard.png]]
	- in [[SQL]], poi, si possono creare delle regole di accesso alle viste sulla base dell'autenticazione
- sono uno strumento di **semplificazione delle query**, perché in query complesse consentono di eliminare sottoespressioni ripetute;

<u>Nota bene</u>: le viste non intaccano minimamente l'efficienza delle query!

## Update
Bisogna fare particolare attenzione agli aggiornamenti sulle viste: **gli aggiornamenti non devono essere ambigui**, vale a dire che ci devono essere sufficienti informazioni per poter aggiornare le tabelle di base.

Infatti ogni aggiornamento sulle view deve corrispondere ad aggiornamenti sulle tabelle di base. E' per questo che _pochissimi aggiornamenti sono consentiti sulle viste_.

## Referenze