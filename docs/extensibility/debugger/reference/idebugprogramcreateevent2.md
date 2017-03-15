---
title: "IDebugProgramCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramCreateEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugProgramCreateEvent2"
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene inviata dal motore \(DE\) di debug gestione \(SDM\) di debug della sessione quando un programma è associato.  
  
## Sintassi  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE o il fornitore di porte personalizzato implementa questa interfaccia per segnalare che un programma è stato creato, in genere quando il programma è associato.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Lo SDM utilizza il metodo di `QueryInterface` per accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE o il fornitore di porte personalizzato crea e invia questo oggetto evento per notificare la creazione di un programma.  Il DE invia questo evento utilizzando [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è collegato al programma sottoposto a debug.  Il fornitore di porte personalizzato invia l'evento [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) utilizzando l'interfaccia.  
  
## Note  
 Il DE o il fornitore di porte personalizzato pubblica una nuova [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia chiamando [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)