---
title: "IDiaSymbol::get_targetRelativeVirtualAddress | Microsoft Docs"
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
  - "IDiaSymbol::get_targetRelativeVirtualAddress (metodo)"
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_targetRelativeVirtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera indirizzo \(RVA\) virtuale relativo di una destinazione di thunk.  
  
## Sintassi  
  
```cpp#  
HRESULT get_targetRelativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce il gli indirizzi RVA di un database di destinazione di thunk.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 Questa proprietà è valida solo se il simbolo ad esempio [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valore di  `SymTagThunk`.  
  
 “Un thunk„ è un frammento di codice che converte tra uno spazio indirizzo di memoria pari a 32 bit \(anche noto come spazio degli indirizzi sono\) e uno spazio degli indirizzi a 16 bit \(noto come spazio degli indirizzi segmentato\).  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)