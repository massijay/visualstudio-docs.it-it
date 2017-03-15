---
title: "IDebugMemoryBytes2::ReadAt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryBytes2::ReadAt"
helpviewer_keywords: 
  - "Metodo IDebugMemoryBytes2::ReadAt"
  - "Metodo ReadAt"
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legge una sequenza di byte, a partire dalla posizione specificata.  
  
## Sintassi  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```c#  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### Parametri  
 `pStartContext`  
 \[in\]  [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) L'oggetto che specifica il percorso di avviare i byte di lettura.  
  
 `dwCount`  
 \[in\]  Numero di byte da leggere.  Specifica inoltre la lunghezza della matrice di `rgbMemory` .  
  
 `rgbMemory`  
 \[in, out\]  Matrice riempita con il numero di byte letti effettivamente da.  
  
 `pdwRead`  
 \[out\]  Restituisce il numero di byte contigui letti effettivamente da.  
  
 `pdwUnreadable`  
 \[in, out\]  Restituisce il numero di byte impedire.  Può essere un valore null se il client è disinteressato il numero dei byte impedire.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Se 100 byte necessari e i primi 50 leggibili, i 20 seguenti sono impedire e i 30 rimanenti leggibili, questo metodo restituisce:  
  
 \*`pdwRead` \= 50  
  
 \*`pdwUnreadable` \= 20  
  
 In questo caso, poiché `*pdwRead + *pdwUnreadable < dwCount`, il chiamante devono effettuare una chiamata a per leggere i 30 byte rimanenti di 100 originali richiesti e [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) l'oggetto passato nel parametro di `pStartContext` devono essere avanzati da 70.  
  
## Vedere anche  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)