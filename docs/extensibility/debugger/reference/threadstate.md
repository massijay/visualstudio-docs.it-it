---
title: THREADSTATE | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADSTATE
helpviewer_keywords: THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 495425e8a91d42d1da4c3a36f7e3be1e02031329
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="threadstate"></a>THREADSTATE
Specifica lo stato del thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>Membri  
 THREADSTATE_RUNNING  
 Indica che il thread è in esecuzione.  
  
 THREADSTATE_STOPPED  
 Indica che il thread è stato arrestato a causa di un punto di interruzione.  
  
 THREADSTATE_FRESH  
 Indica che il thread è stato creato, ma non è ancora in esecuzione codice.  
  
 THREADSTATE_DEAD  
 Indica che il thread è inattivo.  
  
 THREADSTATE_FROZEN  
 Indica che il thread è bloccato (esecuzione non può essere eseguita).  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `dwThreadState` campo il [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struttura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)