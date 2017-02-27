---
title: "La valutazione delle espressioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "la valutazione di espressioni [Debugging SDK]"
  - "debug [debug SDK], la valutazione di espressioni"
  - "valutazione di espressioni"
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# La valutazione delle espressioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le espressioni vengono create le stringhe passate giù dalle automobili, dall'espressione di controllo, dal Controllo Immediato, o nella finestra controllo immediato.  Quando un'espressione viene valutata, viene generata una stringa stampabile che contiene il nome e il tipo di variabile o argomento e il relativo valore.  Questa stringa viene visualizzata nella finestra corrispondente dell'IDE.  
  
## Implementazione  
 Le espressioni vengono valutate quando un programma è stato interrotto a un punto di interruzione.  L'espressione stessa è rappresentata da un'interfaccia di [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , che rappresenta un'espressione analizzata che è pronta per associare e valutano nel contesto l'espressione di valutazione.  Lo stack frame determina il contesto di valutazione di un'espressione, disponibili nel modulo di gestione di debug \(DE\) implementando l'interfaccia di [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
 Assegnato a un utente la stringa e un'interfaccia di [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un motore di debug \(DE\) possibile ottenere un'interfaccia di [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) passando la stringa dell'utente al metodo di [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) .  l'interfaccia IDebugExpression2 restituita contiene l'espressione analizzata pronta per la valutazione.  
  
 Con l'interfaccia di `IDebugExpression2` , il DE possibile ottenere il valore dell'espressione con la valutazione sincrona o asincrona di espressione, utilizzando [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o di [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  Questo valore, con il nome e il tipo della variabile o degli argomenti, viene inviato all'IDE per la visualizzazione.  Il valore, il nome e il tipo sono rappresentati da un'interfaccia di [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
 Per abilitare la valutazione di un'espressione, un DE necessario implementare le interfacce di [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) e di [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  Sia la valutazione sincrona sia asincrona richiede l'implementazione del metodo di [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
## Vedere anche  
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)