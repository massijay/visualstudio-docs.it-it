---
title: "IDebugSymbolProviderDirect::GetSymUnmanagedReader | Microsoft Docs"
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
  - "GetSymUnmanagedReader"
  - "IDebugSymbolProviderDirect::GetSymUnmanagedReader"
ms.assetid: 147bacfa-f66c-43e0-8a72-e601058dc57f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProviderDirect::GetSymUnmanagedReader
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un reader di simboli per il codice non gestito.  
  
## Sintassi  
  
```cpp#  
HRESULT GetSymUnmanagedReader (  
   ULONG32    ulAppDomainID,  
   GUID       guidModule,  
   IUnknown** ppSymUnmanagedReader  
);  
```  
  
```c#  
int GetSymUnmanagedReader (  
   uint       ulAppDomainID,  
   Guid       guidModule,  
   out object ppSymUnmanagedReader  
);  
```  
  
#### Parametri  
 `ulAppDomainID`  
 \[in\]  Identificatore del dominio applicazione.  
  
 `guidModule`  
 \[in\]  Identificatore univoco del modulo.  
  
 `ppSymUnmanagedReader`  
 \[out\]  Restituisce un oggetto che rappresenta il reader di simboli per il codice non gestito.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)