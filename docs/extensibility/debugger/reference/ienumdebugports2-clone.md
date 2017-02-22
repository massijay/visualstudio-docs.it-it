---
title: "IEnumDebugPorts2::Clone | Microsoft Docs"
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
  - "IEnumDebugPorts2::Clone"
helpviewer_keywords: 
  - "IEnumDebugPorts2::Clone"
ms.assetid: d5ce77e8-bb99-409a-98fa-20fe5a0de25e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPorts2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce una copia dell'enumerazione corrente come un oggetto separato.  
  
## Sintassi  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugPorts2 ppEnum  
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
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)