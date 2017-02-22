---
title: "IDiaEnumDebugStreamData::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Next (metodo)"
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un numero specificato di record nella sequenza enumerata.  
  
## Sintassi  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### Parametri  
 celta  
 \[in\]  il numero di record da recuperare.  
  
 cbData  
 \[in\]  Dimensione del buffer di dati, in byte.  
  
 pcbData  
 \[out\]  Restituisce il numero di byte restituiti.  se `data` è NULL, quindi  `pcbData` contiene il numero totale di byte dei dati disponibili per tutti i record necessari.  
  
 dati \[\]  
 \[out\]  Un buffer che sia compilato con dati del record del flusso di debug.  
  
 pceltFetched  
 \[in, out\]  Restituisce il numero di record in `data`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se non sono presenti più record.  In caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)