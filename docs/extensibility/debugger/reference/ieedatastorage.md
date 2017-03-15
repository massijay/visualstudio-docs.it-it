---
title: "IEEDataStorage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEDataStorage"
helpviewer_keywords: 
  - "Interfaccia IEEDataStorage"
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEDataStorage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta una matrice di byte.  
  
## Sintassi  
  
```  
IEEDataStorage : IUnknown  
```  
  
## Note per gli implementatori  
 L'analizzatore di \(EE\) espressioni implementa questa interfaccia per rappresentare una matrice di byte \(utilizzato dai visualizzatori di tipi per recuperare e i dati di modifica tramite [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) l'interfaccia.  L'EE in genere implementa questa interfaccia per supportare i visualizzatori esterno del tipo.  
  
## Note per i chiamanti  
 I metodi di `IPropertyProxyEESide` collegano restituiscono tutti questa interfaccia.  Chiamare [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) per [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ottenere l'interfaccia.  chiamata [QueryInterface](/visual-cpp/atl/queryinterface) [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) su un'interfaccia per ottenere [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) l'interfaccia.  
  
## Metodi nell'ordine di Vtable  
 L'interfaccia di `IEEDataStorage` implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetData](../Topic/IEEDataStorage::GetData.md)|Recupera il numero di byte di dati a un buffer specificato.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera il numero di byte di dati disponibili.|  
  
## Note  
 Questa interfaccia viene utilizzata da un visualizzatore del tipo per accedere ai dati utilizzati da un oggetto specifico.  I dati vengono considerati come matrice di byte, in modo che il visualizzatore del tipo di modifica in alcun modo è obbligatoria presentarla all'utente.  
  
 Un visualizzatore personalizzato anche possibile utilizzare questa interfaccia, se richiesto, sebbene più tipico, un visualizzatore personalizzato abbia utilizzato un'interfaccia o [GetStringChars](../Topic/IDebugProperty3::GetStringChars.md) , [GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md) per i dati basati su stringa\).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Tipo visualizzatore e Visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)