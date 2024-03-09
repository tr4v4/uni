---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 25-11-2023 14:31:25
links:
  - "[[Lecture 22112023151203]]"
---
# Compilazione a 2 livelli
---
## Introduzione
> La **compilazione a 2 livelli** è un tipo di [[Workflow di compilazione|compilazione]] che prevede che la _fase di traduzione avvenga prima dal linguaggio ad alto livello a un linguaggio [[Virtual machine|virtual machine]], e che poi questo venga tradotto a sua volta in linguaggio [[Assembly|assembly]]_.

Questo garantisce _modularità_ e _portabilità_, proprietà non valide per la [[Compilazione diretta|compilazione diretta]]. In particolare portabilità perché **la prima fase di compilazione produce un codice che è valido per ogni tipo di architettura**, per l'appunto virtualizzato dall'implementazione fisica dell'elaboratore. Il codice VM può essere esportato, eseguito su ogni macchina: **ogni architettura per eseguirlo lo compilerà a sua volta nel suo specifico [[ISA]]**.

### Esempio
La [[JVM]] di [[Java]] è un esempio di compilazione a 2 livelli: una prima fase di traduzione consente di creare file `.jar`, che per essere eseguiti devono essere a loro volta compilati in codice oggetto.

## Referenze