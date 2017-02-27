---
title: "IDebugCoreServer3::GetServerName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::GetServerName"
helpviewer_keywords: 
  - "IDebugCoreServer3::GetServerName"
ms.assetid: 0fc3fcf5-d6a3-4a00-bf14-458b8645714e
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3::GetServerName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera il nome del server.  
  
## Sintassi  
  
```cpp#  
HRESULT GetServerName(  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetServerName(  
   out string pbstrName  
);  
```  
  
#### Parametri  
 `pbstrName`  
 \[out\]  Restituisce il nome del server.  
  
> [!NOTE]
>  Il chiamante è responsabile della versione della stringa.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Note  
 Per un nome di server descrittivo, chiamare [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md) il metodo.  
  
## Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)