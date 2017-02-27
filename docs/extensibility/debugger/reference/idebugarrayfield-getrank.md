---
title: "IDebugArrayField::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetRank"
helpviewer_keywords: 
  - "Metodo IDebugArrayField::GetRank"
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il numero di dimensioni o il numero di dimensioni della matrice.  
  
## Sintassi  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### Parametri  
 `pdwRank`  
 \[out\]  Restituisce il numero di dimensioni.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il numero di dimensioni di una matrice corrisponde al numero di dimensioni.  In C\+\+ e c\#, le matrici multidimensionali sono effettivamente matrici di matrici e possono quindi essere considerate solo una matrice unidimensionale e di `GetRank` il metodo restituisca sempre 1\).  In [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], di altra parte, le matrici multidimensionali sono gestite in modo diverso e il numero di dimensioni di una matrice riflette il numero di dimensioni \(e il metodo di `GetRank` restituisce sempre il numero di dimensioni.  
  
## Vedere anche  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)