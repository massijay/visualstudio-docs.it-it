---
title: "IEnumDebugReferenceInfo2::Clone | Microsoft Docs"
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
  - "IEnumDebugReferenceInfo2::Clone"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2::Clone"
ms.assetid: 49c5a301-a33a-428f-b83b-e734c71af4ef
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugReferenceInfo2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce una copia dell'enumerazione corrente come un oggetto separato.  
  
## Sintassi  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### Parametri  
 `ppEnum`  
 \[out\]  restituisce una copia di questa enumerazione come un oggetto separato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 La copia l'enumerazione presenta lo stesso stato originale quando questo metodo viene chiamato.  Tuttavia, la copia e gli stati originali sono separati e possono essere modificati singolarmente.  
  
## Vedere anche  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)