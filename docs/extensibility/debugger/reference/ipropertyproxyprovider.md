---
title: "IPropertyProxyProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyProvider"
helpviewer_keywords: 
  - "Interfaccia IPropertyProxyProvider"
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia fornisce un'interfaccia del proxy per visualizzare e modificare i dati di un oggetto.  
  
## Sintassi  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## Note per gli implementatori  
 L'analizzatore di \(EE\) espressioni implementa questa interfaccia lo stesso oggetto che implementa [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) l'interfaccia come parte del supporto dell'EE dei visualizzatori di tipi.  
  
## Note per i chiamanti  
 chiamata [QueryInterface](/visual-cpp/atl/queryinterface) su un'interfaccia di `IDebugProperty3` per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 l'interfaccia di `IPropertyProxyProvider` implementa il seguente metodo:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera un'interfaccia del proxy della proprietà per visualizzare i dati in un oggetto.|  
  
## Note  
 Sebbene l'EE implementare questa interfaccia, l'implementazione di [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) in genere gestita da [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md).  Vedere [Visualizzazione e la visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate su come ottenere l'interfaccia di IEEVisualizerService.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Tipo visualizzatore e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualizzazione e la visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)