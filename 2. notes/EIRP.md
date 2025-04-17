---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 06-04-2025 18:34:59
links:
  - "[[Lecture 01042025152454]]"
---
# EIRP
---
## Introduzione
Teoricamente _un'antenna ideale dovrebbe ricevere e trasmettere segnali in tutte le direzioni_, raccogliendo e inviando [[Onda radio|onde radio]] in modo uniforme (sferico): si parla di **antenna isotropica**. Nella realta', nessuna antenna e' veramente isotropica, perche' avra' sempre una direzione preferenziale di irradiazione.

Di conseguenza, se all'antenna arriva una certa energia dall'[[Intentional radiator|intentional radiator]], questa non verra' irradiata equamente in tutte le direzioni: avviene una **concentrazione** dell'energia in una certa direzione.

> L'**EIRP** (_Effective Isotropic Radiated Power_) è la potenza irradiata da un'antenna isotropica equivalente a quella dell'antenna reale in una direzione specifica.

Il _limite di potenza irradiata da una antenna_, stabilito da una certa regolamentazione, _è espresso in EIRP_. Si vuole che l'antenna reale emetta una quantita' di segnale **in tutte le direzioni** che non superi l'EIRP. Ma dato che l'antenna reale non e' isotropica, e' necessario che il raggio concentrato di queste non superi l'EIRP.

Per esempio: un'antenna riceve 16mW di energia, ma in quanto reale (non isotropica) concentra questa energia in una direzione facendole guadagnare 10dB (guadagno passivo) e portando l'energia trasmessa come onda radio a 160mW! Se l'EIRP pero' e' imposto essere 16mW, allora bisognera' abbassare l'energia ricevuta dall'antenna (e quindi l'energia emessa dall'intentional radiator) a 1.6mW.
![[EIRP.png]]

## Referenze