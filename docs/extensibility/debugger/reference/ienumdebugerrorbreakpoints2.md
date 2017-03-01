---
title: IEnumDebugErrorBreakpoints2 | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 9
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
ms.openlocfilehash: 39b2ce4bb8fdecbe67d6c39e53454e49853f55c8
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Questa interfaccia enumera i punti di interruzione di errore associate a un punto di interruzione in sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa l'interfaccia specificata come parte del relativo supporto per i punti di interruzione.  
  
## <a name="notes-for-callers"></a>Note per chiamanti  
 Chiamate di Visual Studio [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) per ottenere questa interfaccia che rappresenta un elenco dei punti di interruzione che non può essere associata, o [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco dei punti di interruzione che non sono stati associati.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugErrorBreakpoints2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Avanti](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Recupera un numero specificato di punti di interruzione di errore in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Ignora un numero specificato di punti di interruzione di errore in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Ottiene il numero di punti di interruzione di errore in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia contiene un elenco di [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfacce, ognuna delle quali descrive un punto di interruzione che potrebbe non essere associato e perché si potrebbe non essere associato. Visual Studio utilizza il `IEnumDebugErrorBreakpoint2` interfaccia per aggiornare i punti di interruzione visualizzati nell'IDE.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
