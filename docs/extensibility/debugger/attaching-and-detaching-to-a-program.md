---
title: "Collegamento e scollegamento di un programma | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motori di debug, connessione a programmi"
  - "motori di debug, la disconnessione da programmi"
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Collegamento e scollegamento di un programma
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Connettere il debugger può inviare la sequenza corretta di metodi ed eventi agli attributi appropriati.  
  
## Sequenza di metodi ed eventi  
  
1.  L'amministratore \(SDM\) di debug della sessione chiama [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) il metodo.  
  
     In base al modello \(DE\) di processo il motore di debug, il metodo di `IDebugProgramNodeAttach2::OnAttach` restituisce uno dei metodi seguenti, che determina ciò che si verifica dopo.  
  
     Se `S_FALSE` viene restituito, il motore di debug è in stato connesso al programma.  In caso contrario, [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) viene chiamato il metodo per completare il processo di connessione.  
  
     Se `S_OK` viene restituito, il DE deve essere caricato nello stesso processo di SDM.  Lo SDM esegue le attività seguenti:  
  
    1.  Chiama [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni del motore di DE.  
  
    2.  viene creato il DE.  
  
    3.  Chiama [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  Il DE invia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) a SDM con un attributo di `EVENT_SYNC` .  
  
3.  Il DE invia [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a SDM con un attributo di `EVENT_SYNC` .  
  
4.  Il DE invia [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM con un attributo di `EVENT_SYNC_STOP` .  
  
 Tramite rimozione da un programma è un processo semplice e in due fasi, come segue:  
  
1.  le chiamate di SDM [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  Il DE. [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)