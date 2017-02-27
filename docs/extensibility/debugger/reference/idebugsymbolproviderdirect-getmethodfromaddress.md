---
title: "IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetMethodFromAddress"
  - "GetMethodFromAddress"
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera le informazioni sul metodo all'indirizzo specificato di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```c#  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### Parametri  
 `pAddress`  
 \[in\]  Eseguire il debug l'indirizzo che è rappresentato [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) dall'interfaccia.  
  
 `pGuid`  
 \[out\]  Identificatore univoco del modulo.  
  
 `pAppID`  
 \[out\]  Identificatore del dominio applicazione.  
  
 `pTokenClass`  
 \[out\]  Token che rappresenta la classe contenitore.  
  
 `pTokenMethod`  
 \[out\]  token che rappresenta il modulo.  
  
 `pdwOffset`  
 \[out\]  Un offset in byte dall'inizio del parametro di `pAddress` .  
  
 `pdwVersion`  
 \[out\]  Numero di versione del metodo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)