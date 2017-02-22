---
title: "IDebugSymbolProvider::GetNamespacesUsedAtAddress | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetNamespacesUsedAtAddress"
helpviewer_keywords: 
  - "Metodo IDebugSymbolProvider::GetNamespacesUsedAtAddress"
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetNamespacesUsedAtAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo crea un enumeratore per gli spazi dei nomi associati all'indirizzo di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT GetNamespacesUsedAtAddress(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int GetNamespacesUsedAtAddress(  
   IDebugAddress        pAddress,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parametri  
 `pAddress`  
 \[in\]  l'indirizzo di debug.  
  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) un enumeratore per gli spazi dei nomi.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 È possibile che si verifichino numerosi spazi dei nomi associati a un indirizzo specificato di debug, ad esempio, spazi dei nomi annidati o più istruzioni di `using` .  
  
## Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)