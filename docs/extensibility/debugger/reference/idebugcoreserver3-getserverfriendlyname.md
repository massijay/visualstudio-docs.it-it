---
title: "IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs"
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
  - "IDebugCoreServer3::GetServerFriendlyName"
helpviewer_keywords: 
  - "IDebugCoreServer3::GetServerFriendlyName"
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera un nome descrittivo per il server.  
  
## Sintassi  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### Parametri  
 `pbstrName`  
 \[out\]  restituisce un nome descrittivo per il server.  
  
> [!NOTE]
>  Il chiamante è responsabile della versione della stringa.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Note  
 Per i server utente\-avviati, il nome restituito da questo metodo è il nome completo del server.  Per i server auto\-avviati, il nome è quello del computer del server viene eseguito.  
  
 Per un nome orientato alla macchina, chiamare [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) il metodo.  
  
## Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)