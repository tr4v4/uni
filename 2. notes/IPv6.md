---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 14-12-2024 14:46:31
links:
  - "[[Lecture 22112024130956]]"
---
# IPv6
---
## Introduzione
> L'**IPv6** (_Internet Protocol version 6_) è la sesta versione del [[Protocollo di rete|protocollo di rete]] [[IP]]. Segue l'[[IPv4]].

L'idea di una versione nuova di IP nasce nel 1990 a _causa della preoccupazione riguardo la fine degli indirizzi IPv4 disponibili_, stimata tra il 2008 e il 2018. Questa è effettivamente avvenuta nel 2013.

<u>Nota bene</u>: il motivo per cui ancora oggi la maggior parte di internet si basa su IPv4 è perché sono stati introdotti protocolli che consentono di risparmiare sul numero di indirizzi pubblici, come il [[NAT]].

Oggi l'IPv6 non è usato quasi mai in sostituzione a IPv4, ma bensì integrato ad esso: [[Protocollo di tunnelling|tunnelling IPv4]].

## Caratteristiche
Con questa versione di indirizzi IP si vuole risolvere il problema del numero di indirizzi disponibili e altri problemi dell'IPv4:
- **indirizzi a 128 bit** (rispetto ai 32 bit di IPv4) --> il numero di indirizzi diventa $2^{128}$;
- **QoS** (Quality of Service) --> si introducono nuovi campi per differenziare le priorità dei pacchetti, i [[Router|router]] e i [[Protocollo di routing|protocolli di routing]] devono tenere conto di questo valore;
- **eliminazione della frammentazione**;

## Referenze