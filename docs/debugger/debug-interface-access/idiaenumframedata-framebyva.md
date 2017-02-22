---
title: "IDiaEnumFrameData::frameByVA | Microsoft Docs"
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
  - "IDiaEnumFrameData::frameByVA (metodo)"
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumFrameData::frameByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Restituisce un frame indirizzo \(VA\) virtuale.  
  
## Sintassi  
  
```cpp#  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### Parametri  
 virtualAddress  
 \[in\]  Inserire il frame di interesse.  
  
 frame  
 \[out\]  restituisce [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) oggetto che rappresenta il frame contenente l'indirizzo fornito.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se nessun dati del frame corrisponde all'indirizzo specificato.  In caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)