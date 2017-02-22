---
title: "BP_UNBOUND_REASON | Microsoft Docs"
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
  - "BP_UNBOUND_REASON"
helpviewer_keywords: 
  - "Enumerazione BP_UNBOUND_REASON"
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fornisce il motivo per cui un punto di interruzione è stato separato.  
  
## Sintassi  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```c#  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## Membri  
 BPUR\_UNKNOWN  
 il motivo è sconosciuto.  
  
 BPUR\_CODE\_UNLOADED  
 Il codice contenente il punto di interruzione è stato scaricato.  
  
 BPUR\_BREAKPOINT\_REBIND  
 Il punto di interruzione è stato riassociato in un percorso diverso.  Ciò può verificarsi dopo le operazioni Modifica e continuazione quando il punto di interruzione si sposta, o quando il punto di interruzione verrà associato a un file con un percorso che non è più valido.  
  
 BPUR\_ BREAKPOINT\_ERROR  
 Il punto di interruzione viene determinato sia per errore dopo averlo associato.  Ciò si verifica nei punti di interruzione gestiti che le condizioni non è più valido.  
  
## Note  
 Oggetto restituito [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) dal metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)