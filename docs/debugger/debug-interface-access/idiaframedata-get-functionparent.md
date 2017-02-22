---
title: "IDiaFrameData::get_functionParent | Microsoft Docs"
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
  - "IDiaFrameData::get_functionParent (metodo)"
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_functionParent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un'interfaccia di dati del frame per la funzione che lo contiene.  
  
## Sintassi  
  
```cpp#  
HRESULT get_functionParent (   
   IDiaFrameData** pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) oggetto per la funzione che lo contiene.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)