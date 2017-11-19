---
title: THREADPROPERTIES | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADPROPERTIES
helpviewer_keywords: THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4ec394deef3b317d91e6cbe22bbc1d95a6aca5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="threadproperties"></a>THREADPROPERTIES
Vengono descritte le proprietà di un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Membri  
 dwFields  
 Una combinazione di flag dal [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) enumerazione, che indica quali campi in questa struttura sono validi.  
  
 dwThreadId  
 ID del thread.  
  
 dwSuspendCount  
 Il thread sospendere conteggio.  
  
 dwThreadState  
 Un valore di [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) enumerazione che indica lo stato del thread operativo.  
  
 bstrPriority  
 Stringa che specifica la priorità di thread. ad esempio, "Superiore al normale", "Normal" o "Ora critiche".  
  
 bstName  
 Il nome del thread.  
  
 bstrLocation  
 Il percorso del thread (in genere il frame dello stack più in alto), in genere espresso come il nome del metodo in esecuzione è attualmente bloccata.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene compilata una chiamata al [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metodo. Le informazioni restituite pertanto in genere è utilizzate per il popolamento di **thread** finestra.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)