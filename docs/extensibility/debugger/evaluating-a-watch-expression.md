---
title: "La valutazione di un&#39;espressione di controllo | Microsoft Docs"
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
  - "valutazione dell'espressione, espressioni di controllo"
  - "espressioni di controllo"
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# La valutazione di un&#39;espressione di controllo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando Visual Studio è possibile visualizzare il valore di un'espressione di controllo, viene chiamato [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) che a sua volta chiama [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Questa operazione produce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che contiene il valore e il tipo dell'espressione.  
  
 In questa implementazione di `IDebugParsedExpression::EvaluateSync`, l'espressione viene analizzata e valutata nello stesso momento. Questa implementazione esegue le attività seguenti:  
  
1.  Analizza e valuta l'espressione per produrre un oggetto generico che contiene il valore e il relativo tipo. In c\#, questa viene rappresentata come un `object` mentre in C\+\+ si è rappresentato come un `VARIANT`.  
  
2.  Crea un'istanza di una classe \(chiamato `CValueProperty` in questo esempio\) che implementa il `IDebugProperty2` interfaccia e memorizza nella classe il valore da restituire.  
  
3.  Restituisce il `IDebugProperty2` interfaccia il `CValueProperty` oggetto.  
  
## Codice gestito  
 Si tratta di un'implementazione di `IDebugParsedExpression::EvaluateSync` nel codice gestito. Il metodo helper `Tokenize` Analizza l'espressione in un albero di analisi. La funzione di supporto `EvalToken` converte il token in un valore. La funzione di supporto `FindTerm` in modo ricorsivo attraversa l'albero di analisi, la chiamata a `EvalToken` per ogni nodo che rappresenta un valore e l'applicazione di qualsiasi operazione \(addizione o sottrazione\) nell'espressione.  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT EvaluateSync( uint evalFlags, uint timeout, IDebugSymbolProvider provider, IDebugAddress address, IDebugBinder binder, string resultType, out IDebugProperty2 result) { HRESULT retval = COM.S_OK; this.evalFlags = evalFlags; this.timeout = timeout; this.provider = provider; this.address = address; this.binder = binder; this.resultType = resultType; try { IDebugField field = null; // Tokenize, then parse. tokens = Tokenize(expression); result = new CValueProperty( expression, (int) FindTerm(EvalToken(tokens[0], out field),1), field, binder); } catch (ParseException) { result = new CValueProperty(expression, "Huh?"); retval = COM.E_INVALIDARG; } return retval; } } }  
```  
  
## Codice non gestito  
 Si tratta di un'implementazione di `IDebugParsedExpression::EvaluateSync` nel codice non gestito. La funzione di supporto `Evaluate` Analizza e valuta l'espressione che restituisce un `VARIANT` che contiene il valore risultante. La funzione di supporto `VariantValueToProperty` aggregazioni di `VARIANT` in un `CValueProperty` oggetto.  
  
```  
[C++] STDMETHODIMP CParsedExpression::EvaluateSync( in  DWORD                 evalFlags, in  DWORD                 dwTimeout, in  IDebugSymbolProvider* pprovider, in  IDebugAddress*        paddress, in  IDebugBinder*         pbinder, in  BSTR                  bstrResultType, out IDebugProperty2**     ppproperty ) { // dwTimeout parameter is ignored in this implementation. if (pprovider == NULL) return E_INVALIDARG; if (paddress == NULL) return E_INVALIDARG; if (pbinder == NULL) return E_INVALIDARG; if (ppproperty == NULL) return E_INVALIDARG; else *ppproperty = 0; HRESULT hr; VARIANT value; BSTR    bstrErrorMessage = NULL; hr = ::Evaluate( pprovider, paddress, pbinder, m_expr, &bstrErrorMessage, &value ); if (hr != S_OK) { if (bstrErrorMessage == NULL) return hr; //we can display better messages ourselves. HRESULT hrLocal = S_OK; VARIANT varType; VARIANT varErrorMessage; VariantInit( &varType ); VariantInit( &varErrorMessage ); varErrorMessage.vt      = VT_BSTR; varErrorMessage.bstrVal = bstrErrorMessage; CValueProperty* valueProperty = new CValueProperty(); if (valueProperty != NULL) { hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage); if (SUCCEEDED(hrLocal)) { hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2, reinterpret_cast<void**>(ppproperty) ); } } VariantClear(&varType); VariantClear(&varErrorMessage); //frees BSTR if (!valueProperty) return hr; valueProperty->Release(); if (FAILED(hrLocal)) return hr; } else { if (bstrErrorMessage != NULL) SysFreeString(bstrErrorMessage); hr = VariantValueToProperty( pprovider, paddress, pbinder, m_radix, m_expr, value, ppproperty ); VariantClear(&value); if (FAILED(hr)) return hr; } return S_OK; }  
```  
  
## Vedere anche  
 [Valutazione di un'espressione di finestra Espressioni di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Implementazione di esempio della valutazione dell'espressione](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)