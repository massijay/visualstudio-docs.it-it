---
title: "IDiaSymbol::get_constType | Microsoft Docs"
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
  - "IDiaSymbol::get_constType (metodo)"
ms.assetid: cb43605e-fa39-4f83-b047-f936a8019d03
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_constType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un flag che indica se il tipo di dati definito dall'utente è costante.  
  
## Sintassi  
  
```cpp#  
HRESULT get_constType (   
   BOOL* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce `TRUE` se il tipo di dati definito dall'utente è una costante; in caso contrario, restituisce  `FALSE`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v7.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)