---
title: "IDebugPendingBreakpoint2::SetCondition | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::SetCondition"
helpviewer_keywords: 
  - "Metodo SetCondition"
  - "Metodo IDebugPendingBreakpoint2::SetCondition"
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta o modifica la condizione associata al punto di interruzione in attesa.  
  
## Sintassi  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```c#  
int SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
#### Parametri  
 `bpCondition`  
 \[in\]  [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Una struttura che specifica la condizione per impostare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Le condizioni che in precedenza era associata al punto di interruzione in attesa viene persa.  Tutti i punti di interruzione limitano da questo punto di interruzione corrente vengono chiamati per impostare lo stato corrispondente al valore specificato nel parametro di `bpCondition` .  
  
## Vedere anche  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)