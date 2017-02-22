---
title: "THUNK_ORDINAL | Microsoft Docs"
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
  - "Thunk_Ordinal (enumerazione)"
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

definisce i tipi di thunk.  
  
## Sintassi  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## Elementi  
 THUNK\_ORDINAL\_NOTYPE  
 thunk standard.  
  
 THUNK\_ORDINAL\_ADJUSTOR  
 In `this` thunk del controller master.  
  
 THUNK\_ORDINAL\_VCALL  
 thunk di chiamata virtuale.  
  
 THUNK\_ORDINAL\_PCODE  
 thunk di P\-codice.  
  
 THUNK\_ORDINAL\_LOAD  
 Ritardare il thunk di caricamento.  
  
 THUNK\_ORDINAL\_TRAMP\_INCREMENTAL  
 Thunk incrementale di trampolino \(un thunk di trampolino viene utilizzato per rimbalzare le chiamate dallo spazio di memoria a un altro\).  
  
 THUNK\_ORDINAL\_TRAMP\_BRANCHISLAND  
 Thunk di trampolino del punto di diramazione.  
  
## Note  
 I valori in questa enumerazione restituiti da una chiamata a [IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) metodo.  
  
## Requisiti  
 intestazione: cvconst.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)