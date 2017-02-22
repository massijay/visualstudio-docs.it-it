---
title: "IDiaSourceFile::get_compilands | Microsoft Docs"
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
  - "IDiaSourceFile::get_compilands (metodo)"
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_compilands
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un enumeratore dei moduli contenenti numeri di riga che fanno riferimento a questo file.  
  
## Sintassi  
  
```cpp#  
HRESULT get_compilands (   
   IDiaEnumSymbols** ppRetVal  
);  
```  
  
#### Parametri  
 `ppRetVal`  
 \[out\]  restituisce [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) oggetto che contiene un elenco di tutti i moduli contenenti numeri di riga che fanno riferimento a questo file.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)