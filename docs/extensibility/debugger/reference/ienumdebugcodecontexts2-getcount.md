---
title: "IEnumDebugCodeContexts2::GetCount | Microsoft Docs"
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
  - "IEnumDebugCodeContexts2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2::GetCount"
ms.assetid: 74c52fcf-688c-40df-9acd-29b3b84e6216
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCodeContexts2::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce il numero di elementi nell'enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
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
 Questo metodo non fa parte dell'interfaccia solito di enumerazione COM che specifica che solo `Next`, `Clone`, `Skip`e i metodi di `Reset` devono essere distribuiti.  
  
## Vedere anche  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)