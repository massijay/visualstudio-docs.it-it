---
title: "IDebugExceptionEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugExceptionEvent2"
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Il motore \(DE\) di debug invia questa interfaccia gestione \(SDM\) di debug della sessione quando viene generata un'eccezione nel programma attualmente eseguito.  
  
## Sintassi  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per segnalare che si è verificata nel programma sottoposto a debug.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento per notificare un'eccezione.  L'evento viene inviato [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) mediante la funzione di callback che viene fornita da SDM quando è collegato al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugExceptionEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetException](../Topic/IDebugExceptionEvent2::GetException.md)|Ottiene informazioni dettagliate sull'eccezione che ha generato l'evento.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Ottiene una descrizione leggibile per l'eccezione generata un'eccezione che ha generato l'evento.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina se il motore di \(DE\) debug supporta la possibilità di passare questa eccezione al programma in corso il debug quando l'esecuzione riprende.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Specifica se l'eccezione debba essere passata al programma sottoposto a debug durante l'esecuzione riprende, o se l'eccezione viene rimossa.|  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Note  
 Prima di inviare l'evento, i controlli di DE per verificare se questo evento di eccezione è stato definito in una first\-chance o a un'eccezione second\-chance da una chiamata precedente a [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md).  Se è stata definita come un'eccezione first\-chance, l'evento di `IDebugExceptionEvent2` viene inviato a SDM.  In caso contrario, il DE fornisce all'applicazione una possibilità di gestire l'eccezione.  Se nessun gestore di eccezioni viene fornito e se l'eccezione è stata definita come eccezioni second\-chance, l'evento di `IDebugExceptionEvent2` viene inviato a SDM.  In caso contrario, il DE riprende l'esecuzione del programma e il sistema operativo o il runtime gestisce l'eccezione.  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)