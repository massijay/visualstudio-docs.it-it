---
title: "Implementazione di esempio della valutazione dell&#39;espressione | Microsoft Docs"
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
  - "valutazione dell'espressione, esempi"
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementazione di esempio della valutazione dell&#39;espressione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Per un **espressioni di controllo** espressione finestra, Visual Studio chiama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per produrre un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) oggetto.`IDebugExpressionContext2::ParseText` Crea un'istanza di un analizzatore di espressioni \(EE\) e chiama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per ottenere un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) oggetto.  
  
 Questa implementazione di `IDebugExpressionEvaluator::Parse` esegue le attività seguenti:  
  
1.  \[Solo C\+\+\] Analizza l'espressione per cercare errori.  
  
2.  Crea un'istanza di una classe \(chiamato `CParsedExpression` in questo esempio\) che implementa il `IDebugParsedExpression` l'interfaccia e vengono archiviati nella classe l'espressione deve essere analizzato.  
  
3.  Restituisce il `IDebugParsedExpression` interfaccia il `CParsedExpression` oggetto.  
  
> [!NOTE]
>  Negli esempi che seguono e nell'esempio di MyCEE, l'analizzatore di espressioni non separa l'analisi dalla valutazione.  
  
## Codice gestito  
 Questa è un'implementazione di `IDebugExpressionEvaluator::Parse` nel codice gestito. Si noti che questa versione del metodo rinvia l'analisi di [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) come valuta inoltre il codice per l'analisi allo stesso tempo \(vedere [La valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)\).  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT Parse( string                 expression, uint                   parseFlags, uint                   radix, out string                 errorMessage, out uint                   errorPosition, out IDebugParsedExpression parsedExpression) { errorMessage = ""; errorPosition = 0; parsedExpression = new CParsedExpression(parseFlags, radix, expression); return COM.S_OK; } } }  
```  
  
## Codice non gestito  
 Questa è un'implementazione di `IDebugExpressionEvaluator::Parse` nel codice non gestito. Questo metodo chiama una funzione di supporto, `Parse`, analizzare l'espressione e il controllo degli errori, ma questo metodo ignora il valore risultante. La valutazione formale viene posticipata per [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) in cui l'espressione viene analizzato quando viene valutata \(vedere [La valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)\).  
  
```cpp#  
STDMETHODIMP CExpressionEvaluator::Parse( in    LPCOLESTR                 pszExpression, in    PARSEFLAGS                flags, in    UINT                      radix, out   BSTR                     *pbstrErrorMessages, inout UINT                     *perrorCount, out   IDebugParsedExpression  **ppparsedExpression ) { if (pbstrErrorMessages == NULL) return E_INVALIDARG; else *pbstrErrormessages = 0; if (pparsedExpression == NULL) return E_INVALIDARG; else *pparsedExpression = 0; if (perrorCount == NULL) return E_INVALIDARG; HRESULT hr; // Look for errors in the expression but ignore results hr = ::Parse( pszExpression, pbstrErrorMessages ); if (hr != S_OK) return hr; CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression ); if (!pparsedExpr) return E_OUTOFMEMORY; hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression, reinterpret_cast<void**>(ppparsedExpression) ); pparsedExpr->Release(); return hr; }  
```  
  
## Vedere anche  
 [Valutazione di un'espressione di finestra Espressioni di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [La valutazione di un'espressione di controllo](../../extensibility/debugger/evaluating-a-watch-expression.md)