---
title: "IDebugObject::IsReadOnly | Microsoft Docs"
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
  - "IDebugObject::IsReadOnly"
helpviewer_keywords: 
  - "Metodo IDebugObject::IsReadOnly"
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::IsReadOnly
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina se l'oggetto è di sola lettura.  
  
## Sintassi  
  
```cpp#  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```c#  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### Parametri  
 `pfIsReadOnly`  
 \[out\]  Restituisce diverso da zero \(`TRUE`\) se l'oggetto è di sola lettura; in caso contrario, restituisce zero \(`FALSE`\).  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Un oggetto di sola lettura non può avere il valore modificato dopo averlo creato.  
  
## Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)