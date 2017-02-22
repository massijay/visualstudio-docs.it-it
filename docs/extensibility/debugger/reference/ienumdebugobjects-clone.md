---
title: "IEnumDebugObjects::Clone | Microsoft Docs"
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
  - "IEnumDebugObjects::Clone"
helpviewer_keywords: 
  - "Metodo IEnumDebugObjects::Clone"
ms.assetid: cb7df109-d29a-4218-b900-6809091459dd
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugObjects::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo restituisce una copia dell'enumerazione corrente come un oggetto separato.  
  
## Sintassi  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugObjects** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugObjects ppEnum  
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
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)