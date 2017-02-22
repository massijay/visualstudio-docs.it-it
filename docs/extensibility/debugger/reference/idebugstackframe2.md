---
title: "IDebugStackFrame2 | Microsoft Docs"
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
  - "IDebugStackFrame2"
helpviewer_keywords: 
  - "Interfaccia IDebugStackFrame2"
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un unico stack frame nello stack di chiamate in un thread specifico.  
  
## Sintassi  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## Note per gli implementatori  
 il motore di debug \(DE\) implementa questa interfaccia per rappresentare uno stack frame.  
  
## Note per i chiamanti  
 Chiamare [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) recuperare un'interfaccia.  Chiamare [Successivo](../Topic/IEnumDebugFrameInfo2::Next.md) per [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) recuperare una struttura che contiene l'interfaccia di `IDebugStackFrame2` .  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugStackFrame2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|ottiene il contesto di codice per questo stack frame.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ottiene il contesto del documento per questo stack frame.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Ottiene il nome dello stack frame.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Ottiene una descrizione dello stack frame.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Ottiene una rappresentazione computer\-dipendente l'intervallo di indirizzi virtuali associata a uno stack frame.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Ottiene un contesto di valutazione per eseguire la valutazione di espressioni nel contesto corrente di uno stack frame e stack di un thread.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Ottiene il linguaggio associato a uno stack frame.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Ottiene una descrizione delle proprietà associata a uno stack frame.|  
|[EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)|Crea un enumeratore per le proprietà dello stack frame.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Ottiene il thread associato a uno stack frame.|  
  
## Note  
 Questa interfaccia viene ottenuta solo quando il programma sottoposto a debug è stato interrotto a un punto di interruzione \(causato da un punto di interruzione utente\-impostato o un'eccezione\).  Da questa interfaccia, un contesto dell'espressione può essere ottenuto valutare le espressioni, un elenco dei registri può essere restituito, o lo stack di chiamate è possibile ottenere e esaminato.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)