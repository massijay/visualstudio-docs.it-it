---
title: "IDebugFunctionObject::CreateArrayObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateArrayObject"
helpviewer_keywords: 
  - "Metodo IDebugFunctionObject::CreateArrayObject"
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crea un oggetto matrice.  Questa matrice può contenere i valori dell'istanza dell'oggetto o della primitiva.  
  
## Sintassi  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### Parametri  
 `ot`  
 \[in\]  Specifica un valore [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) dell'enumerazione che indica il tipo del nuovo oggetto matrice.  
  
 `pClassField`  
 \[in\]  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Un oggetto che rappresenta la classe di oggetto, si crea una matrice di valori dell'istanza dell'oggetto.  Se creando una matrice di oggetti primitivi, questo parametro è un valore null.  
  
 `dwRank`  
 \[in\]  Il numero di dimensioni o il numero di dimensioni della matrice.  
  
 `dwDims`  
 \[in\]  Le dimensioni di ciascuna dimensione della matrice.  
  
 `dwLowBounds`  
 \[in\]  l'origine di ogni dimensione \(in genere 0 o 1\).  
  
 `ppObject`  
 \[out\]  Restituisce [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) un oggetto che rappresenta la matrice appena creato.  Ciò è [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) in realtà un oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un parametro di matrice alla funzione che è rappresentata [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) dall'interfaccia.  
  
## Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)