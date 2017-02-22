---
title: "IDiaSymbol::get_container | Microsoft Docs"
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
  - "IDiaSymbol::get_container (metodo)"
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_container
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa funzione recupera un puntatore a un simbolo che rappresenta il padre\/contenitore di questo simbolo.  
  
## Sintassi  
  
```cpp#  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce un puntatore a un oggetto `IDiaSymbol` contenere informazioni sul contenitore di questo simbolo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce S\_FALSE o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di S\_FALSE significa che la proprietà non è disponibile per il simbolo.  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v8.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)