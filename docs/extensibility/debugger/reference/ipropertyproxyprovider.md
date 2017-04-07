---
title: IPropertyProxyProvider | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 73a1a1a189e4922d662081a92738b1c35c6bb291
ms.lasthandoff: 04/05/2017

---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Questa interfaccia fornisce un'interfaccia proxy per visualizzare e modificare i dati di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni (Java EE) implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaccia come parte del supporto del motore di esecuzione di visualizzatori di tipo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProperty3` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Il `IPropertyProxyProvider` interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera un'interfaccia proxy di proprietà per visualizzare i dati su un oggetto.|  
  
## <a name="remarks"></a>Note  
 Sebbene l'analizzatore di Espressioni implementa questa interfaccia, l'implementazione di [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) viene generalmente gestita dagli [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Vedere [Visualizing e visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate su come ottenere l'interfaccia IEEVisualizerService.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualizzatore di tipo e il visualizzatore personalizzato](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
