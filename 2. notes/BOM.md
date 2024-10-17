---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 13-10-2024 13:09:08
links:
---
# BOM
---
## Introduzione
> Il **BOM** (_Byte Order Mark_) è un carattere usato da [[UNICODE]] per specificare l'ordine dei byte, ossia [[Big-endian & Little-endian|big-endian o little-endian]].

In particolare UNICODE suggerisce di usare `FEFF` all'inizio di ogni flusso [[UTF-16]] come carattere per segnalare il big-endian, e se non c'è allora significa che la trasmissione è in little-endian.

Questo carattere viene chiamato **ZWNBSP** (_Zero-Width No-Break Space_): può essere messo in qualunque contesto di whitespace (ossia ovunque tranne in mezzo alle parole) e non modifica il significato dei testi.

## Referenze