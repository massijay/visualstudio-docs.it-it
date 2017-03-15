---
title: "IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dato un valore corrispondente tag, questo metodo restituisce un'enumerazione di simboli contenuti in una funzione padre specificata di uno stub di scelta rapida a un indirizzo virtuale relativo specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parametri  
 `parent`  
 \[in\] `IDiaSymbol` che corrisponde alla funzione di uno stub di scelta rapida da cercare.  
  
 `tagValue`  
 \[in\] il valore del tag del puntatore.  
  
 `rva`  
 \[in\] indirizzo virtuale relativo.  
  
 `ppResult`  
 \[out\] puntatore A un puntatore a interfaccia `IDiaEnumSymbols` inizializzato con il risultato.  
  
## Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## Note  
 Chiamare questo metodo solo in un'interfaccia `IDiaSymbol` che corrisponde a una funzione dello stub dei tasti di scelta rapida.  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)