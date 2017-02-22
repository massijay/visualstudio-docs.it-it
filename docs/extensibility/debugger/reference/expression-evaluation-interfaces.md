---
title: "Interfacce di valutazione di espressioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "valutazione dell'espressione, interfacce"
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfacce di valutazione di espressioni
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Di seguito sono le interfacce di valutazione di espressioni per il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging SDK.  
  
## Discussione  
 Queste interfacce vengono utilizzate per valutare le espressioni in uno stack di chiamate durante la modalità di interruzione. Vengono implementati solo per common language runtime gli analizzatori di espressioni \(EE\).  
  
 Ogni interfaccia nella tabella viene illustrato il componente che è possibile implementare dall'elenco seguente:  
  
-   Eseguire il debug del motore \(DE\)  
  
-   Analizzatore di espressioni \(EE\)  
  
-   Visual Studio \(VS\)  
  
|Interfaccia|Implementata da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Rappresenta un alias per una variabile numerico.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Rappresenta un alias per una variabile numerico e consente un analizzatore di espressioni \(EE\) per ottenere il dominio applicazione per l'alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Rappresenta un oggetto matrice.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Rappresenta una matrice gestita e consente un analizzatore di espressioni \(EE\) per determinare l'indice di base \(inferiore\) per la matrice.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Rappresenta un Raccoglitore che associa i simboli per gli indirizzi effettivi in memoria di debug.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Come il [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaccia ma fornisce l'accesso a tipi, alias e i visualizzatori personalizzati.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Rappresenta l'analizzatore di espressioni.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Rappresenta una versione avanzata di un analizzatore di espressioni \(EE\).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Rappresenta un analizzatore di espressioni \(EE\) con una struttura ad albero parser avanzata.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Rappresenta una funzione.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Rappresenta una funzione e migliora il [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Consente un analizzatore di espressioni \(EE\) visualizzare un messaggio nella finestra di output del debugger.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Rappresenta un oggetto di codice gestito.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaccia di base che rappresenta qualsiasi simbolo associato a un indirizzo di memoria.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Come il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia ma fornisce l'accesso a informazioni aggiuntive.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Rappresenta un'espressione analizzata pronta per essere valutata.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Rappresenta un puntatore.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Rappresenta un puntatore in un albero di analisi ed estende il **IDebugPointerObject** interfaccia.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Offre la possibilità di modificare il valore di un tipo tramite un visualizzatore di tipo.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VISUAL STUDIO|Consente di accedere ai visualizzatori personalizzati e i visualizzatori di tipo.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VISUAL STUDIO|Fornisce la possibilità di creare un [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) oggetto.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Rappresenta una raccolta di oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md).|  
  
## Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Scrittura di un analizzatore di espressioni CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Tipo visualizzatore e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)