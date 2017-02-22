---
title: "IEnumDebugFields::GetCount | Microsoft Docs"
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
  - "IEnumDebugFields::GetCount"
helpviewer_keywords: 
  - "Metodo IEnumDebugFields::GetCount"
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo restituisce il numero di elementi nell'enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```c#  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### Parametri  
 `pcelt`  
 \[out\]  Restituisce il numero di elementi nell'enumerazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo non fa parte dell'interfaccia solito di enumerazione COM che specifica che solo esigenze dopo, di clonazione, di salto e reimposta da implementare.  
  
## Vedere anche  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)