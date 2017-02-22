---
title: "IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "Metodo SetPassCount"
  - "Metodo IDebugPendingBreakpoint2::SetPassCount"
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta o modifica il conteggio della sessione associato al punto di interruzione in attesa.  
  
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
 \[in\]  [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Una struttura che contiene il numero di sessione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Restituisce `E_BP_DELETED` se il punto di interruzione è stato eliminato.  
  
## Note  
 Il conteggio della sessione che in precedenza era associato al punto di interruzione in attesa viene perso.  Tutti i punti di interruzione limitano da questo punto di interruzione corrente vengono chiamati per impostare il conteggio della sessione al parametro di `bpPassCount` .  
  
## Vedere anche  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)