---
title: "IDebugExpressionContext2 | Microsoft Docs"
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
  - "IDebugExpressionContext2"
helpviewer_keywords: 
  - "Interfaccia IDebugExpressionContext2"
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un contesto per la valutazione di espressioni  
  
## Sintassi  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## Note per gli implementatori  
 il motore di debug \(DE\) implementa questa interfaccia per rappresentare un contesto in cui un'espressione può essere valutata.  
  
## Note per i chiamanti  
 Una chiamata [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) a restituisce la questa interfaccia.  Questa interfaccia è accessibile solo quando il programma sottoposto a debug è stato messo in pausa e uno stack frame è disponibile.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugExpressionContext2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetName](../Topic/IDebugExpressionContext2::GetName.md)|Recupera il nome del contesto di valutazione.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analizza un'espressione basata su testo per la valutazione.|  
  
## Note  
 Un contesto di valutazione può essere considerato come ambito per eseguire la valutazione di espressioni.  
  
 Quando un programma è stato interrotto, l'amministratore \(SDM\) di debug della sessione ottiene uno stack frame da DE con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  Le chiamate di SDM quindi [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere l'interfaccia di `IDebugExpressionContext2` .  Questo è seguito da una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) creare un'interfaccia, che rappresenta l'espressione analizzata pronta per essere valutato.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)