---
title: "IActiveScriptSite::OnScriptTerminate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptTerminate"
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptTerminate
All'host che lo script termina l'esecuzione.  
  
## Sintassi  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### Parametri  
 `pvarResult`  
 \[in\] indirizzo di una variabile contenente il risultato dello script, o `NULL` se lo script non fornite da risultato.  
  
 `pexcepinfo`  
 \[in\] indirizzo di una struttura `EXCEPINFO` contenente le informazioni sull'eccezione ha generato quando lo script termina, o `NULL` se non è stata generata un'eccezione.  
  
## Valore restituito  
 Se ha esito positivo restituisce `S_OK`.  
  
## Note  
 Il motore di scripting chiama questo metodo prima della chiamata al metodo [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md), con il flag di SCRIPTSTATE\_INITIALIZED, sia completata.  Questo metodo può essere utilizzato per ripristinare lo stato di completamento e i risultati all'host.  Notare che molti linguaggi di script, basati sugli eventi di affondamento dall'host, con durate definite dall'host.  In questo caso, questo metodo non può mai essere chiamato.  
  
## Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)