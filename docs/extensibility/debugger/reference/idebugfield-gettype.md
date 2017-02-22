---
title: "IDebugField::GetType | Microsoft Docs"
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
  - "IDebugField::GetType"
helpviewer_keywords: 
  - "Metodo IDebugField::GetType"
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::GetType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questo metodo ottiene il tipo di campo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```c#  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### Parametri  
 `ppType`  
 \[out\]  restituisce il tipo di campo come altro [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)