---
title: IDebugMessageEvent2 | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 0f033c5793dc3b89a1f2bd74a2bc4857730fb746
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Questa interfaccia viene utilizzata dal motore di debug (DE) per inviare un messaggio a Visual Studio che richiede una risposta da parte dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il DE implementa questa interfaccia per inviare un messaggio a Visual Studio che richiede una risposta dell'utente. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia. Utilizza il modello SDM [QueryInterface](/visual-cpp/atl/queryinterface) accesso il `IDebugEvent2` interfaccia.  
  
 L'implementazione di questa interfaccia deve comunicare la chiamata di Visual Studio di [metodo {1>setresponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) per il DE. Ad esempio, questa operazione può essere eseguita con un messaggio inviato al messaggio del DE thread di gestione o l'oggetto che implementa questa interfaccia può mantenere un riferimento per il DE e richiamare il DE con la risposta passata `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Note per chiamanti  
 La dice crea e invia l'oggetto evento per visualizzare un messaggio per l'utente che richiede una risposta. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito dal suo SDM quando è associato al programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente vengono illustrati i metodi di `IDebugMessageEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ottiene il messaggio da visualizzare.|  
|[Metodo {1>setresponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Imposta la risposta, se presente, dalla finestra di messaggio.|  
  
## <a name="remarks"></a>Note  
 Se è necessaria una risposta specifica da parte dell'utente per un determinato messaggio, il DE utilizzerà questa interfaccia. Ad esempio, se il DE Ottiene un messaggio "Accesso negato" dopo un tentativo di connettersi in modalità remota a un programma, il DE invia il messaggio specifico per Visual Studio in un `IDebugMessageEvent2` evento con lo stile di finestra di messaggio `MB_RETRYCANCEL`. Ciò consente all'utente di ripetere oppure annullare l'operazione di collegamento.  
  
 Il DE specifica la modalità questo messaggio di essere gestiti seguendo le convenzioni della funzione Win32 `MessageBox` (vedere [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) per informazioni dettagliate).  
  
 Utilizzare il [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfaccia per inviare messaggi a Visual Studio che non richiedono una risposta da parte dell'utente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
