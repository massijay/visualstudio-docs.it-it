---
title: "Esempio di implementazione di variabili locali | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], variabili locali"
  - "valutazione delle espressioni, variabili locali"
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Esempio di implementazione di variabili locali
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Di seguito viene fornita una panoramica di come Visual Studio Ottiene le variabili locali per un metodo dall'analizzatore di espressioni \(EE\):  
  
1.  Visual Studio chiama il motore di debug \(DE\) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) per ottenere un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta tutte le proprietà dello stack frame, tra cui le variabili locali.  
  
2.  `IDebugStackFrame2::GetDebugProperty` chiamate [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) per ottenere un oggetto che descrive il metodo all'interno del quale si è verificato il punto di interruzione. Il DE fornisce un provider di simboli \([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)\), un indirizzo \([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)\) e un gestore di associazione \([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)\).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` chiamate [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con il parametro `IDebugAddress` oggetto da ottenere un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) che rappresenta il metodo contenente l'indirizzo specificato.  
  
4.  Il `IDebugContainerField` interfaccia viene eseguita una query per il [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaccia. È questa interfaccia che fornisce accesso alle variabili locali del metodo.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` Crea un'istanza di una classe \(chiamato `CFieldProperty` nell'esempio\) che implementa il `IDebugProperty2` interfaccia rappresentano variabili locali del metodo. Il `IDebugMethodField` oggetto viene inserito in questa `CFieldProperty` oggetto insieme con il `IDebugSymbolProvider`, `IDebugAddress` e `IDebugBinder` oggetti.  
  
6.  Quando il `CFieldProperty` oggetto viene inizializzato, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) viene chiamato sul `IDebugMethodField` per ottenere un [FIELD\_INFO](../../extensibility/debugger/reference/field-info.md) struttura che contiene tutte le informazioni visualizzabili il metodo stesso.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Restituisce il `CFieldProperty` dell'oggetto come un `IDebugProperty2` oggetto.  
  
8.  Chiamate di Visual Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sull'oggetto restituito `IDebugProperty2` oggetto con il filtro `guidFilterLocalsPlusArgs`. Questo metodo restituisce un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contenente variabili locali del metodo. Questa enumerazione viene compilata tramite chiamate a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) e [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Chiamate di Visual Studio [Successivo](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) per ottenere un [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) struttura per ogni locale. Questa struttura contiene un puntatore a un `IDebugProperty2` interfaccia per una variabile locale.  
  
10. Chiamate di Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) per ogni locale ottenere nome, valore e tipo di oggetto locale. Si tratta delle informazioni visualizzate nel **variabili locali** finestra.  
  
## Contenuto della sezione  
 [Implementazione di GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Viene descritta un'implementazione di [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumerazione delle variabili locali](../../extensibility/debugger/enumerating-locals.md)  
 Viene descritto come il motore di debug \(DE\) effettua una chiamata per enumerare le variabili locali o argomenti.  
  
 [Recupero delle proprietà locale](../../extensibility/debugger/getting-local-properties.md)  
 Viene descritto come il DE effettua una chiamata per ottenere il nome, tipo e valore di uno o più variabili locali.  
  
 [Ottenere valori locali](../../extensibility/debugger/getting-local-values.md)  
 Viene illustrato come ottenere il valore della variabile locale, che richiede i servizi di un oggetto gestore di associazione fornito dal contesto di valutazione.  
  
 [Valutazione delle variabili locali](../../extensibility/debugger/evaluating-locals.md)  
 Viene illustrato come vengono valutate variabili locali.  
  
## Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Fornisce gli argomenti che vengono passati al momento il DE chiama l'analizzatore di espressioni \(EE\).  
  
 [MyCEE Sample](http://msdn.microsoft.com/it-it/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Viene illustrato un approccio di implementazione per la creazione di un analizzatore di espressioni per la lingua MyC.  
  
## Vedere anche  
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)