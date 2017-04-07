---
title: IDebugAddress2 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 10
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
ms.openlocfilehash: e36f2863680dea79451e57d06bd749b52fbed933
ms.lasthandoff: 04/05/2017

---
# <a name="idebugaddress2"></a>IDebugAddress2
Questa interfaccia fornisce accesso all'ID del processo a cui appartiene l'oggetto il cui indirizzo è rappresentato da questa interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia. Questa interfaccia fornisce l'accesso all'ID del processo a cui appartiene l'oggetto che è correlato a questo indirizzo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Utilizzare [QueryInterface](/cpp/atl/queryinterface) per questa interfaccia da ottenere il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable  
 Oltre ai metodi ereditati dal [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia, implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera l'ID del processo a cui appartiene l'oggetto rappresentato da questa interfaccia.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
