---
title: "IDiaSymbol::get_upperBoundId | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_upperBoundId (metodo)"
ms.assetid: ddfa1617-bd0f-4187-ba77-a225bab93a95
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_upperBoundId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera l'identificatore del simbolo del limite superiore della dimensione di una matrice FORTRAN.  
  
## Sintassi  
  
```cpp#  
HRESULT get_upperBoundId (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\], restituisce l'ID del simbolo che rappresenta il limite superiore della dimensione di una matrice FORTRAN.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 L'identificatore è un valore univoco creato dal DIA SDK per contrassegnare i simboli quali univoco.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)