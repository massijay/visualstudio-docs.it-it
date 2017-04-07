---
title: IDebugOutputStringEvent2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
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
ms.openlocfilehash: 42a3b630a501a379d38a53f942c0aceb494d94d7
ms.lasthandoff: 04/05/2017

---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Questa interfaccia viene inviata dal motore di debug (DE) al gestore di sessione di debug (SDM) per restituire una stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per l'invio di una stringa per il **Output** finestra dell'IDE. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Usa il SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso il `IDebugEvent2` interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 La Germania crea e invia l'oggetto evento per inviare una stringa per il **Output** finestra. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente mostra il metodo di `IDebugOutputStringEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Ottiene il messaggio visualizzabile.|  
  
## <a name="remarks"></a>Note  
 Nel codice non gestito, ad esempio, può derivare la stringa di output quando il programma sottoposto a debug invia una stringa a Win32 `OutputDebugString` (funzione). Questa stringa viene intercettata dalla Germania e inviata a un il SDM come il `IDebugOutputStringEvent2` evento.  
  
 Utilizzare [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) per inviare un messaggio che richiede una risposta dell'utente.  
  
 Utilizzare [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) per inviare un messaggio di errore che non richiedono una risposta.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
