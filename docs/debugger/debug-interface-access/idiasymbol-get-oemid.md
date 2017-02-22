---
title: "IDiaSymbol::get_oemId | Microsoft Docs"
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
  - "IDiaSymbol::get_oemId (metodo)"
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_oemId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il valore originale del produttore dell'\(OEM\) attrezzatura di ID di simboli.  
  
## Sintassi  
  
```cpp#  
HRESULT get_oemId (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce un valore univoco che identifica un OEM.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 Questa proprietà si applica solo ai simboli con un oggetto [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) tipo di  `SymTagCustomType`.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)