---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 05-11-2023 22:47:30
links:
  - "[[Lecture 02112023130607]]"
---
# Trap
---
## Definizione
> Una **trap** è una [[Invocazione di procedura|chiamata di procedura]] _automatica_ effettuata quando si verificano 2 eventi particolari:
> - _[[Istruzioni ISA#Composizione|opcode]] non definito_
> - _accesso ad area di memoria non consentito_
> 
> Al verificarsi di uno di questi eventi il controllo viene trasferito a una specifica procedura chiamata **gestore di trap**.

Il _gestore di trap_ potrebbe, per esempio, comunicare l'errore al processo che l'ha scatenato e non restituirgli più il controllo.

## Referenze