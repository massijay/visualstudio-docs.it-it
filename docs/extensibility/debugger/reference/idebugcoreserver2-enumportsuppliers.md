---
title: "IDebugCoreServer2::EnumPortSuppliers | Microsoft Docs"
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
  - "IDebugCoreServer2::EnumPortSuppliers"
helpviewer_keywords: 
  - "IDebugCoreServer2::EnumPortSuppliers"
ms.assetid: ce0c90e4-8e02-4b08-b558-7677fb2c88f7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer2::EnumPortSuppliers
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera un elenco di tutti i fornitori di porte disponibili.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumPortSuppliers(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```c#  
int EnumPortSuppliers(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### Parametri  
 `ppEnum`  
 \[out\]  restituisce [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) un oggetto che contiene un elenco di tutti i fornitori di porte.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)