---
title: "IPropertyProxyEESide::GetInitialData | Microsoft Docs"
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
  - "IPropertyProxyEESide::GetInitialData"
helpviewer_keywords: 
  - "IPropertyProxyEESide::GetInitialData"
ms.assetid: 36cceb19-2604-4ef9-b42b-5dd30cbe24b1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide::GetInitialData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

restituisce i dati iniziali per questo oggetto.  
  
## Sintassi  
  
```cpp#  
HRESULT GetInitialData(  
   IEEDataStorage** dataOut  
);  
```  
  
```c#  
int GetInitialData(  
   out IEEDataStorage dataOut  
);  
```  
  
#### Parametri  
 `dataOut`  
 \[out\]  Restituisce [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) un oggetto contenente i dati iniziali di questo oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)