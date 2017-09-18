---
title: "IDebugField::Equal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::Equal"
helpviewer_keywords: 
  - "Metodo IDebugField::Equal"
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::Equal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo consente di confrontare questo campo con il campo specificato per uguaglianza.  
  
## Sintassi  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```c#  
int Equal(  
   IDebugField pField  
);  
```  
  
#### Parametri  
 `pField`  
 \[in\]  il campo da confrontare a questo.  
  
## Valore restituito  
 Se i campi sono uguali, restituisce `S_OK`.  Se i campi sono diversi, restituisce `S_FALSE.` in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)