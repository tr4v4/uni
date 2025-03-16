---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/architettura-degli-elaboratori
  - topic/sistemi-operativi
date: 22-09-2023 19:59:20
links:
  - "[[Lecture 21092023130150]]"
  - "[[Lecture 18102023151217]]"
  - "[[Lecture 21022025091223]]"
---
# Memorie
---
## Introduzione
La memoria è qualunque oggetto in grado di _memorizzare informazioni_, su cui quindi è possibile **leggere e/o scrivere dati**. Ci sono delle proprietà che caratterizzano ogni dispositivo di memorizzazione:
- _prezzo_
- _velocità_
- _capacità_

## Classificazione
Delle 3 caratteristiche non si può volere tutto, e anzi queste determinano di una memoria la sua funzione, e quindi classificazione:
- **volatili** - che non mantengono i valori salvati se spenti
	- [[Registro|registri]] --> quelli usati più spesso dalla CPU
	- [[Cache|cache]] --> più piccola e veloce della RAM, più grande e lenta dei registri
	- [[RAM]]
- **persistenti** - che mantengono i valori salvati se spenti
	- [[HD|dischi magnetici]] e a [[SSD|stato solido]] (on-line, perché sempre accessibili)
	- nastri, [[CD|dischi ottici]] (off-line, perché _da montare_ per poter accedervi)

La gerarchia delle memorie e' quindi la seguente:
![[gerarchia-memorie.png]]

## Organizzazione
Le memorie, qualunque esse siano, si organizzano in **celle**, vale a dire _sequenze di bit identificate da un indirizzo_. A seconda del tipo di memoria e del tipo di architettura dell'elaboratore, la capacità delle celle può variare: nella maggior parte dei casi, però, **le celle di memoria sono di 1 byte**.

Di solito oggigiorno i computer lavorano in _blocchi_ di 32 o 64 bit, chiamati **word**: questo vuol dire che per salvare una word di 32 bit saranno necessarie 4 celle di memoria; 8 per una word di 64 bit.
Esistono allora due modi per memorizzare le word: [[Big-endian & Little-endian|big-endian e little-endian]].

## Tipologie
Esistono due principali tecnologie di costruzione di memorie:
- [[SRAM]]
- [[DRAM]]/[[SDRAM]]

## Referenze
- [[RAID]]
- [[Big-endian & Little-endian]]