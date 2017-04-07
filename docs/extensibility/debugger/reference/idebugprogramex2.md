---
title: IDebugProgramEx2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
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
ms.openlocfilehash: 55781c5d1f0fc15c505394fb08291a058de71247
ms.lasthandoff: 04/05/2017

---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Questa interfaccia consente la sessione di debug manager (SDM) collegare a un programma e ottenere il nodo di programma associato a un programma.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porta personalizzato implementa questa interfaccia per l'oggetto stesso come il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per consentire il SDM connessi a un programma allo stesso tempo consentendo il fornitore della porta tenere traccia di tutte le sessioni associata al programma. Se sceglie, il fornitore della porta personalizzato può implementare questa interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate SDM [QueryInterface](/cpp/atl/queryinterface) su un `IDebugProgram2` interfaccia per ottenere questa interfaccia per tenere traccia delle sessioni che sono connessi a tali programmi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProgramEx2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Connette un programma a una sessione.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ottiene il nodo di programma associato a un programma.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia è privata tra il SDM e il programma.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
