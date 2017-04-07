---
title: IDebugProperty3 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 12
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
ms.openlocfilehash: 295baf524d3b1261826090164ccdf657b9672122
ms.lasthandoff: 04/05/2017

---
# <a name="idebugproperty3"></a>IDebugProperty3
Questa interfaccia fornisce supporto per:  
  
-   Recupero di una stringa di lunghezza arbitraria associata alla proprietà.  
  
-   Associazione di un ID univoco alla proprietà.  
  
-   Recupero di un elenco di visualizzatori personalizzati per la proprietà.  
  
-   Impostazione del valore di una proprietà con la possibilità di segnalare gli eventuali errori risultanti  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia sullo stesso oggetto che implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) per fornire supporto per stringhe lunghe, ID di proprietà e i visualizzatori personalizzati.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProperty2` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da `IDebugProperty2`, `IDebugProperty3` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Restituisce la lunghezza della stringa di cui è associata alla proprietà.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Restituisce la stringa in un buffer fornito dall'utente.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Crea un ID univoco per questa proprietà.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Elimina l'ID univoco per questa proprietà.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Restituisce il numero di visualizzatori personalizzati che è possibile visualizzare con questa proprietà.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Restituisce l'elenco dei visualizzatori personalizzati che è possibile visualizzare con questa proprietà.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Imposta il valore di questa proprietà, restituendo un messaggio di errore se qualsiasi elemento è verificato un errore.|  
  
## <a name="remarks"></a>Note  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) è il modo preferito per la gestione di debug (SDM) per impostare un valore della proprietà di sessione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
