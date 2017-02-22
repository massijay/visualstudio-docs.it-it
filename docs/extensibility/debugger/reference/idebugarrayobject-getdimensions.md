---
title: "IDebugArrayObject::GetDimensions | Microsoft Docs"
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
  - "IDebugArrayObject::GetDimensions"
helpviewer_keywords: 
  - "Metodo IDebugArrayObject::GetDimensions"
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene le dimensioni della matrice.  
  
## Sintassi  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```c#  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### Parametri  
 `dwCount`  
 \[in\]  Il numero di dimensioni da recuperare.  
  
 `dwDimensions`  
 \[in, out\]  Una matrice che viene riempita con dimensioni di ciascuna dimensione.  `dwCount` specifica la dimensione massima della matrice di `dwDimensions` .  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Una matrice multidimensionale può presentare dimensioni diverse per ciascuna dimensione.  Ad esempio, data la matrice tridimensionale `myarray[3][2][6]`, questo metodo restituisce 3, 2 e 6 nel parametro di `dwDimensions` in questo ordine.  
  
## Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)