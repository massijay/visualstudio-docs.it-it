---
title: "IDebugCanStopEvent2::CanStop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::CanStop"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::CanStop"
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Notifica al motore \(DE\) di debug indipendentemente dal fatto che l'interruzione in corrispondenza della posizione corrente di codice o continuare immediatamente l'esecuzione.  
  
## Sintassi  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```c#  
int CanStop (   
   int fCanStop  
);  
```  
  
#### Parametri  
 `fCanStop`  
 \[in\]  Diverso da zero \(`TRUE`\) se il DE si ferma in corrispondenza della posizione corrente di codice; in caso contrario, lo zero \(`FALSE`\).  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il ricevitore di questo evento in genere chiama [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md) il metodo per determinare il motivo per cui il DE desidera arrestare e chiama quindi il metodo di `IDebugCanStopEvent2::CanStop` con la risposta appropriata.  
  
 Se il DE si interrompe, invia un evento che descrive il motivo per arrestare.  È in genere due eventi inviati, un utente o un'interruzione del segnale rappresentata [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) dall'interfaccia e un evento del punto di interruzione rappresentato [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) dall'interfaccia.  
  
## Vedere anche  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../Topic/IDebugCanStopEvent2::GetReason.md)