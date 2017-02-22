---
title: "IDiaSymbol::get_editAndContinueEnabled | Microsoft Docs"
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
  - "IDiaSymbol::get_editAndContinueEnabled (metodo)"
ms.assetid: cd703c64-9ff8-4654-8493-8cde9309cb22
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_editAndContinueEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera un flag che indica se il modulo è stato compilato con [\/Z7, \/Zi, \/ZI \(Formato informazioni di debug\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) opzione del compilatore.  
  
## Sintassi  
  
```cpp#  
HRESULT get_editAndContinueEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce `TRUE` se Modifica e continuazione è attivato alla compilazione; in caso contrario, restituisce  `FALSE`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v7.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [\/Z7, \/Zi, \/ZI \(Formato informazioni di debug\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)