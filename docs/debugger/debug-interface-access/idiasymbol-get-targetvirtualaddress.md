---
title: "IDiaSymbol::get_targetVirtualAddress | Microsoft Docs"
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
  - "IDiaSymbol::get_targetVirtualAddress (metodo)"
ms.assetid: a0a5ce72-95f8-443e-bb4b-8c21194faad0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_targetVirtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera indirizzo \(VA\) virtuale di un database di destinazione di thunk.  
  
## Sintassi  
  
```cpp#  
HRESULT get_targetVirtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce il VA di un database di destinazione di thunk.  
  
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