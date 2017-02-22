---
title: "IDebugCoreServer2::GetPortSupplier | Microsoft Docs"
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
  - "IDebugCoreServer2::GetPortSupplier"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetPortSupplier"
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer2::GetPortSupplier
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera un fornitore di porte specifico.  
  
## Sintassi  
  
```cpp#  
HRESULT GetPortSupplier(   
   REFGUID               guidPortSupplier,  
   IDebugPortSupplier2** ppPortSupplier  
);  
```  
  
```c#  
int GetPortSupplier(   
   ref Guid                guidPortSupplier,  
   out IDebugPortSupplier2 ppPortSupplier  
);  
```  
  
#### Parametri  
 `guidPortSupplier`  
 \[in\]  GUID del fornitore di porte da recuperare.  
  
 `ppPortSupplier`  
 \[out\]  restituisce [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) un oggetto che rappresenta il fornitore di porte desiderato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)