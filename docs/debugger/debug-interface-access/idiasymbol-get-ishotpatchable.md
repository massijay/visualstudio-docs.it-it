---
title: "IDiaSymbol::get_isHotpatchable | Microsoft Docs"
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
  - "IDiaSymbol::get_isHotpatchable (metodo)"
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isHotpatchable
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera un flag che indica se il modulo è stato compilato con [\/hotpatch \(Crea immagine con funzionalità di patch a caldo\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) opzione del compilatore.  
  
## Sintassi  
  
```cpp#  
HRESULT get_isHotpatchable(  
   BOOL *pFlag  
);  
```  
  
#### Parametri  
 `pFlag`  
 \[out\]  Restituisce `TRUE` se il modulo è caldo\-patchable; in caso contrario, restituisce  `FALSE`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 Questa proprietà è disponibile da `SymTagCompilandDetails` tipo di simboli \(vedere  [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)\).  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v8.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)