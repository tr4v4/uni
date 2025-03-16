---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
  - topic/sistemi-operativi
date: 25-09-2023 18:46:38
links:
  - "[[Lecture 25092023130405]]"
  - "[[Lecture 21022025091223]]"
---
# HD
---
## Definizione
> Gli **HD** (_Hard Disk_) sono **dispositivi elettro-meccanici** per la conservazione di informazioni sotto forma _magnetica_.

Sono molto più lenti della [[RAM]], ma in grado di salvare in maniera persistente una ben più grande quantità di dati.

L'**accesso ai dati e' diretto**, non sequenziale.

## Composizione
- **testina** - magnetizza e legge lo stato di magnetizzazione della superficie del disco
- **traccia** (o **cilindro**) - sequenza circolare di bit
- **settore** - porzione di traccia che contiene una quantità prefissata di bit (uguale per tutti i settori)

Per accedervi il [[Device controller|controller]] espone i metodi:
- `READ(head, sector)`
- `WRITE(head, sector)`
- `SEEK(cylinder)` - la piu' costosa, consiste nello spostare fisicamente il pettine di testine da un cilindro a un altro;

## Referenze