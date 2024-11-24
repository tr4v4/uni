---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 20:49:41
links:
  - "[[Lecture 13112024133033]]"
---
# Subnetting
---
## Introduzione
> Il **subnetting** è un _processo di divisione di una rete in sottoreti_. Per farlo ci si serve della [[Subnet mask|subnet mask]].

## Funzionamento
I passaggi per poter fare subnetting sono i seguenti:
1. identificare la [[Classi di rete|classe di rete]] dell'[[Indirizzo IP|indirizzo IP]] a disposizione;
2. capire quanti bit vengono rubati dalla parte di host per creare le sottoreti.

<u>Attenzione</u>: per evitare la frammentazione degli indirizzi nelle sottoreti, **è buona prassi allocare verso l'inizio di un blocco di indirizzi**, da quelli più grandi a quelli più bassi. Questo perché _il subnetting è impostato sui bit più significativi_, per cui se si vuole dividere in sottoreti bisogna per forza partire dalle più grandi e poi scalare in quelle più piccole.

## Referenze