---
title: "IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetAttributeBytes"
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene informazioni su come BLOB di byte.  
  
## Sintassi  
  
```cpp#  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```c#  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### Parametri  
 `ppBlob`  
 \[in, out\]  Una matrice che viene soddisfatta di byte di attributo.  
  
 `pdwLen`  
 \[in, out\]  Specifica il numero massimo di byte da restituire nella matrice di `ppBlob` e restituisce il numero di byte in realtà scritti nella matrice.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Impostare il parametro di `ppBlob` a un valore null per restituire il numero di byte di attributi disponibili.  Quindi allocare una matrice e passare la matrice in per il parametro di `ppBlob` .  
  
 I byte di attributo rappresentano i dati non elaborati l'attributo personalizzato.  
  
## Vedere anche  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)