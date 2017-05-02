---
title: "Metodo IActiveScriptProfilerCallback3::SetWebWorkerId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo IActiveScriptProfilerCallback3::SetWebWorkerId
Notifica al profiler sui thread di lavoro ID da utilizzare per questa sessione di profilo.  Se la funzione non viene eseguito nel contesto della pagina, questo metodo non viene chiamato.  Il valore degli incrementi `webWorkerId` da 1 per ogni thread di lavoro, inizio a 1.  I valori ID non vengono considerati stabili oltre una sessione e corrispondono all'ordine in cui i lavoratori sono stati creati.  
  
## Sintassi  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
  
```  
  
#### Parametri  
 `webWorkerId`  
 L'id Web di lavoro  
  
## Valore restituito  
 Il valore restituito del metodo viene ignorato dal motore di scripting.