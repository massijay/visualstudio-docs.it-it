---
title: "L&#39;avvio del Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK], l'avvio del debugger"
  - "l'avvio di debugger [Debugging SDK]"
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# L&#39;avvio del Debugger
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Avviare il debugger può inviare la sequenza corretta di metodi ed eventi con i relativi attributi appropriati.  
  
## Sequenze di metodi ed eventi  
  
1.  L'amministratore \(SDM\) di debug della sessione viene chiamato dal menu Debug e scegliendo **Avvia**.  Per ulteriori informazioni, vedere [Avviare un programma](../../extensibility/debugger/launching-a-program.md).  
  
2.  Lo SDM chiama [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) il metodo.  
  
3.  In base al modello \(DE\) di processo il motore di debug, il metodo di `IDebugProgramNodeAttach2::OnAttach` restituisce uno dei metodi seguenti, che determina ciò che si verifica dopo.  
  
     Se `S_FALSE` viene restituito, il motore di debug \(DE\) deve essere caricato in corso della macchina virtuale.  
  
     In alternativa  
  
     Se `S_OK` viene restituito, il DE deve essere caricato in corso di SDM.  Lo SDM quindi esegue le attività seguenti:  
  
    1.  Chiama [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni del motore di DE.  
  
    2.  viene creato il DE.  
  
    3.  Chiama [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Il DE invia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) a SDM con un attributo di `EVENT_SYNC` .  
  
5.  Il DE invia [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a SDM con un attributo di `EVENT_SYNC` .  
  
6.  Il DE invia [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) a SDM con un attributo di `EVENT_SYNC` .  
  
7.  Il DE invia [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM con un attributo di `EVENT_SYNC` .  
  
8.  Il DE invia [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) a SDM con un attributo di `EVENT_SYNC` .  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)   
 [Avviare un programma](../../extensibility/debugger/launching-a-program.md)