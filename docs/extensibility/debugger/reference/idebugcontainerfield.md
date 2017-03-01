---
title: IDebugContainerField | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7cf087725f8cfcb8ba53da739706ededcddb61c4
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Questa interfaccia rappresenta un simbolo o un tipo che è un contenitore per altri tipi o i simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia. Questa interfaccia è anche la classe base per tutte le interfacce che rappresentano i contenitori.  
  
## <a name="notes-for-callers"></a>Note per chiamanti  
 Molti metodi su interfacce restituiscono questa interfaccia. Poiché si tratta di una classe di base per tutti i contenitori, interfacce più specifiche possono ottenere da questa interfaccia tramite [QueryInterface](/visual-cpp/atl/queryinterface). Tali interfacce includono [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia, implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumeratore per i campi del contenitore.|  
  
## <a name="remarks"></a>Note  
 Matrici (contenitori per le variabili), classi (contenitori per i metodi e variabili) e i metodi (contenitori per i parametri e variabili locali) sono tutti esempi di contenitori.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
