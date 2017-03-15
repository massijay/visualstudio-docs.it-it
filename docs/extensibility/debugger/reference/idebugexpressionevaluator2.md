---
title: "IDebugExpressionEvaluator2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugExpressionEvaluator2"
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluator2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Rappresenta una versione avanzata di un analizzatore di espressioni \(EE\).  
  
## Sintassi  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata da un analizzatore di espressioni.  
  
## Metodi  
 Oltre ai metodi nel [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Recupera un oggetto servizio dato il relativo identificatore univoco.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Precarica i moduli designati dal provider del simbolo specificati.|  
|[SetCallback](../Topic/IDebugExpressionEvaluator2::SetCallback.md)|Consente l'analizzatore di espressioni \(EE\) specificare l'interfaccia di callback, che il motore del debugger \(DE\) verrà utilizzato per leggere le impostazioni metriche.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Imposta il percorso di common language runtime \(CLR\) caricato nel debugger.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Consente un motore di debug passare un callback dell'analizzatore di espressioni durante l'inizializzazione.|  
|[Termina](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Arresta e pulisce l'analizzatore di espressioni.|  
  
## Requisiti  
 Intestazione: Ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll