---
title: "IDiaEnumInjectedSources::Next | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Next (metodo)"
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumInjectedSources::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un numero specificato di database di origine inseriti nella sequenza di enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### Parametri  
 celta  
 \[in\]  Il numero di database di origine inseriti nell'enumeratore da recuperare.  
  
 rgelt  
 \[out\]  restituisce una matrice di [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) oggetti che rappresenta il database di origine inseriti desiderati.  
  
 pceltFetched  
 \[out\]  Restituisce il numero di database di origine inseriti nell'enumeratore recuperato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se non sono presenti altri database di origine inseriti.  In caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)