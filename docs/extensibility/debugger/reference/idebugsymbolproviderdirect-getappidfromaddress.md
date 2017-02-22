---
title: "IDebugSymbolProviderDirect::GetAppIDFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetAppIDFromAddress"
  - "GetAppIDFromAddress"
ms.assetid: d76a0f36-79c4-4c58-9db3-880b00d11610
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProviderDirect::GetAppIDFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera l'identificatore del dominio applicazione fornito l'indirizzo di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT GetAppIDFromAddress(  
   IDebugAddress* pAddress,  
   DWORD*         pAppID  
);  
```  
  
```c#  
int GetAppIDFromAddress(  
   IDebugAddress pAddress,  
   out uint      pAppID  
);  
```  
  
#### Parametri  
 `pAddress`  
 \[in\]  Eseguire il debug l'indirizzo che è rappresentato [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) dall'interfaccia.  
  
 `pAppID`  
 \[out\]  Identificatore del dominio applicazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)