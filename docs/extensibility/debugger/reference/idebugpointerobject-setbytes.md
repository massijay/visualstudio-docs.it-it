---
title: "IDebugPointerObject::SetBytes | Microsoft Docs"
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
  - "IDebugPointerObject::SetBytes"
helpviewer_keywords: 
  - "Metodo IDebugPointerObject::SetBytes"
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta il valore puntato da una serie di byte consecutivi.  
  
## Sintassi  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### Parametri  
 `dwStart`  
 \[in\]  Un offset, in byte, dall'inizio dell'oggetto a cui fa riferimento a.  
  
 `dwCount`  
 \[in\]  Il numero di byte da impostare.  
  
 `pBytes`  
 \[in\]  Una matrice di byte che rappresenta il nuovo valore.  Questo valore viene archiviato nell'oggetto, a partire dall'offset specificato.  
  
 `pdwBytes`  
 \[out\]  Restituisce il numero di byte in realtà impostati.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene utilizzato quando il puntatore come rappresentato da questi [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punti a un tipo primitivo o a una matrice semplice di tipi primitivi \(ovvero una matrice che può essere rappresentata da una sequenza semplice di byte\).  Questo oggetto di `IDebugPointerObject` non può essere un riferimento Null \(necessario indicare un indirizzo di memoria\).  
  
## Vedere anche  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)