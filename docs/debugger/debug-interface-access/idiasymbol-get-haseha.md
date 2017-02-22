---
title: "IDiaSymbol::get_hasEHa | Microsoft Docs"
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
  - "IDiaSymbol::get_hasEHa (metodo)"
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hasEHa
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un flag che indica se la funzione contiene la gestione delle eccezioni strutturata \(\) asincrona.  
  
## Sintassi  
  
```cpp  
HRESULT get_hasEHa(  
   BOOL *pFlag  
);  
```  
  
#### Parametri  
 `pFlag`  
 \[out\]  Restituisce `TRUE` se la funzione prevede di gestione delle eccezioni asincrona, in caso contrario, restituisce  `FALSE`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 È possibile mischiare asincrono o la gestione delle eccezioni strutturata gestione delle eccezioni di in stile C\+\+, ma richiede un'opzione del compilatore specifica, \/EHa, per abilitarla.  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v8.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)