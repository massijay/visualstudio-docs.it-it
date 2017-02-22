---
title: "IDebugEngine2::RemoveSetException | Microsoft Docs"
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
  - "IDebugEngine2::RemoveSetException"
helpviewer_keywords: 
  - "IDebugEngine2::RemoveSetException"
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::RemoveSetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Rimuove eccezione specificata in modo da più non è gestita dal motore di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### Parametri  
 `pException`  
 \[in\]  [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) una struttura che descrive l'eccezione da rimuovere.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Eccezione che viene rimossa sia stata precedentemente impostata da una chiamata precedente [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) al metodo.  
  
 Per rimuovere tutte le eccezioni stabilito immediatamente, chiamare [RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md) il metodo.  
  
## Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)