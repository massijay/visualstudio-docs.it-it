---
title: "IDebugProperty2::GetReference | Microsoft Docs"
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
  - "IDebugProperty2::GetReference"
helpviewer_keywords: 
  - "Metodo IDebugProperty2::GetReference"
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::GetReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce un riferimento al valore della proprietà.  
  
## Sintassi  
  
```cpp#  
HRESULT GetReference(  
   IDebugReference2** ppReference  
);  
```  
  
```c#  
int GetReference(  
   out IDebugReference2 ppReference  
);  
```  
  
#### Parametri  
 `ppRererence`  
 \[out\]  Restituisce [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) un oggetto che rappresenta un riferimento al valore della proprietà.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore, in genere `E_NOTIMPL` o `E_GETREFERENCE_NO_REFERENCE`.  
  
## Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)