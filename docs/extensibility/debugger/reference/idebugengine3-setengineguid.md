---
title: "IDebugEngine3::SetEngineGuid | Microsoft Docs"
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
  - "IDebugEngine3::SetEngineGuid"
helpviewer_keywords: 
  - "IDebugEngine3::SetEngineGuid"
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3::SetEngineGuid
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo imposta `GUID`\(DE\) del motore di debug.  
  
## Sintassi  
  
```cpp  
HRESULT SetEngineGuid(  
   GUID* guidEngine  
);  
```  
  
```  
[C#]  
int SetEngineGuid(  
   ref Guid guidEngine  
);  
```  
  
#### Parametri  
 `guidEngine`  
 \[in\]  `GUID` del motore.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Vedere anche  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)