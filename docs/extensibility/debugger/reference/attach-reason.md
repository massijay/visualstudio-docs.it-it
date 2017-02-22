---
title: "ATTACH_REASON | Microsoft Docs"
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
  - "ATTACH_REASON"
helpviewer_keywords: 
  - "Enumerazione ATTACH_REASON"
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# ATTACH_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica il motivo per cui il motore di \(DE\) debug possa connettersi a un nodo di programma.  
  
## Sintassi  
  
```cpp#  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```c#  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## Membri  
 ATTACH\_REASON\_AUTO  
 Connettersi perché il processo si trova in modalità di debug.  
  
 ATTACH\_REASON\_LAUNCH  
 Connettersi perché il processo è stato avviato.  
  
 ATTACH\_REASON\_USER  
 Connettersi a causa di una richiesta dell'utente.  
  
## Note  
 Questi valori vengono utilizzati come parametro [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) ai metodi e.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)