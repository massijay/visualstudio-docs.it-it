---
title: "IDebugField::GetTypeInfo | Microsoft Docs"
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
  - "IDebugField::GetTypeInfo"
helpviewer_keywords: 
  - "Metodo IDebugField::GetTypeInfo"
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::GetTypeInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo recupera le informazioni dell'tipo\-indipendente sul simbolo o il tipo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```c#  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### Parametri  
 `pTypeInfo`  
 \[out\]  Restituisce le informazioni sul tipo nella struttura fornita [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) .  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 le informazioni dell'Tipo\-indipendente dovrebbero includere, ad esempio, l'AppDomain, il modulo e la classe che contiene il simbolo.  
  
## Vedere anche  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)