---
title: "IDiaSymbol::get_hasLongJump | Microsoft Docs"
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
  - "IDiaSymbol::get_hasLongJump (metodo)"
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hasLongJump
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un flag che indica se la funzione contiene un utilizzo di [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) comando \(abbinato a un oggetto  [setjmp](/visual-cpp/c-runtime-library/reference/setjmp) ordinare, questi formano il metodo di tipo C gestione delle eccezioni\).  
  
## Sintassi  
  
```cpp#  
HRESULT get_hasLongJump  
   BOOL *pFlag  
);  
```  
  
#### Parametri  
 `pFlag`  
 \[out\]  Restituisce `TRUE` se la funzione contiene un oggetto  `longjmp` comando; in caso contrario, restituisce  `FALSE`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v8.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)   
 [longjmp](/visual-cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/visual-cpp/c-runtime-library/reference/setjmp)