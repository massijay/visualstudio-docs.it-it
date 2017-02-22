---
title: "DEBUG_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_REASON"
helpviewer_keywords: 
  - "Enumerazione DEBUG_REASON"
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica perché il processo è stato avviato per il debug.  
  
## Sintassi  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```c#  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### Parametri  
 DEBUG\_REASON\_ERROR  
 Un errore non specifico si è verificato questo viene utilizzato come stato predefinito quando nessuno degli altri motivi viene allungato\).  
  
 DEBUG\_REASON\_USER\_LAUNCHED  
 Il processo è stato avviato alla richiesta dell'utente.  
  
 DEBUG\_REASON\_USER\_ATTACHED  
 Il processo di già\-funzionamento è stato collegato dall'utente.  
  
 DEBUG\_REASON\_AUTO\_ATTACHED  
 Il processo automatico è stato collegato a quando è stato avviato.  
  
 DEBUG\_REASON\_CAUSALITY  
 il processo è stato avviato a causa di un evento \(JIT\) di debug JIT.  
  
## Note  
 Restituito [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) dal metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)