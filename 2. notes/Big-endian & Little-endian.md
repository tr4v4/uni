---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
  - topic/tecnologie-web
date: 13-10-2024 13:05:36
links:
  - "[[Lecture 21092023130150]]"
---
# Big-endian & Little-endian
---
## Introduzione
Alcuni processori generano e gestiscono i flussi di coppie di byte ponendo il byte più significativo prima, altri dopo il byte meno significativo.
Esistono allora due modi per memorizzare le word:
- **big endian** --> indirizzi assegnati da sx a dx
- **little endian** --> indirizzi assegnati da dx a sx

![[big_endian-little_endian.webp]]

O meglio, considerato che la memoria si struttura **a matrice**
![[big-endian-little-endian.png]]

Ma come si fa, ricevuto un flusso di dati in una certa [[Codifica dei caratteri|codifica]], a essere sicuri di quale sia il modello di memorizzazione originario? [[UNICODE]] ci ha pensato con il [[BOM]].

## Referenze