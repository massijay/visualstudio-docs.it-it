---
title: "IEnumDebugErrorBreakpoints2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugErrorBreakpoints2::Next"
helpviewer_keywords: 
  - "IEnumDebugErrorBreakpoints2::Next"
ms.assetid: 6a3dee11-5267-4d77-9e28-6a38413ba70b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugErrorBreakpoints2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce il set di elementi dell'enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Next(  
   ULONG                    celt,  
   IDebugErrorBreakpoint2** rgelt,  
   ULONG*                   pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                     celt,  
   IDebugErrorBreakpoint2[] rgelt,  
   ref uint                 pceltFetched  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\]  Il numero di elementi da recuperare.  Specifica inoltre la dimensione massima della matrice di `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Matrice [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) di elementi da riempire.  
  
 `pceltFetched`  
 \[out\]  Restituisce il numero di elementi effettivamente restituiti in `rgelt`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se meno che il numero richiesto degli elementi possono essere restituiti, in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)