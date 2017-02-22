---
title: "IDiaSession::findAcceleratorInlineesByName | Microsoft Docs"
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
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Restituisce un'enumerazione di simboli per i frame inline che corrispondono al nome di funzione inline specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parametri  
 `name`  
 \[in\] il nome della funzione dell'entità incorporata da cercare.  
  
 `option`  
 \[in\] le opzioni di ricerca del nome possibile utilizzare quando si cercano frame inline che corrispondono a `name`.  Per ulteriori informazioni, vedere [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 \[out\] puntatore A un puntatore a interfaccia `IDiaEnumSymbols` inizializzato con il risultato.  
  
## Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## Note  
 Questa funzione cerca i inlinees solo all'interno delle funzioni dello stub dei tasti di scelta rapida.  Ignora i record nativi di routine C\+\+.  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)