---
title: "IDebugProgramDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProgramDestroyEvent2"
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene inviata dal motore \(DE\) di debug gestione \(SDM\) di debug della sessione quando un programma è stata completata.  
  
## Sintassi  
  
```  
IDebugProgramDestroyEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE o il fornitore di porte personalizzato implementa questa interfaccia per segnalare che un programma è stato interrotto e non sarà più disponibile per il debug.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE o il fornitore di porte personalizzato crea e invia questo oggetto evento per notificare la chiusura di un programma.  Il DE invia questo evento utilizzando [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è collegato al programma sottoposto a debug.  Il fornitore di porte personalizzato invia l'evento [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) utilizzando l'interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente viene illustrato il metodo di `IDebugProgramDestroyEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md)|Ottiene il codice di uscita del programma.|  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)