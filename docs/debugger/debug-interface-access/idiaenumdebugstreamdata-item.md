---
title: "IDiaEnumDebugStreamData::Item | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Item (metodo)"
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera il record specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parametri  
 indice  
 \[in\]  Indice del record da recuperare.  L'indice è compreso tra 0 e `count`\-1, dove  `count` viene restituito da  [IDiaEnumDebugStreamData::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md).  
  
 cbData  
 \[in\]  Dimensione del buffer di dati, in byte.  
  
 pcbData  
 \[out\]  Restituisce il numero di byte restituiti.  se `data` viene  `NULL`, quindi  `pcbData` contiene il numero totale di byte dei dati disponibili nel record specificato.  
  
 dati \[\]  
 \[out\]  Un buffer che vengono inseriti i dati del record del flusso di debug.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Restituisce `E_INVALIDARG` per i parametri non validi e se  `index` il parametro è fuori dai limiti.  
  
## Vedere anche  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreamData::get\_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)