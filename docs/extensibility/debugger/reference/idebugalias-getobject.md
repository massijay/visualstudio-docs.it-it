---
title: "IDebugAlias::GetObject | Microsoft Docs"
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
  - "IDebugAlias::GetObject"
helpviewer_keywords: 
  - "Metodo IDebugAlias::GetObject"
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias::GetObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene l'oggetto che tale alias per.  
  
## Sintassi  
  
```cpp  
HRESULT GetObject(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetObject(  
   Out IDebugObject2 ppObject  
)  
```  
  
#### Parametri  
 `ppObject`  
 \[out\]  [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) Il tale alias rappresenta.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)