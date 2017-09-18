---
title: "IDebugField::GetContainer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetContainer"
helpviewer_keywords: 
  - "Metodo IDebugField::GetContainer"
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetContainer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questo metodo ottiene il contenitore di un campo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetContainer(   
   IDebugContainerField** ppContainerField  
);  
```  
  
```c#  
int GetContainer(  
   out IDebugContainerField ppContainerField  
);  
```  
  
#### Parametri  
 `ppContainerField`  
 \[out\]  Restituisce il contenitore come rappresentato [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) dall'interfaccia.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Se questo campo non dispone di un contenitore, `ppContainerField` restituito sarà un valore null.  
  
## Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)