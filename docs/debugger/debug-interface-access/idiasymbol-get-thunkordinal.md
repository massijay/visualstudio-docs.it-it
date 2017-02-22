---
title: "IDiaSymbol::get_thunkOrdinal | Microsoft Docs"
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
  - "IDiaSymbol::get_thunkOrdinal (metodo)"
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera il tipo di thunk di funzione.  
  
## Sintassi  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce un valore dal [Enumerazione THUNK\_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) enumerazione che specifica il tipo di thunk di funzione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 Questa proprietà è valida solo se il simbolo ad esempio [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valore di  `SymTagThunk`.  
  
 “Un thunk„ è un frammento di codice che converte tra uno spazio indirizzo di memoria pari a 32 bit \(anche noto come spazio degli indirizzi sono\) e uno spazio degli indirizzi a 16 bit \(noto come spazio degli indirizzi segmentato\).  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione THUNK\_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)