---
title: "IDebugProgram3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugProgram3"
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugProgram3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un programma in esecuzione in un processo ed esteso [Esegui](../../../extensibility/debugger/reference/idebugprogram2-execute.md) fornendo informazioni del thread.  
  
## Sintassi  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug e un fornitore di porte personalizzato implementare questa interfaccia per rappresentare un programma in un processo.  L'amministratore \(SDM\) di debug della sessione implementa anche l'interfaccia per fornire informazioni a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## Note per i chiamanti  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) L'evento restituisce questa interfaccia per creare un nuovo programma.  Questa interfaccia viene utilizzata come parametro per molti metodi su più interfacce.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugProgram3`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|esegue il programma.  Il thread viene restituito per fornire al debugger le informazioni sui quali il thread l'utente accede quando viene eseguita.|  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Note  
 Un programma è un funzionamento del contenitore del thread in un'architettura di runtime particolare, mentre un processo è costituito da uno o più programmi.  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [Successivo](../Topic/IEnumDebugPrograms2::Next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)