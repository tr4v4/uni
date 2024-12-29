---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 08-10-2024 20:28:25
links:
  - "[[Lecture 02102024131913]]"
  - "[[Lecture 09102024132027]]"
  - "[[Lecture 27112024132652]]"
---
# Modello ISO-OSI
---
## Introduzione
> Il **modello ISO-OSI**, anche detto **ISO-OSI RM** (_Open System Interconnection Reference Model_), è il [[Protocollo di rete|protocollo di rete]] standard (_de jure_). Definisce un'_architettura dei protocolli di [[Rete|rete]] organizzata in 7 livelli_, nel quale _ogni livello gestisce una classe di problematiche di rete e fornisce ai livelli superiori una visione della rete semplificata attraverso l'astrazione dei livelli inferiori e l'interfacciamento comune per tutti i protocolli_.

## Livelli
I 7 livelli sono:
1. _[[Livello fisico]]_
2. _[[Livello MAC-LLC]]_
3. _[[Livello rete]]_
4. _[[Livello trasporto]]_
5. _[[Livello sessione]]_
6. _[[Livello presentazione]]_
7. _[[Livello applicazione]]_

<u>Attenzione</u>: in realtà del modello ISO-OSI, nella realtà (de facto), si utilizzano solo 5 di questi livelli, appartenenti allo stack [[Modello TCP-IP|TCP-IP]]:
1. livello fisico
2. livello MAC-LLC
3. livello rete
4. livello trasporto
5. livello applicazione (che comprende, o talvolta ignora, i livelli sessione e presentazione)

<u>Nota bene</u>: infatti oggigiorno i livelli di sessione e di presentazione sono considerati inutili. Erano nati per esigenze che oggi non ci sono più: la _presentazione consisteva nel convertire i dai tra formati diversi_, come il [[Big-endian & Little-endian|Big Endian vs. Little Endian]]; la _sessione per gestire appunto le sessioni di comunicazione_, che risultava però in un appesantimento dello stack.

## Funzionamento
Ogni livello verifica i dati della busta, agisce di conseguenza e passa il contenuto della busta ai livelli superiori. Formalmente si dice che ogni livello fa due operazioni:
- _in fase di trasmissione_ --> **incapsulamento**: aggiunge una busta al contenuto e passa il tutto al livello inferiore;
- _in fase di ricezione_ --> **decapsulamento**: toglie la "sua" busta e restituisce il contenuto al livello superiore.

## Referenze