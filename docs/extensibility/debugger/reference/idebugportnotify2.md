---
title: IDebugPortNotify2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
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
ms.openlocfilehash: de163fdf55052ff4cc2f1599bc8ddfd162d03df3
ms.lasthandoff: 04/05/2017

---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Questa interfaccia registra o Annulla la registrazione di un programma che è possibile eseguire il debug con la porta in cui viene eseguito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porta personalizzato implementa questa interfaccia per supportare l'aggiunta e rimozione di programmi dalla porta. In genere viene implementato nello stesso oggetto che implementa il [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [QueryInterface](/cpp/atl/queryinterface) sul `IDebugPort2` interfaccia restituisce questa interfaccia. Inoltre, una chiamata a [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) restituisce questa interfaccia. Un motore di debug è possibile visualizzare questa interfaccia come parametro a [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortNotify2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programma che è possibile eseguire il debug con la porta in cui viene eseguito.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annulla la registrazione di un programma che è possibile eseguire il debug dalla porta in cui viene eseguito.|  
  
## <a name="remarks"></a>Note  
 A meno che una porta di debug è un modo per sapere quando i programmi sono caricati o scaricati, un fornitore di porta personalizzato deve implementare questa interfaccia. Tutti i programmi che vengono caricati per il debug tramite una porta specifica vengono rilevati tramite questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
