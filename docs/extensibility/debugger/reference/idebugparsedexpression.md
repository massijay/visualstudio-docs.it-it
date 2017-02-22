---
title: "IDebugParsedExpression | Microsoft Docs"
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
  - "IDebugParsedExpression"
helpviewer_keywords: 
  - "Interfaccia IDebugParsedExpression"
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta un'espressione analizzata pronta per essere valutata.  
  
## Sintassi  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## Note per gli implementatori  
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un'espressione analizzata che è pronta per la valutazione.  
  
## Note per chiamanti  
 Una chiamata a [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) restituisce questa interfaccia.  
  
## Metodi nell'ordine Vtable  
 Nella tabella seguente illustra il metodo di `IDebugParsedExpression`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Valuta l'espressione analizzata.|  
  
## Note  
 Quando il chiamante è pronto per la valutazione dell'espressione, chiama [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per restituire un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che contiene il risultato della valutazione. Questo approccio due parti per la valutazione, analisi, la valutazione, consente all'espressione analizzata essere valutate più volte, ignorando il lungo processo di analisi dell'espressione.  
  
## Requisiti  
 Intestazione: ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)