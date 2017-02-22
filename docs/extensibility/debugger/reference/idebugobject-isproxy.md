---
title: "IDebugObject::IsProxy | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugObject::IsProxy"
  - "IsProxy"
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::IsProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

determina se l'oggetto è un proxy trasparente.  
  
## Sintassi  
  
```cpp#  
HRESULT IsProxy (  
   BOOL* pfIsProxy  
);  
```  
  
```c#  
int IsProxy (  
   out bool pfIsProxy  
);  
```  
  
#### Parametri  
 `pfIsProxy`  
 \[out\]  `TRUE` se l'oggetto è un proxy trasparente, in caso contrario, `FALSE`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene implementato dal motore di debug C\+\+ predefinite.  
  
## Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)