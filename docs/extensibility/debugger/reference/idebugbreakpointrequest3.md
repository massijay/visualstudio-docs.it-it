---
title: IDebugBreakpointRequest3 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 8
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
ms.openlocfilehash: 61307781f8d386e7011422c0df815d80113b95cd
ms.lasthandoff: 04/05/2017

---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Questa interfaccia rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione. È un'estensione di [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Gestore di sessione di debug (SDM) in genere implementa questa interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Il motore di debug (DE) accede a questa interfaccia chiamando [QueryInterface](/cpp/atl/queryinterface) sull'interfaccia IDebugBreakpointRequest2 ricevuto in una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), `IDebugBreakpointRequest3` interfaccia espone il metodo seguente.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Ottiene le informazioni di richiesta di punto di interruzione che descrivono la richiesta di punto di interruzione.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene utilizzata per fornire informazioni aggiuntive per la Germania tramite il [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura. Queste informazioni aggiuntive includono l'ID fornitore del DE (sotto forma di un GUID), il nome di un punto di analisi e il nome di un vincolo di punto di interruzione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
