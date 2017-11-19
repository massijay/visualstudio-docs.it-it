---
title: PENDING_BP_STATE_FLAGS | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PENDING_BP_STATE_FLAGS
helpviewer_keywords: PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c89469cd1b2d41fc0e3258d2875b9e22b7c55747
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="pendingbpstateflags"></a>PENDING_BP_STATE_FLAGS
Specifica i flag di stato del punto di interruzione in sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
typedef DWORD PENDING_BP_STATE_FLAGS;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE_FLAGS {   
   PBPSF_NONE        = 0x0000,  
   PBPSF_VIRTUALIZED = 0x0001  
};  
```  
  
## <a name="members"></a>Membri  
 PBPSF_NONE  
 Segnaposto.  
  
 PBPSF_VIRTUALIZED  
 Specifica un virtualizzato in sospeso punto di interruzione, che è necessario associare ogni volta che viene caricato di nuovo codice.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `flags` appartenente il [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) struttura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)