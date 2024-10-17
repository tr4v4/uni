---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 13-10-2024 13:44:01
links:
---
# Base64
---
## Introduzione
> **Base64** è un tipo di _transfer encoding_ [[MIME]] suggerito per dati binari o multi-byte.

Identifica un sottoinsieme di 64 caratteri [[ASCII]] sicuri, che sono: le minuscole, le maiuscole, i numeri e i caratteri `+` e `/`.

## Funzionamento
Ogni flusso di dati viene suddiviso in blocchi di 24 bit (3 byte). A loro volta questi 24 bit sono suddivisi in 4 blocchi di 6 bit ciascuno e codificati secondo una tabella prefissata in uno dei 64 caratteri già descritti.

![[base64-funzionamento.png]]

La stringa risultante viene divisa in righe di 76 caratteri (tranne l'ultima, che è lunga quanto deve essere) con l'aggiunta di `CRLF`.

<u>Nota bene</u>: la decodifica di base64 è algoritmica, banale, non usa chiavi né calcoli di particolari complessità --> **base64 non è una tecnica crittografica**!

## Referenze