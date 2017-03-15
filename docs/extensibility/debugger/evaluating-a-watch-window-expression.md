---
title: "Valutazione di un&#39;espressione di finestra Espressioni di controllo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Finestra Espressioni di controllo"
  - "Finestra Espressioni di controllo, espressioni"
  - "valutazione dell'espressione, espressioni specificate nelle finestre Espressioni di controllo"
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Valutazione di un&#39;espressione di finestra Espressioni di controllo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando viene sospesa l'esecuzione, Visual Studio chiama il motore di debug \(DE\) per determinare il valore corrente di ogni espressione nell'elenco di espressioni di controllo. Il DE valuta ogni espressione utilizzando un analizzatore di espressioni \(EE\) e viene visualizzato il valore corrispondente in Visual Studio il **espressioni di controllo** finestra.  
  
 Di seguito viene fornita una panoramica di come viene valutata un'espressione di elenco di controllo:  
  
1.  Visual Studio chiama il DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere il contesto di un'espressione che può essere utilizzato per valutare le espressioni.  
  
2.  Per ogni espressione nell'elenco di controllo, Visual Studio chiama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per convertire il testo dell'espressione in un'espressione analizzata.  
  
3.  `IDebugExpressionContext2::ParseText` chiamate [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per svolgere il lavoro effettivo dell'analisi di testo e producono un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto.  
  
4.  `IDebugExpressionContext2::ParseText` Crea un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto e vi inserisce il `IDebugParsedExpression` oggetti al suo interno. Questo si`DebugExpression2` che viene quindi restituito a Visual Studio.  
  
5.  Chiamate di Visual Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) per valutare l'espressione analizzata.  
  
6.  `IDebugExpression2::EvaluateSync` passa la chiamata a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per la valutazione effettiva e produrre un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto restituito in Visual Studio.  
  
7.  Chiamate di Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ottenere il valore dell'espressione che viene quindi visualizzato nell'elenco di controllo.  
  
## Analizzare quindi valutare  
 Poiché l'analisi di un'espressione complessa può richiedere molto più lunga della valutazione, il processo di valutazione di un'espressione è suddiviso in due passaggi: 1\) consente di analizzare l'espressione e 2\) valuta l'espressione analizzata. In questo modo, la valutazione può verificarsi più volte, ma l'espressione deve essere analizzata una sola volta. L'espressione analizzata intermedia viene restituito dal motore di esecuzione in un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) che a sua volta è incapsulato e restituito da DE come un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto. Il `IDebugExpression` oggetto Rinvia tutti della valutazione di `IDebugParsedExpression` oggetto.  
  
> [!NOTE]
>  Non è necessario per un EE rispettare questo processo in due passaggi, anche se Visual Studio si presuppone che questa classe. l'analizzatore di Espressioni può analizzare e valutare nello stesso passaggio quando [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) viene chiamato \(si tratta di funzionamento dell'esempio MyCEE, ad esempio\). Se la lingua può creare espressioni complesse, è consigliabile separare il passaggio di analisi del passaggio di valutazione. Ciò può migliorare le prestazioni nel debugger di Visual Studio quando molte espressioni di controllo vengono visualizzate.  
  
## Contenuto della sezione  
 [Implementazione di esempio della valutazione dell'espressione](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Utilizza l'esempio MyCEE per entrare nel processo di valutazione dell'espressione.  
  
 [La valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Viene illustrato cosa accade dopo un'analisi dell'espressione ha esito positivo.  
  
## Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti passati quando il motore di debug \(DE\) richiede l'analizzatore di espressioni \(EE\).  
  
## Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)