---
title: "IDebugCoreServer3::DisableAutoAttach | Microsoft Docs"
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
  - "IDebugCoreServer3::DisableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::DisableAutoAttach"
ms.assetid: 9d860a20-c154-4df4-ba15-636e0fcd42bf
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::DisableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Disabilita la connessione automatica per tutti i motori di debug associati a questo server.  
  
## Sintassi  
  
```cpp#  
HRESULT DisableAutoAttach(  
   void  
);  
```  
  
```c#  
int DisableAutoAttach();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)