---
title: "IDebugPointerObject::GetBytes | Microsoft Docs"
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
  - "IDebugPointerObject::GetBytes"
helpviewer_keywords: 
  - "Metodo IDebugPointerObject::GetBytes"
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il valore puntato come numero di byte consecutivi.  
  
## Sintassi  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### Parametri  
 `dwStart`  
 \[in\]  Un offset, in byte, dall'inizio dell'oggetto a cui fa riferimento a.  
  
 `dwCount`  
 \[in\]  Numero di byte da recuperare.  
  
 `pBytes`  
 \[in, out\]  Una matrice che viene riempita con valore come numero di byte consecutivi, a partire dall'offset specificato dall'oggetto a cui fa riferimento a.  
  
 `pdwBytes`  
 \[out\]  Restituisce il numero di byte effettivamente recuperate.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene utilizzato quando il puntatore come rappresentato da questi [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punti a un tipo primitivo o a una matrice semplice di tipi primitivi \(ovvero una matrice che può essere rappresentata da una sequenza semplice di byte\).  
  
## Vedere anche  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)