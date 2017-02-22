---
title: "IEEVisualizerDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider"
helpviewer_keywords: 
  - "Interfaccia IEEVisualizerDataProvider"
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione di analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [gli analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia fornisce la possibilità di modificare il valore di un oggetto tramite un visualizzatore di tipo.  
  
## Sintassi  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## Note per gli implementatori  
 L'analizzatore di espressioni implementa questa interfaccia per supportare la modifica dei dati su un oggetto di proprietà tramite un visualizzatore di tipo.  
  
## Note per chiamanti  
 Questa interfaccia viene utilizzata per la creazione di [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) oggetto tramite una chiamata a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Per altre informazioni, vedere [Visualizzazione e la visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md).  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../Topic/IEEVisualizerDataProvider::CanSetObjectForVisualizer.md)|Determina se è possibile aggiornare l'oggetto \(e, successivamente, il relativo valore\) che è che rappresenta questo visualizzatore.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Forza una nuova valutazione dell'oggetto per il visualizzatore.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ottiene un oggetto esistente per questo visualizzatore \(non viene eseguita alcuna valutazione\).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aggiorna l'oggetto per questo visualizzatore, cambiando il valore che viene visualizzato il visualizzatore.|  
  
## Note  
 Il servizio Visualizzatore \(rappresentati dal [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) l'interfaccia e restituito da [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\) mantiene un riferimento all'oggetto che implementa il `IEEVisualizerDataProvider` interfaccia. Di conseguenza, il `IEEVisualizerDataProvider` interfaccia non deve essere implementata sullo stesso oggetto che implementa il [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) se quell'oggetto mantiene un riferimento di `IEEVisualizerService` oggetto: otterrà un riferimento circolare e si verifica un deadlock quando gli oggetti vengono eliminati. L'approccio consigliato consiste nell'implementare `IEEVisualizerDataProvider` su un oggetto separato a cui il `IDebugProperty2` delegati senza chiamare il metodo dell'oggetto `IUnknown::AddRef` su di esso.  
  
## Requisiti  
 Intestazione: ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualizzazione e la visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)