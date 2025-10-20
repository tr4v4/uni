---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 17:33:18
links:
---
# Bridge pattern
---
## Introduzione
> Il **bridge**, come l'[[Adapter|adapter]], è un [[Design patterns strutturali|design pattern strutturale]] usato per separare l'interfaccia di una classe dalla sua reale implementazione, _nascondendo l'[[Implementazione|implementazione]] dall'[[Interfaccia|interfaccia]]_.

Il suo obiettivo è quello di **interfacciare le interfacce e le loro implementazioni in modo da renderle ugualmente interscambiabili, senza dover fare tutte le combinazioni possibile tra di esse**.

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[bridge-uml.png]]

Fondamentalmente, il bridge lo fa `Abstraction`, in quanto contiene un'implementazione **generica** `Implementor` e consente al client di usare i metodi definiti dall'interfaccia che saranno passati alla generica implementazione, che a seconda del suo tipo concreto eseguirà l'operazione chiamata.

L'esempio perfetto è con `Device`, interfaccia generica per `Tv`, `Radio`, `Stereo`, ecc..., e `RemoteController`, che è l'interfaccia _bridge_ di `Device`, che contiene (_aggregazione_) un `Device` generico. I metodi esposti di `RemoteController` sono invocati sul `Device`, e quindi eseguiti da qualche sua implementazione. La cosa interessante è la possibilità di creare il `NewRemoteController`, che è una versione rifinita di `RemoteController` ([[Sottotipaggio|sottoclasse]]) che definisce nuovi metodi ma si interfaccia perfettamente con `Device`.

## Referenze