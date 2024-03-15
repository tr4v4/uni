---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 15-03-2024 16:03:33
links:
  - "[[Lecture 12032024111356]]"
---
# Generics
---
## Introduzione
> Un **generic** in [[Java]] è un _[[Tipi di dati|tipo di dato]] per l'appunto generico_, _utile per definire classi che operano su tipi di dati differenti_. Questo ci permette di [[Astrazione|astrarre]] ancora di più delle classi e dei metodi.

La sintassi per definire una classe generic è `NomeDellaClasse<T>`. Alcune [[Interfaccia|interfacce]] possono essere generic, come `Comparable<T>`.

## Imposizione di vincoli
E' anche possibile imporre delle restrizioni sul tipo di dato generic della classe. Per esempio _su una classe che implementa [[Algoritmo di ordinamento|algoritmi di ordinamento]], è inutile prendere in input array di oggetti non confrontabili e quindi non ordinabili secondo un certo criterio_. Si può allora imporre una restrizione con la seguente sintassi: `public class NomeDellaClasse<T extends Comparable<T>>`. In questo modo la classe `NomeDellaClasse` prenderà dei generici tipi `T` che siano di tipo `Comparable`, e che quindi possono essere confrontati (con il metodo `compareTo`).

## Limiti
**Non è possibile allocare un array di generics**. Questo perché il tipo degli array è verificato a runtime, mentre i generici sono sostituiti durante la compilazione (dove c'è `T` viene tutto sostituito con il tipo istanziato). Questo conflitto può essere risolto con due metodi che ci permettono alla fine di ottenere array di generici.

### 1° metodo
```java
T[] array;
@SuppressWarnings("unchecked")
T[] tmp = (T[]) new Object[size];
array = tmp;
```

O se si vuole imporre un vincolo sul tipo dei generici, come `T extends Comparable<T>`, allora si dovrà dichiarare non un `Object` ma un `Comparable`:
```java
T[] array;
@SuppressWarnings("unchecked")
T[] tmp = (T[]) new Comparable[size];
array = tmp;
```

### 2° metodo
```java
Object[] array;
@SuppressWarnings("unchecked")
T data = (T) array[i];
return data;
```

## Metodi statici
I tipi generics non possono essere referenziati in un contesto statico, per cui bisogna usare una speciale keyword nella firma del metodo per rendere possibile ciò: `public static <T extends Comparable<T>> void sort(T[] A);`.

## Referenze