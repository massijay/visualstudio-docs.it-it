---
title: "IEEDataStorage::GetSize | Microsoft Docs"
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
  - "IEEDataStorage::GetSize"
helpviewer_keywords: 
  - "IEEDataStorage::GetSize"
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEDataStorage::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce il numero di byte contenuti in questo oggetto.  
  
## Sintassi  
  
```cpp#  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```c#  
int GetSize(  
   out uint size  
);  
```  
  
#### Parametri  
 `size`  
 \[out\]  Il numero di byte contenuti in questo oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Utilizzare [GetData](../Topic/IEEDataStorage::GetData.md) il metodo per recuperare i byte di dati.  
  
## Vedere anche  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../Topic/IEEDataStorage::GetData.md)