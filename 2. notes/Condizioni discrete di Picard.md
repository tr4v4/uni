---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 10-11-2024 19:41:12
links:
  - "[[Lecture 04112024131513]]"
---
# Condizioni discrete di Picard
---
## Introduzione
> Le **condizioni discrete di Picard** sono uno strumento usato nell'ambito dei [[Problemi inversi|problemi inversi]] per visualizzare l'influenza del rumore $\delta$ nella [[Problema dei minimi quadrati|risoluzione dei minimi quadrati]] del sistema $Ax = y^{\delta}$ attraverso [[Fattorizzazione ai valori singolari|SVD]].

## Visualizzazione
Considerando il vettore $y^{\delta} = y + \delta$, e fattorizzando la matrice $A$ in $A = U \Sigma U^{T}$, allora la soluzione $x^{*}$ è calcolabile come:
$$x^{*} = \sum\limits_{i=1}^{n} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}} v_{i} = \sum\limits_{i=1}^{n} \frac{u_{i}^{T}y}{\sigma_{i}}v_{i} + \sum\limits_{i=1}^{n} \frac{u_{i}^{T}\delta}{\sigma_{i}}v_{i}$$

Ora, considerando i dati reali $y$, visualizziamo un grafico che mette in relazione:
- $\sigma_{i}$, i _valori singolari_;
- $u_{i}^{T}y$, i _coefficienti di Fourier_;
- $\frac{u_{i}^{T}y}{\sigma_{i}}$, i _coefficienti della soluzione_.

![[condizioni-discrete-di-picard-1.png]]

Se invece consideriamo la soluzione i dati con rumore $y^{\delta}$, il grafico risulta essere il seguente:
![[condizioni-discrete-di-picard-2.png]]

Cosa succede? I coefficienti di Fourier ora sono $u_{i}^{T}y^{\delta}$, ovvero $u_{i}^{T}(y + \delta)$, e questo provoca un comportamento del tutto differente della curva rossa nel grafico precedente. **Il rumore**, anche se piccolo, **provoca un generale innalzamento dei coefficienti di Fourier**, che si mantengono nell'ordine di $10^{3}$, quando senza rumore arrivavano anche a $10^{-11}$. Se i coefficienti di Fourier non si abbassano, e i valori singolari (in blu) invece tendono a 0 per le iterazioni $i = 1, \cdots, n$, avviene che **i coefficienti della soluzione (in nero) assumeranno valori sempre più grandi**.

Sono chiamati coefficienti della soluzione perché dovranno moltiplicare i vettori $v_{i}$ per $i = 1, \cdots, n$. Questi vettori, detti _valori singolari destri_, sono delle oscillazioni:
![[condizioni-discrete-di-picard-3.png]]

Quindi **avviene che i coefficienti della soluzione più grandi moltiplicheranno le oscillazioni $v_{i}$ di ampiezza maggiore**. E' da questo che sono generate le oscillazioni della soluzione $x^{*}$!

## Soddisfazione
Quindi, vengono soddisfatte le condizioni discrete di Picard quando i coefficienti di Fourier decrescono più velocemente dei valori singolari. _Se ciò non avviene, i coefficienti della soluzione sono destinati a salire_.

## Referenze