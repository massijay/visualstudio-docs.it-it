---
title: "IDebugProgramEngines2::SetEngine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2::SetEngine"
helpviewer_keywords: 
  - "IDebugProgramEngines2::SetEngine"
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEngines2::SetEngine
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Indica al programma o il nodo del programma quale motore di debug \(DE\) da utilizzare per eseguire il debug del programma.  
  
## Sintassi  
  
```cpp#  
HRESULT SetEngine(   
   REFGUID guidEngine  
);  
```  
  
```c#  
int SetEngine(   
   ref Guid guidEngine  
);  
```  
  
#### Parametri  
 `guidEngine`  
 \[in\]  Il GUID di DE.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)