---
title: IDebugThread2 | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 363f2aa684d45a07978c70b222af7f35ea2b05d3
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthread2"></a>IDebugThread2
Questa interfaccia rappresenta un thread in esecuzione in un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un thread di esecuzione in un unico programma.  
  
## <a name="notes-for-callers"></a>Note per chiamanti  
 Chiamare [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) per ottenere questa interfaccia che rappresenta il thread attualmente attivo.  
  
 Questa interfaccia viene inoltre utilizzata per la creazione di una richiesta di interruzione (vedere [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).  
  
 Questa interfaccia viene restituita anche durante la risoluzione di un punto di interruzione associato o errore (vedere [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) e [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente vengono illustrati i metodi di `IDebugThread2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Recupera un elenco degli stack frame per il thread.|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Ottiene il nome del thread.|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Imposta il nome del thread.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Ottiene il programma in cui è in esecuzione un thread.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Determina se l'istruzione successiva può essere impostata nel contesto determinato stack frame e il codice.|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Imposta istruzione successiva nel contesto determinato stack frame e il codice.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Ottiene l'identificatore del thread del sistema.|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Sospende un thread.|  
|[Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Riprende un thread.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Ottiene le proprietà che descrivono un thread.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Ottiene il thread logico associato a questo thread fisico.|  
  
## <a name="remarks"></a>Note  
 Poiché un singolo thread fisici possono essere eseguiti in più programmi, più `IDebugThread2` da più di un programma può rappresentare lo stesso thread fisico.  
  
 Quando si verifica un punto di interruzione o un'eccezione, viene inviato un evento chiamando [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Uno degli argomenti di questo metodo è un `IDebugThread2` interfaccia che rappresenta il thread corrente. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) viene utilizzata per ottenere il [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia per lo stack frame corrente.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
