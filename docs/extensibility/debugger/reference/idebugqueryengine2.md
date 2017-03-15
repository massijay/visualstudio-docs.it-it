---
title: "IDebugQueryEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugQueryEngine2"
helpviewer_keywords: 
  - "Interfaccia IDebugQueryEngine2"
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfacciaamministratore \(SDM\) di debug della sessione recuperare un'interfaccia che rappresenta il motore di debug \(DE\).  
  
## Sintassi  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia negli oggetti che implementano la maggior parte di common DE interfaces \( [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)ad esempio, [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)e [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)\) per consentire l'accesso [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) all'interfaccia di DE stesso.  
  
## Note per i chiamanti  
 Chiamare [QueryInterface](/visual-cpp/atl/queryinterface) su un'interfaccia tipica di DE per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugQueryEngine2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetEngineInterface](../Topic/IDebugQueryEngine2::GetEngineInterface.md)|Ottiene un'interfaccia del \(DE\) motore di debug.|  
  
## Note  
 Questa interfaccia in genere viene implementata nell'oggetto che implementa [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) l'interfaccia per supportare l'esecuzione di istruzioni causalità\-ordinata con le funzioni; ovvero quando il debugger è l'uscita da una funzione, la funzione successiva da eseguire non può essere la funzione precedente nello stack ma una funzione in un altro thread nel suo complesso.  Per una definizione di “causalità„, vedere [Glossario di Debugger di Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)