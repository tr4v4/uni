---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 21-10-2025 14:30:57
links:
  - "[[Lecture 14052025105842]]"
---
# Type erasure
---
## Introduzione
> La **type erasure** è il meccanismo usato da [[Java]] per implementare i [[Generics|generici]].

## Funzionamento
In fase di compilazione il **[[Compilatore|compilatore]] cancella tutti i parametri di tipo dal codice** (es. `Set<T>` diventa semplicemente `Set`) e **tutti i tipi parametrici diventano istanze del tipo `Top` di Java, ovvero `Object`**.

## Limiti
Non possiamo fare `new T()` perché il compilatore non sa che oggetto creare. Allo stesso modo, non funziona bene il meccanismo della [[Reflection|reflection]], ossia `instanceof`, perché non si è in grado di distinguere tra `Set<Integer>` e `Set<String>`[^1].

## Wildcards
Per esprimere le relazioni di [[Covarianza e controvarianza|varianza]] sui generici, Java ha introdotto la wildcard `?`, per indicare:
- `T<? extends S>` consente l'uso di `S` e dei suoi sottotipi;
- `T<? super S>` consente l'uso di `S` e dei suoi supertipi.

## Referenze

[^1]: si può usare la tecnica della **reificazione**
