---
title: "IDiaSession::findSymbolsForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Restituisce un'enumerazione dei simboli per la variabile che il valore specificato di tag corrisponde alla funzione padre stub dei tasti di scelta rapida.  
  
## Sintassi  
  
```cpp#  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parametri  
 `parent`  
 \[in\] un IDiaSymbol che corrisponde alla funzione di uno stub di scelta rapida da cercare.  
  
 `tagValue`  
 \[in\] il valore del tag del puntatore.  
  
 `ppResult`  
 \[out\] puntatore A un puntatore a interfaccia `IDiaEnumSymbols` inizializzato con il risultato.  
  
## Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)