---
title: "IDebugStackFrame3 | Microsoft Docs"
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
  - "IDebugStackFrame3"
helpviewer_keywords: 
  - "Interfaccia IDebugStackFrame3"
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia estende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) per gestire le eccezioni rilevate.  
  
## Sintassi  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia lo stesso oggetto che implementa [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) l'interfaccia per supportare le eccezioni rilevate.  
  
## Note per i chiamanti  
 chiamata [QueryInterface](/visual-cpp/atl/queryinterface) su un'interfaccia di `IDebugStackFrame2` per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi ereditati da [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gestisce un'eccezione per lo stack frame corrente prima di qualsiasi gestione delle eccezioni normale.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Restituisce un contesto di codice se uno stack viene rimosso è stato di verifica.|  
  
## Note  
 Un'eccezione intercettata significa che un debugger può elaborare un'eccezione prima che tutte le routine standard di gestione delle eccezioni sono chiamate dal runtime.  I mezzi di intercettazione di un'eccezione essenzialmente che hanno il runtime fingono che vi sia presente un gestore di eccezioni anche quando non c " è.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) viene chiamato durante tutti gli eventi di callback di eccezione normale \(l'unica eccezione è se il codice misto di debug \(gestito e codice non gestito, nel qual caso l'eccezione non è possibile intercettare durante il callback dell'ultima vendita potrebbe\).  se il DE non implementa `IDebugStackFrame3`, o il DE restituisce un errore da IDebugStackFrame3::`InterceptCurrentException` \(come `E_NOTIMPL`\), il debugger gestisce l'eccezione generale.  
  
 Intercettando un'eccezione, il debugger può consentire all'utente vengano apportate modifiche allo stato del programma sottoposto a debug e quindi riattivi l'esecuzione nel punto in cui l'eccezione è stata generata.  
  
> [!NOTE]
>  Le eccezioni individuate sono consentite solo nel codice gestito, ovvero, in un programma in esecuzione nel Common Language \(CLR\) Runtime.  
  
 Il modulo di debug indica che supporta le eccezioni di intercettazione impostando “i metricExceptions„ a un valore 1 in fase di esecuzione utilizzando la funzione di `SetMetric` .  Per ulteriori informazioni, vedere [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)