---
title: "IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs"
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
  - "IDebugBoundBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "Metodo SetPassCount"
  - "Metodo IDebugBoundBreakpoint2::SetPassCount"
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBoundBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta o modifica il conteggio della sessione associato a questo punto di interruzione associato.  
  
## Sintassi  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### Parametri  
 `bpPassCount`  
 \[in\]  [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) La struttura che specifica il numero della sessione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Restituisce `E_BP_DELETED` se lo stato dell'oggetto punto di interruzione associato è impostato su `BPS_DELETED` \(parte [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) dell'enumerazione\).  
  
## Note  
 Il conteggio della sessione determina se il punto di interruzione viene generato.  la sessione o il numero di passaggi corrente può essere ottenuto chiamando [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) il metodo.  
  
 Il conteggio della sessione che in precedenza era associato a questo punto di interruzione viene perso.  
  
## Vedere anche  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)