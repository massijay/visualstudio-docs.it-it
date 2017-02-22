---
title: "IDebugCoreServer3::QueryIsLocal | Microsoft Docs"
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
  - "IDebugCoreServer3::QueryIsLocal"
helpviewer_keywords: 
  - "IDebugCoreServer3::QueryIsLocal"
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::QueryIsLocal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina se il server è locale al chiamante.  
  
## Sintassi  
  
```cpp#  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```c#  
int QueryIsLocal();  
```  
  
## Valore restituito  
 Restituisce `S_OK` per indicare il server è locali.  Restituisce `S_FALSE` se il server è in esecuzione da un'istanza di msvsmon.exe, che viene in genere utilizzato per il debug remoto.  
  
## Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)