---
title: "Implementazione di un analizzatore di espressioni | Microsoft Docs"
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
  - "analizzatori di espressioni"
  - "debug [debug SDK], analizzatori di espressioni"
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementazione di un analizzatore di espressioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Valutazione di un'espressione è un'interazione complicata fra il motore di debug \(DE\), il provider di simboli \(SP\), l'oggetto di associazione e l'analizzatore di espressioni \(EE\) stesso. I quattro componenti sono connessi tramite le interfacce che vengono implementate da un componente e utilizzate da un altro.  
  
 L'analizzatore di Espressioni accetta un'espressione da DE sotto forma di stringa e analizza o valuta. L'analizzatore di Espressioni implementa le interfacce seguenti, che vengono utilizzate dal DE:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 L'analizzatore di Espressioni chiama l'oggetto binder, forniti da DE, per ottenere il valore di simboli e oggetti. L'analizzatore di Espressioni utilizza le interfacce seguenti, che sono implementate dal DE:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 L'analizzatore di Espressioni implementa [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md).`IDebugProperty2` fornisce il meccanismo per la descrizione del risultato della valutazione di un'espressione, ad esempio una variabile locale, una primitiva o un oggetto, a Visual Studio, che consente di visualizzare le informazioni appropriate nella **variabili locali**, **espressioni di controllo**, o **immediato** finestra.  
  
 Il Service Pack viene fornito l'analizzatore di Espressioni dal DE quando vengono richieste informazioni. SP implementa interfacce che descrivono gli indirizzi e campi, ad esempio le interfacce seguenti e i relativi derivati:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 L'analizzatore di Espressioni utilizza tutte queste interfacce.  
  
## In questa sezione  
 [Strategia di implementazione dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definisce un processo in tre fasi per la strategia di implementazione dell'analizzatore di espressioni \(EE\) espressione.  
  
## Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)