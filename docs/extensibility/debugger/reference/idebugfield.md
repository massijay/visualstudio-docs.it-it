---
title: IDebugField | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
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
ms.openlocfilehash: e272f7b5e314e09d111ca3996870f5131ebdc3d0
ms.lasthandoff: 02/22/2017

---
# <a name="idebugfield"></a>IDebugField
Questa interfaccia rappresenta un campo, vale a dire, una descrizione di un tipo o un simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia come classe di base per tutti i campi.  
  
## <a name="notes-for-callers"></a>Note per chiamanti  
 Questa interfaccia è la classe base per tutti i campi. In base al valore restituito di [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), questa interfaccia può restituire interfacce più specifiche utilizzando [QueryInterface](/visual-cpp/atl/queryinterface). Inoltre, molte interfacce restituiscono `IDebugField` oggetti da vari metodi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente vengono illustrati i metodi di `IDebugField`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ottiene informazioni visualizzabile del simbolo o del tipo.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ottiene il tipo di campo.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ottiene il tipo di campo.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ottiene il contenitore del campo.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ottiene l'indirizzo del campo.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ottiene le dimensioni di un campo, in byte.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ottiene le informazioni relative a un campo estese.|  
|[Uguale a](../../../extensibility/debugger/reference/idebugfield-equal.md)|Confronta due campi.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ottiene informazioni indipendente dal tipo di simbolo o del tipo.|  
  
## <a name="remarks"></a>Note  
 Un tipo è equivalente a un linguaggio C `typedef`.  
  
 Nell'esempio seguente del linguaggio C++ `weather` è un tipo di classe, e `sunny` e `stormy` sono simboli:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Se un campo rappresenta un simbolo o tipo può essere determinato chiamando [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) ed esaminando il [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) risultato. Se il `FIELD_KIND_TYPE` bit è impostato, il campo è un tipo e se il `FIELD_KIND_SYMBOL` bit è impostato, è un simbolo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
