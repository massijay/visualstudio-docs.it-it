---
title: "IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs"
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
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Restituisce tutti i valori del tag del puntatore di scelta rapida che corrispondono alla funzione stub di tasti di scelta rapida AMP C\+\+.  
  
## Sintassi  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### Parametri  
 `cnt`  
 \[in\] dimensione della matrice di output `pPointerTags`.  
  
 `pcnt`  
 \[out\] numero dei tag del puntatore di scelta rapida nella funzione stub di tasti di scelta rapida AMP C\+\+.  
  
 `pPointerTags`  
 \[out\] puntatore a matrice A `DWORD` che viene riempito con un tag del puntatore di scelta rapida stima nella funzione stub di tasti di scelta rapida AMP C\+\+.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## Note  
 Questo metodo viene chiamato in un'interfaccia `IDiaSymbol` che corrisponde alla funzione stub di tasti di scelta rapida AMP C\+\+.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)