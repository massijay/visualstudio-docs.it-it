---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::CompleteProfilerStart"
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica al profiler aver avviato il profilo in tutti i moduli di gestione di scripting applicabili.  Utilizzando questo metodo, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando avviare la profilatura.  
  
## Sintassi  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### Parametri  
 Il metodo non accetta parametri.  
  
## Valore restituito  
 Restituisce un HRESULT.  I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|La profilatura non può essere avviato.|  
|`S_FALSE`|La profilatura è stato avviato quando uno script non era in esecuzione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La profilatura non è abilitato.  Alcun callback è stato impostato.|  
|`E_OUTOFMEMORY`|Lo stack di chiamate non può essere ottenuto a causa di una condizione di memoria insufficiente.|  
  
## Note  
 Chiamando `IActiveScriptProfilerControl2::CompleteProfilerStart` garantisce che gli eventi per le funzioni già nello stack di chiamate vengono inviati.  Questo metodo deve essere chiamato dopo che la profilatura avviata sul motore di gestione di script che si trova nella scheda corrente.  Il metodo può essere chiamato dal motore di scripting.  
  
## Vedere anche  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Interfaccia IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)