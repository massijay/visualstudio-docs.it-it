---
title: "IDebugProperty2::GetDerivedMostProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
helpviewer_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ottiene la proprietà derivata\-più di una proprietà.  
  
## Sintassi  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### Parametri  
 `ppDerivedMost`  
 \[out\]  restituisce [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) un oggetto che rappresenta la proprietà derivata\-più.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce il codice di errore.  Restituisce `S_GETDERIVEDMOST_NO_DERIVED_MOST` se non c " è proprietà derivata\-più da recuperare.  
  
## Note  
 Ad esempio, se la proprietà viene illustrato un oggetto che implementa `ClassRoot` ma che rappresenti una creazione di istanze di `ClassDerived` derivata da `ClassRoot`, pertanto questo metodo [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) restituisce un oggetto che descrive l'oggetto di `ClassDerived` .  
  
## Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)