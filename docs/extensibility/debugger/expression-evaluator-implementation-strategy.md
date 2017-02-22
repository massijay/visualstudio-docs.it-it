---
title: "Strategia di implementazione dell&#39;analizzatore di espressioni | Microsoft Docs"
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
  - "valutazione dell'espressione, strategia di implementazione"
  - "motori di debug, strategie di implementazione"
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Strategia di implementazione dell&#39;analizzatore di espressioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Un approccio per creare rapidamente un analizzatore di espressioni \(EE\) consiste nell'implementare il codice minimo necessario per visualizzare le variabili locali nel **variabili locali** finestra. È utile tenere presente che ogni riga di **variabili locali** finestra vengono visualizzati nome, tipo e il valore di una variabile locale e che tutti e tre sono rappresentate da un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto. Nome, tipo e il valore di una variabile locale può essere ottenuti da un `IDebugProperty2` oggetto chiamando il relativo [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metodo. Per ulteriori informazioni sulla modalità di visualizzazione delle variabili locali all'interno di **variabili locali** finestra, vedere [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md).  
  
## Discussione  
 Una possibile implementazione che inizia con implementazione [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Il [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metodi devono essere implementate per visualizzare variabili locali. La chiamata `IDebugExpressionEvaluator::GetMethodProperty` restituisce un `IDebugProperty2` oggetto che rappresenta un metodo: vale a dire un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) oggetto. Metodi non vengono visualizzati di **variabili locali** finestra.  
  
 Il [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metodo deve essere implementato successivamente. Il motore di debug \(DE\) chiama questo metodo per ottenere un elenco di argomenti e variabili locali passando `IDebugProperty2::EnumChildren` un `guidFilter` argomento di `guidFilterLocalsPlusArgs`.`IDebugProperty2::EnumChildren` chiamate [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinare i risultati in una singola enumerazione. Per altre informazioni, vedere [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md).  
  
## Vedere anche  
 [Implementazione di un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)