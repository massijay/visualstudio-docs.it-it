---
title: "IDiaStackWalkHelper::symbolForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper::symbolForVA (metodo)"
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::symbolForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il simbolo contenente l'indirizzo virtuale specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### Parametri  
 `va`  
 \[in\]  Indirizzo virtuale che è contenuto nel simbolo richiesto.  Il simbolo deve corrispondere a `SymTagFunctionType` \(un valore dal  [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumerazione\).  
  
 `ppSymbol`  
 \[out\]   [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il simbolo all'indirizzo specificato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)