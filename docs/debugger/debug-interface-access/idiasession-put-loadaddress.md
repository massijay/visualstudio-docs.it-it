---
title: "IDiaSession::put_loadAddress | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaSession::put_loadAddress (metodo)"
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Imposta l'indirizzo del caricamento del file eseguibile che corrisponde ai simboli in questo archivio di simboli.  
  
## Sintassi  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### Parametri  
 `NewVal`  
 \[in\]  Indirizzo del caricamento del file eseguibile.  
  
## Note  
 Le proprietà di indirizzo virtuale \(VA\) del simbolo vengono calcolate utilizzando il valore di questo metodo.  Gli indirizzi virtuali non viene calcolato a meno che la proprietà sia impostata su diverso da zero.  
  
> [!NOTE]
>  È necessario chiamare questo metodo se si ottengono [IDiaSession](../../debugger/debug-interface-access/idiasession.md) oggetto e prima di iniziare utilizzando l'oggetto se è necessario utilizzare qualsiasi proprietà virtuali sui simboli.  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)