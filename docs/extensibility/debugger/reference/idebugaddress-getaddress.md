---
title: "IDebugAddress::GetAddress | Microsoft Docs"
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
  - "IDebugAddress::GetAddress"
helpviewer_keywords: 
  - "Metodo IDebugAddress:GetAddress"
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce una struttura che descrive un oggetto e la relativa posizione all'interno del relativo ambito o contenitore.  
  
## Sintassi  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```c#  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### Parametri  
 `pAddress`  
 \[in, out\]  [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Una struttura che viene soddisfatta da questo metodo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) La struttura viene passata al metodo, che quindi il riempimento in con le informazioni appropriate.  Come queste informazioni vengono interpretate dipende dal tipo di dati restituito e del gestore dei simboli stesso.  Per ulteriori informazioni, vedere [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md).  
  
## Vedere anche  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)