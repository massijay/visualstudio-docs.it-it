---
title: "NameSearchOptions | Microsoft Docs"
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
  - "NameSearchOptions (enumerazione)"
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# NameSearchOptions
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Specifica le opzioni di ricerca del simbolo e i nomi di file.  
  
## Sintassi  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## Elementi  
 `nsNone`  
 Non è stata specificata alcuna opzione.  
  
 `nsfCaseSensitive`  
 Applica una corrispondenza con distinzione tra maiuscole e minuscole dei nomi.  
  
 `nsfCaseInsensitive`  
 Applica una corrispondenza senza distinzione tra maiuscole e minuscole dei nomi.  
  
 `nsfFNameExt`  
 I nomi di considera come percorsi e applica la corrispondenza del nome di filename.ext.  
  
 `nsfRegularExpression`  
 Applica una corrispondenza con distinzione tra maiuscole e minuscole dei nomi utilizzando gli asterischi \(\*\) e punti interrogativi \(?\) come caratteri jolly.  
  
 `nsfUndecoratedName`  
 Si applica solo ai simboli che dispongono di nomi non decorato che decorati.  
  
## Note  
 I valori di questa enumerazione vengono passati ai metodi seguenti:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Requisiti  
 intestazione: dia2.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)