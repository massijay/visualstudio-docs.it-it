---
title: "IDiaSymbol::get_offset | Microsoft Docs"
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
  - "IDiaSymbol::get_offset (metodo)"
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_offset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recuperare l'offset della posizione del simbolo.  Utilizzare quando [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) viene  `LocIsRegRel` o  `LocIsBitField`.  
  
## Sintassi  
  
```cpp#  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce l'offset in byte della posizione del simbolo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 L'offset proviene da un certo punto noto in precedenza determinato.  Ad esempio, l'offset per un oggetto `LocIsBitField` il tipo del percorso è in genere dall'inizio della classe contenitore.  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v7.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)