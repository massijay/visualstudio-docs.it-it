---
title: "IDiaFrameData::get_allocatesBasePointer | Microsoft Docs"
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
  - "IDiaFrameData::get_allocatesBasePointer (metodo)"
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera un flag che indica se il puntatore di base è allocato per il codice in questo intervallo di indirizzi.  Il metodo è deprecato.  
  
## Sintassi  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce `TRUE` se un puntatore di base è allocato, in caso contrario, restituisce  `FALSE`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se questa proprietà non è supportata.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Questa proprietà deve essere utilizzata solo dal codice che ha precedentemente eseguito FPO\_DATA, oppure quando la stringa del programma restituita da l [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) il metodo viene  `NULL`.  In caso contrario, la stringa del programma contiene tutte le informazioni necessarie per calcolare valori precedenti di log.  
  
## Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)