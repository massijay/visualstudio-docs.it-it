---
title: "IDebugBinder | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder"
helpviewer_keywords: 
  - "Interfaccia IDebugBinder"
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugBinder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia consente di associare un campo di simboli, in genere restituito dal provider di simboli, in un contesto di memoria o un oggetto che contiene valore corrente del simbolo.  
  
## Sintassi  
  
```  
IDebugBinder : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia supporta la valutazione dell'espressione e deve essere implementata dal motore di debug \(DE\).  
  
## Note per chiamanti  
 Questa interfaccia viene utilizzata nel processo di valutazione dell'espressione e viene in genere utilizzata nell'implementazione di [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## Metodi nell'ordine Vtable  
 Nella tabella seguente vengono illustrati i metodi di `IDebugBinder`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ottiene il contesto di memoria o un oggetto che contiene valore corrente del simbolo.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina il tipo in fase di esecuzione di un oggetto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Converte un indirizzo di memoria o percorso oggetto in un contesto di memoria.|  
|[GetFunctionObject](../Topic/IDebugBinder::GetFunctionObject.md)|Ottiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) oggetto utilizzato per creare parametri di funzione.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ottiene il tipo esatto per una variabile.|  
  
## Note  
 Questa interfaccia restituisce gli oggetti utilizzati dall'analizzatore di espressioni in strutture di analisi. L'analizzatore di espressioni analizza un'espressione tramite il provider di simboli per convertire i simboli nell'espressione alle istanze di [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), che descrivono ogni simbolo in termini il tipo e la posizione nel codice sorgente. Il [Operazione di binding](../../../extensibility/debugger/reference/idebugbinder-bind.md) metodo converte `IDebugField` oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti collegare o associare un simbolo di tipo a un valore effettivo in memoria. Questi `IDebugObject` gli oggetti vengono quindi archiviati in un albero di analisi per la valutazione successiva.  
  
## Requisiti  
 Intestazione: ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)