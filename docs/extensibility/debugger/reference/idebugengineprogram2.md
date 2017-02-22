---
title: "IDebugEngineProgram2 | Microsoft Docs"
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
  - "IDebugEngineProgram2"
helpviewer_keywords: 
  - "Interfaccia IDebugEngineProgram2"
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia fornisce il supporto multithreading di debug.  
  
## Sintassi  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il modulo di debug implementa questa interfaccia per supportare il debug simultaneo di più thread.  Questa interfaccia viene implementata nello stesso oggetto che implementa [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) l'interfaccia.  
  
## Note per i chiamanti  
 Utilizzare per ottenere [QueryInterface](/visual-cpp/atl/queryinterface) questa interfaccia da un'interfaccia di `IDebugProgram2` .  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugEngineProgram2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Interrompi](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Arresta tutti i thread in esecuzione nel programma.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Controlla per l'esecuzione \(oppure interrompere che controlla per l'esecuzione\) per verificare il thread specificato.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Consente di \(o\) impedisce la valutazione di un'espressione si verifichi sul thread specificato, anche se il programma viene arrestato.|  
  
## Note  
 In Visual Studio viene chiamato questa interfaccia in [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) risposta a un evento e impostare su “espressione di controllo per il passaggio del thread„ e “espressione di controllo per la valutazione delle espressioni gli stati sul thread„ del programma.  [Interrompi](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato ogni volta che il programma deve essere un utente; questo metodo fornisce il programma una probabilità terminare tutti i thread.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)