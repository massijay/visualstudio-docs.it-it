---
title: DEBUGPROP_INFO_FLAGS | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
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
ms.openlocfilehash: c5b749cffbc05fcc3fa6c533dc4bb3bdcd1ad1c0
ms.lasthandoff: 02/22/2017

---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Specifica le informazioni per recuperare un oggetto di proprietà di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 DEBUGPROP_INFO_FULLNAME  
 Inizializzazione/Usa il `bstrFullName` campo.  
  
 DEBUGPROP_INFO_NAME  
 Inizializzazione/Usa il `bstrName` campo.  
  
 DEBUGPROP_INFO_TYPE  
 Inizializzazione/Usa il `bstrType` campo.  
  
 DEBUGPROP_INFO_VALUE  
 Inizializzazione/Usa il `bstrValue` campo.  
  
 DEBUGPROP_INFO_ATTRIB  
 Inizializzazione/Usa il `dwAttrib` campo.  
  
 DEBUGPROP_INFO_PROP,  
 Inizializzazione/Usa il `pProperty` campo che contiene un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaccia.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Specifica che il campo del valore deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Deprecato.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Non restituiscono i valori beautified o i membri (vale a dire non formattare i valori).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Non restituiscono alcun valore sintetizzati speciali (ad esempio, non chiamare `ToString()` su un oggetto per produrre un valore).  
  
 DEBUGPROP_INFO_NONE  
 Specifica che nessun flag impostato.  
  
 DEBUGPROP_INFO_STANDARD  
 Inizializzazione/Usa il `dwAttrib`, `bstrName`, `bstrType`, e `bstrValue` campi.  
  
 DEBUGPROP_INFO_All  
 Indica una maschera di tutti i flag.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati per il [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), e [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metodi per indicare i campi da inizializzare il [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struttura.  
  
 Questi valori vengono utilizzati anche per il `dwFields` membro del `DEBUG_PROPERTY_INFO` struttura per indicare quali campi della struttura sono validi e utilizzate quando la struttura viene restituita.  
  
 Questi valori possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
