---
title: "IDiaSymbol::get_oemSymbolId | Microsoft Docs"
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
  - "IDiaSymbol::get_oemSymbolId (metodo)"
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_oemSymbolId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il valore originale dell'ID del simbolo \(OEM\) del produttore dell'attrezzatura.  
  
## Sintassi  
  
```cpp#  
HRESULT get_oemSymbolId (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce un ID internamente assegnata del simbolo OEM  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 L'identificatore è un valore univoco creato dal DIA SDK per contrassegnare i simboli quali univoco.  
  
 Questa proprietà si applica solo ai simboli con un oggetto [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) tipo di  `SymTagCustomType`.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)