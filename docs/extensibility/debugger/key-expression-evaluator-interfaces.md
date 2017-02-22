---
title: "Interfacce dell&#39;analizzatore di espressioni di espressione chiave | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], la valutazione di espressioni"
  - "valutazione dell'espressione, interfacce"
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfacce dell&#39;analizzatore di espressioni di espressione chiave
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando si scrive un analizzatore di espressioni \(EE\), insieme al contesto di valutazione, è necessario conoscere le interfacce seguenti.  
  
## Descrizioni dell'interfaccia  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Dispone di un singolo metodo, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), che ottiene una struttura di dati che rappresenta il punto di esecuzione corrente. Questa struttura di dati è uno dei tre argomenti che il motore di debug \(DE\) passa il [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) metodo per valutare un'espressione. In genere, questa interfaccia viene implementata dal provider di simboli.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     È il [Operazione di binding](../../extensibility/debugger/reference/idebugbinder-bind.md) metodo, che ottiene l'area di memoria che contiene il valore corrente di un simbolo. Dato sia il metodo che lo contiene, rappresentato da un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) oggetto e il simbolo, rappresentato da un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) oggetto `IDebugBinder::Bind` restituisce il valore del simbolo.`IDebugBinder` è in genere implementato dal DE.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Rappresenta un tipo di dati semplice. Per i tipi più complessi, ad esempio matrici e metodi, utilizzare le [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) e [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfacce, rispettivamente.[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) è un altro importante derivata l'interfaccia che rappresenta i simboli che contiene altri simboli, ad esempio metodi o classi. Il `IDebugField` interfaccia \(e i relativi derivati\) viene in genere implementate dal provider di simboli.  
  
     Un `IDebugField` oggetto può essere utilizzata per trovare il nome e il tipo di un simbolo e, insieme a un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) di oggetto, può essere utilizzato per trovare il relativo valore.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Rappresenta i bit del valore in fase di esecuzione di un simbolo effettivi.[Operazione di binding](../../extensibility/debugger/reference/idebugbinder-bind.md) accetta un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta un simbolo e restituisce un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) oggetto. Il [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) metodo restituisce il valore del simbolo in un buffer di memoria. In genere un DE implementa questa interfaccia per rappresentare il valore di una proprietà in memoria.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Questa interfaccia rappresenta l'analizzatore di espressioni. Il metodo chiave è [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), che restituisce un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaccia.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Questa interfaccia rappresenta un'espressione analizzata pronta per essere valutata. Il metodo chiave è [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) che restituisce un IDebugProperty2 che rappresenta il valore e il tipo dell'espressione.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Questa interfaccia rappresenta un valore e il relativo tipo ed è il risultato della valutazione di un'espressione.  
  
## Vedere anche  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)