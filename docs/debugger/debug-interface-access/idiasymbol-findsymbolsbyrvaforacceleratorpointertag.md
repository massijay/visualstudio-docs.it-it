---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dato un valore corrispondente tag, questo metodo restituisce un'enumerazione di simboli contenuti in questa funzione stub a un indirizzo virtuale relativo specificato.  
  
## Sintassi  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### Parametri  
 `tagValue`  
 \[in\] il valore del tag del puntatore per il quale i record del simbolo di pointee viene trovato.  
  
 `rva`  
 \[in\] il rva utilizzato per filtrare i simboli corrispondenti alla variabile di pointee il valore specificato nel tag.  
  
 `ppResult`  
 \[out\] puntatore A un puntatore a interfaccia `IDiaEnumSymbols` inizializzato con il risultato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## Note  
 Chiamare questo metodo solo in un'interfaccia `IDiaSymbol` che corrisponde a una funzione dello stub dei tasti di scelta rapida.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)