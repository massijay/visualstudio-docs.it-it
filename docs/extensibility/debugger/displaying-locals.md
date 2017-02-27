---
title: "Visualizzazione di variabili locali | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], la valutazione di espressioni"
  - "valutazione dell'espressione, la visualizzazione delle variabili locali"
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Visualizzazione di variabili locali
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Sempre l'esecuzione avviene all'interno del contesto di un metodo, noto anche come metodo che contiene o il metodo corrente. Quando viene sospesa l'esecuzione, Visual Studio chiama il motore di debug \(DE\) per ottenere un elenco delle variabili locali e argomenti, collettivamente le variabili locali del metodo. Visual Studio visualizza le variabili locali e i relativi valori di **variabili locali** finestra.  
  
 Per visualizzare variabili locali, chiama il DE la [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metodo appartenente all'analizzatore di Espressioni e fornisce un contesto di valutazione, ovvero, un provider di simboli \(SP\), l'indirizzo di esecuzione corrente e un oggetto di associazione. Per altre informazioni, vedere [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md). Se la chiamata ha esito positivo, il `IDebugExpressionEvaluator::GetMethodProperty` metodo restituisce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta il metodo che contiene l'indirizzo di esecuzione corrente.  
  
 Le chiamate DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) oggetto, che viene filtrato in modo da restituire soli variabili locali ed enumerato per produrre un elenco di [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) strutture. Ogni struttura contiene nome, tipo e il valore di una variabile locale. Il tipo e il valore vengono archiviati come stringhe formattate, adatte per la visualizzazione. Il nome, tipo e valore sono in genere visualizzati insieme in una riga di **variabili locali** finestra.  
  
> [!NOTE]
>  Il **controllo immediato** e **espressioni di controllo** windows visualizzate anche le variabili con lo stesso formato di nome, valore e tipo. Tuttavia, tali valori vengono ottenuti chiamando [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anziché `IDebugProperty2::EnumChildren`.  
  
## In questa sezione  
 [Esempio di implementazione di variabili locali](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Alcuni esempi di utilizzo per entrare nel processo di implementazione di variabili locali.  
  
## Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Viene illustrato che quando il motore di debug \(DE\) chiama l'analizzatore di espressioni \(EE\), vengano passati tre argomenti.  
  
## Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)