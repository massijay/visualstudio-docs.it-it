---
title: "IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartAddressOffset"
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_liveRangeStartAddressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Restituisce parte dell'offset indirizzo iniziale dell'intervallo in cui il simbolo locale è valido.  
  
## Sintassi  
  
```cpp#  
HRESULT get_liveRangeStartAddressOffset (   
   DWORD* offset  
);  
```  
  
#### Parametri  
 `offset`  
 \[out\]  Restituisce parte dell'offset dall'intervallo di indirizzo iniziale.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
> [!NOTE]
>  Un codice di errore restituito indica che il simbolo non dispone di informazioni attive l'intervallo.  
  
## Note  
 L'indirizzo formato collegando dalla sezione e dall'offset è l'inizio dell'intervallo in cui il simbolo è valido.  
  
 Per ottenere la parte della sezione di indirizzo, utilizzare [IDiaSymbol::get\_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)