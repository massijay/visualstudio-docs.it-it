---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::PrepareProfilerStop"
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::PrepareProfilerStop
Notifica al profiler che si desidera interrompere la profilatura in tutti i moduli di gestione di scripting applicabili.  Utilizzando questo metodo, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] in esecuzione quando si interrompe il profilo.  
  
## Sintassi  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### Parametri  
 Il metodo non accetta parametri.  
  
## Valore restituito  
 Restituisce un HRESULT.  I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|La profilatura non può essere avviato.|  
|`S_FALSE`|La profilatura è stato arrestato quando uno script non era in esecuzione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La profilatura non è abilitato.|  
  
## Note  
 Chiamando `IActiveScriptProfilerControl2::PrepareProfilerStop` garantisce che gli eventi per le funzioni nello stack di chiamate vengono inviati.  Questo metodo deve essere chiamato prima che smettiate del profilo nel modulo di gestione di script che si trova nella scheda corrente.  Il metodo può essere chiamato dal motore di scripting.  
  
## Vedere anche  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Interfaccia IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)