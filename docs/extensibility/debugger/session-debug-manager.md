---
title: "Gestione sessione di Debug | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestione di debug di sessione, unificare le visualizzazioni di sessione"
  - "gestione di debug di sessione, la trasmissione"
  - "debug Gestione sessione di debug [debug SDK]"
  - "Gestione sessione di debug"
  - "gestione di debug di sessione, eseguire il debug multiplexing motore"
  - "gestione di debug di sessione, la delega"
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Gestione sessione di Debug
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'amministratore \(SDM\) di debug della sessione gestisce un numero qualsiasi dei motori di \(DE\) debug che esegue il debug di qualsiasi numero di programmi in più processi su qualsiasi numero di computer.  Oltre a essere un multiplexor del motore di debug, lo SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.  
  
## Operazione di amministratore di Debug della sessione  
 L'amministratore \(SDM\) di debug della sessione gestisce il DE.  Possono essere presenti più di un funzionamento del motore di debug su un computer contemporaneamente.  Per eseguire il multiplexing DES, il wrapping di SDM una serie di interfacce dal DES e li espone all'IDE come una singola interfaccia.  
  
 Per migliorare le prestazioni, alcune interfacce non sono in multiplexing.  Al contrario, vengono utilizzati direttamente da DE e le chiamate a queste interfacce non superano con lo SDM.  Ad esempio, le interfacce utilizzate con la memoria, il codice e i contesti di documento non sono in multiplexing, poiché fanno riferimento a un'istruzione, alla memoria, o a un documento specifico in un programma specifico eseguito il debug da un DE specifico.  Nessun altro DE necessario prendere parte a tale livello di comunicazione.  
  
 Ciò non vale per tutti i contesti.  Le chiamate all'interfaccia del contesto di valutazione di espressioni passano con lo SDM.  Durante la valutazione di un'espressione, lo SDM esegue il wrapping [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) dell'interfaccia che fornisce all'IDE poiché quando tale espressione viene valutata, può comportare DES multipli che è programmi di debug nello stesso processo che potrebbe essere in esecuzione sullo stesso thread.  
  
 Lo SDM in genere funge da meccanismo di delega, ma può essere utilizzato come meccanismo di trasmissione.  Ad esempio, durante la valutazione di un'espressione, lo SDM funge da meccanismo di trasmissione per notificare al DES che possono eseguire il codice su un thread specificato.  Analogamente, quando lo SDM riceve un evento bloccato, trasmette a tutti i programmi che devono l'arresto dell'esecuzione.  Quando un passaggio viene chiamato, lo SDM trasmette a tutti i programmi che possono continuare l'esecuzione.  I punti di interruzione sono anche trasmessi a ogni DE.  
  
 Lo SDM non tiene traccia del programma corrente, il thread, o lo stack frame.  Il processo, il programma e le informazioni del thread viene inviato a SDM insieme agli eventi di debug specifici.  
  
## Vedere anche  
 [Il motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)