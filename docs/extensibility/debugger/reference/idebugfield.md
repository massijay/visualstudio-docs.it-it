---
title: IDebugField | Documenti Microsoft
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: b96de879e880fc786f3bcedbe797cb66e68e04b9
ms.lasthandoff: 04/05/2017

---
# <a name="idebugfield"></a>IDebugField
Questa interfaccia rappresenta un campo, vale a dire, una descrizione di un tipo o un simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia come classe base per tutti i campi.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia è la classe base per tutti i campi. In base al valore restituito di [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), questa interfaccia può restituire più specializzate interfacce tramite [QueryInterface](/cpp/atl/queryinterface). Inoltre, molte delle interfacce restituiscono `IDebugField` oggetti da vari metodi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugField`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Ottiene informazioni visualizzabili sul simbolo o un tipo.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Ottiene il tipo di campo.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Ottiene il tipo di campo.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Ottiene il contenitore del campo.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Ottiene l'indirizzo del campo.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Ottiene le dimensioni di un campo, in byte.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Ottiene le informazioni relative a un campo estese.|  
|[Uguale a](../../../extensibility/debugger/reference/idebugfield-equal.md)|Confronta due campi.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Ottiene informazioni indipendente dal tipo di simbolo o un tipo.|  
  
## <a name="remarks"></a>Note  
 Un tipo è equivalente a un linguaggio C `typedef`.  
  
 Nell'esempio seguente linguaggio C++ `weather` è un tipo di classe e `sunny` e `stormy` simboli:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Se un campo rappresenta un simbolo o il tipo può essere determinato chiamando [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) ed esaminando il [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) risultato. Se il `FIELD_KIND_TYPE` bit viene impostato, il campo è un tipo e se il `FIELD_KIND_SYMBOL` bit viene impostato, è un simbolo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)