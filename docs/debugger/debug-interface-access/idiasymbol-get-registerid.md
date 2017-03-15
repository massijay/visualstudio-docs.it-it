---
title: "IDiaSymbol::get_registerId | Microsoft Docs"
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
  - "IDiaSymbol::get_registerId (metodo)"
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera l'identificatore del registro della posizione quando [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è impostato su  `LocIsEnregistered`.  
  
## Sintassi  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce l'identificatore del registro della posizione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 Se il simbolo è relativo a un log, ovvero, se il simbolo [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è impostato su  `LocIsRegRel`, utilizzare  `get_registerId` metodo seguito da una chiamata a  [IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) metodo per recuperare l'offset del log in cui il simbolo si trova.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)