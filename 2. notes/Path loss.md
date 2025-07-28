---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-07-2025 18:11:47
links:
  - "[[Lecture 07042025111854]]"
---
# Path loss
---
## Introduzione
> Il **path-loss** e' una _stima pessimistica in dB della dispersione di un segnale [[Onda radio|radio]] in un canale di comunicazione_, basato sulla _distanza tra il trasmettitore e il ricevitore e sulla frequenza del segnale_.

Il path-loss e' un parametro importante per calcolare la potenza del segnale ricevuto, e viene calcolato con la seguente formula:
$$PL = 36.6 + 20\log_{10}(F) + 20\log_{10}(D)$$

## 6dB rule
> La **6dB rule** e' una regola empirica che afferma che, _per ogni raddoppio della distanza tra il trasmettitore e il ricevitore, il path-loss aumenta di 6dB_.

Qui sotto la tabella dei path-loss su una frequenza fissa di 2.4GHz (che conferma la 6dB rule):
![[6db-rule.png]]

## Referenze