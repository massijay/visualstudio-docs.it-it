---
title: "IDiaStackWalkFrame::searchForReturnAddressStart | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkFrame::searchForReturnAddressStart (metodo)"
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkFrame::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cercare lo stack frame specificato un indirizzo del mittente in corrispondenza dell'indirizzo specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT searchForReturnAddressStart (   
   IDiaFrameData* frame,  
   ULONGLONG      startAddress,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### Parametri  
 `frame`  
 \[in\]   [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) oggetto che rappresenta lo stack frame corrente.  
  
 `startAddress`  
 \[in\]  Un indirizzo di memoria virtuale da cui iniziare la ricerca.  
  
 `returnAddress`  
 \[out\]  Restituisce l'indirizzo di ritorno di una funzione più vicino a `startAddress`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)