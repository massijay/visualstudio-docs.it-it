---
title: PROCESS_INFO | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
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
ms.openlocfilehash: 791686d7ab4516f5eb4da0642d97acb9df730f12
ms.lasthandoff: 02/22/2017

---
# <a name="processinfo"></a>PROCESS_INFO
Contiene informazioni su un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```c#  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Membri  
 Campi  
 Una combinazione di flag dal [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) enumerazione che specificano quali campi vengono compilati.  
  
 bstrFileName  
 Nome e percorso completo del processo. Equivalente alla chiamata di [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metodo con il parametro `GN_FILENAME`.  
  
 bstrBaseName  
 Il nome del file e l'estensione del processo. Equivalente alla chiamata di `IDebugProcess2::Getname` metodo con il parametro `GN_BASENAME`.  
  
 bstrTitle  
 Il titolo del processo, se presente. Equivalente alla chiamata di `IDebugProcess2::Getname` metodo con il parametro `GN_TITLE`.  
  
 ProcessId  
 Il [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura che identifica il processo. Equivalente alla chiamata di [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) metodo.  
  
 dwSessionId  
 Identificatore della sessione di debug che questo processo viene eseguito in.  
  
 bstrAttachedSessionName  
 Nome della sessione associata. Equivalente alla chiamata di [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) metodo.  
  
 CreationTime  
 Ora che è stato creato il processo.  
  
 Flag  
 Una combinazione di flag dal [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) enumerazione che specificano proprietà del processo.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per la [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) in cui viene compilato nel metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)