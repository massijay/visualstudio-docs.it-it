---
title: IDebugDefaultPort2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
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
ms.openlocfilehash: d048bf55d8a8cb721e8ebf85444e49c3bfa771b9
ms.lasthandoff: 04/05/2017

---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Questa interfaccia fornisce diversi metodi per l'accesso ai server di una porta e le funzionalità di notifica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per rappresentare la porta di debug per l'accesso ai programmi. Un fornitore di porta personalizzato può anche implementare questa interfaccia se gestisce il debug remoto.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un argomento a metodi di [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaccia fornisce questa interfaccia. La chiamata [QueryInterface](/cpp/atl/queryinterface) su un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia anche possibile ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi definiti in [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ottiene l'interfaccia di notifica di porta da questa porta.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ottiene l'interfaccia per il server che ospita questa porta.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se questa porta è in esecuzione nel computer locale.|  
  
## <a name="remarks"></a>Note  
 Il nome "`IDebugDefaultPort2`" è un po' di impropria poiché non rappresenta una porta predefinita. Impossibile chiamare "IDebugPort3".  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
