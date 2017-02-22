---
title: "IDebugArrayObject2::HasBaseIndices | Microsoft Docs"
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
  - "HasBaseIndices"
  - "IDebugArrayObject2::HasBaseIndices"
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject2::HasBaseIndices
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina se la matrice contiene indici di base \(limite inferiore\) definiti.  
  
## Sintassi  
  
```cpp#  
HRESULT HasBaseIndices (  
   BOOL* pfHasBaseIndices  
);  
```  
  
```c#  
int HasBaseIndices (  
   out bool pfHasBaseIndices  
);  
```  
  
#### Parametri  
 `pfHasBaseIndices`  
 \[out\]  TRUE per specificare che la matrice contiene indici di base \(limite inferiore\); in caso contrario, FALSE.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.