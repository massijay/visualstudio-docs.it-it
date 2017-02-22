---
title: "IPropertyProxyEESide | Microsoft Docs"
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
  - "IPropertyProxyEESide"
helpviewer_keywords: 
  - "Interfaccia IPropertyProxyEESide"
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia fornisce metodi ai dati della visualizzazione dell'oggetto associato.  Questa interfaccia fanno parte del supporto per i visualizzatori di tipi.  
  
## Sintassi  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## Note per gli implementatori  
 Un analizzatore di espressioni implementa questa interfaccia per supportare i visualizzatori di tipi.  
  
## Note per i chiamanti  
 Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per ottenere questa interfaccia.  chiamata [QueryInterface](/visual-cpp/atl/queryinterface) [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) su un'interfaccia per ottenere [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) l'interfaccia.  
  
## Metodi nell'ordine di Vtable  
 i seguenti metodi sono implementati da questa interfaccia:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inizializza un provider dell'origine dati in modo dai dati possa accedere a un oggetto.|  
|[GetManagedViewerCreationData](../Topic/IPropertyProxyEESide::GetManagedViewerCreationData.md)|Recupera le informazioni sull'assembly dell'oggetto.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|ottiene i dati iniziali per l'oggetto.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Crea una copia di un archivio dati esistente.|  
|[InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md)|Crea un riferimento a un archivio dati esistente.|  
|[ResolveAssemblyRef](../Topic/IPropertyProxyEESide::ResolveAssemblyRef.md)|Recupera le informazioni su un assembly specifico nel contesto dell'assembly che contiene questo oggetto.|  
  
## Note  
 Un visualizzatore di tipo utilizza questa interfaccia per accedere ai valori associati all'oggetto che questa interfaccia fanno parte di.  I dati avviene tramite l'interfaccia [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , che fornisce una visualizzazione in sola lettura di dati.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Tipo visualizzatore e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)