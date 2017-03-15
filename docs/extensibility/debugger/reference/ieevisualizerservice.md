---
title: "IEEVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService"
helpviewer_keywords: 
  - "Interfaccia IEEVisualizerService"
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IEEVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia implementa i metodi principali che forniscono funzionalità per la [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) e [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfacce.  
  
## Sintassi  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## Note per gli implementatori  
 Visual Studio implementa questa interfaccia per consentire un analizzatore di espressioni \(EE\) per supportare i visualizzatori di tipo.  
  
## Note per chiamanti  
 Le chiamate EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) per ottenere questa interfaccia come parte del relativo supporto per i visualizzatori di tipo.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Recupera il numero di cui questo servizio sia in grado di visualizzatori personalizzati.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Recupera l'elenco dei visualizzatori personalizzati.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Restituisce un oggetto proxy per una proprietà.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Recupera il numero di stringhe di valori da visualizzare per la proprietà specificata o il campo.|  
  
## Note  
 L'IDE utilizza il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia per determinare se sono presenti eventuali visualizzatori personalizzati o digitare i visualizzatori per la proprietà. Tramite la creazione di un servizio del visualizzatore \(con [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\), l'analizzatore di Espressioni può fornire la funzionalità per la `IDebugProperty3` e [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) \(che supporta la visualizzazione e modifica il valore della proprietà\) di interfacce e pertanto supporta i visualizzatori di tipo.  
  
 Se un EE visualizzatori personalizzati che a sua volta implementa, l'analizzatore di Espressioni è possibile aggiungere il `CLSID`s di tali visualizzatori personalizzati alla fine dell'elenco restituito da [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). In questo modo un EE supportare sia i visualizzatori di tipo e i proprio visualizzatori personalizzati. Accertarsi che [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) riflette l'aggiunta di eventuali visualizzatori personalizzati.  
  
 Vedere [Tipo visualizzatore e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) per una descrizione della differenza tra i visualizzatori e visualizzatori.  
  
## Requisiti  
 Intestazione: ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Tipo visualizzatore e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)