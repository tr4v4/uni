---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2024 20:49:41
links:
  - "[[Lecture 01102024110253]]"
---
# Sistema di transizione
---
## Introduzione
> Un **sistema di transizione** è un modello matematico usato nella [[Semantica operazionale strutturata|semantica operazionale strutturata]] per _"dare" [[Semantica|semantica]] ([[Semantica dinamica|dinamica]]) alla [[Sintassi|sintassi]]_.
> Formalmente è una tripla
> $$(\Gamma, T, \to)$$
> dove:
> - $\Gamma$ è l'_insieme di stati/configurazioni_ (possibilmente infinito);
> - $T \subseteq \Gamma$ è l'_insieme degli stati terminali_;
> - $\to \subseteq \Gamma \times \Gamma$ è la _[[Relazione|relazione]] di transizione_ (da uno stato all'altro).

## Struttura
### $\sigma$
Se un sistema di transizione deve dare significato alla sintassi di un linguaggio, è necessario introdurre un oggetto **store** che mantenga lo stato del programma.
Questo viene fatto introducendo una funzione che associ ad ogni variabile del linguaggio un numero intero
$$\sigma: \text{Var} \to \mathbb{N}$$
e definendo allora lo store come
$$\text{Store} = \{\sigma | \sigma: \text{Var} \to \mathbb{N}\}$$
ossia come l'_insieme delle associazioni variabile-valore_.

Se supponiamo che $\text{Var} = \{x_{1}, \cdots, x_{k}\}$, allora lo store $\sigma$ può essere annotato secondo la definizione di [[Sostituzione|sostituzione]] come:
$$\sigma = \{x_{1}/n_{1}, \cdots, x_{k}/n_{k}\}$$

### $\Gamma$
Abbiamo detto che l'insieme degli stati $\Gamma$ è solitamente un infinito, [[Numerabilità|contabile]]. E' allora _necessario rappresentarlo in modo finito_: lo facciamo con le [[Grammatiche libere|grammatiche libere]].

In particolare, fissata la categoria sintattica del sistema di transizione (descritta da una grammatica libera), _questa verrà associato un insieme di stati $\Gamma$_, che sarà l'insieme delle coppie di un'espressione sintattica $\text{Expr}$ appartenente alla categoria (in grammatica libera) con la sua funzione di store $\sigma$:
$$\Gamma_{e} = \{(e, \sigma) | e \in \text{Expr}, \sigma \in \text{Store}\}$$

### $\to$
Per descrivere questo insieme, che solitamente si compone di infinite coppie di stati, anche in questo caso, fissata la categoria sintattica del sistema di transizione, è _necessario trovare una rappresentazione finita implicita come minima relazione che soddisfi un certo insieme finito di [[Assioma|assiomi]] e [[Regole di inferenza|regole d'inferenza]]_.

## Referenze
- [[Computazione]]