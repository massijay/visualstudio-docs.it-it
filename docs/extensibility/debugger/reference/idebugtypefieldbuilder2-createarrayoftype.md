---
title: "IDebugTypeFieldBuilder2::CreateArrayOfType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugTypeFieldBuilder2::CreateArrayOfType"
  - "CreateArrayOfType"
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugTypeFieldBuilder2::CreateArrayOfType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea una matrice di tipo e le dimensioni specificate.  
  
## Sintassi  
  
```cpp#  
HRESULT CreateArrayOfType (  
   IDebugField*  pTypeField,  
   DWORD         rank,  
   IDebugField** pArrayOfTypeField  
);  
```  
  
```c#  
int CreateArrayOfType (  
   IDebugField     pTypeField,  
   uint            rank,  
   out IDebugField pArrayOfTypeField  
);  
```  
  
#### Parametri  
 `pTypeField`  
 \[in\]  Tipo di elementi della matrice utilizzata.  
  
 `rank`  
 \[in\]  Numero di elementi nella matrice.  
  
 `pArrayOfTypeField`  
 \[out\]  Restituisce [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetti che rappresentano la nuova matrice.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)