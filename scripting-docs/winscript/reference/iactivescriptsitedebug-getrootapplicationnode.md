---
title: "IActiveScriptSiteDebug::GetRootApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetRootApplicationNode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetRootApplicationNode"
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetRootApplicationNode
Ottiene il nodo dell'applicazione in cui i documenti di script da aggiungere.  
  
## Sintassi  
  
```  
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### Parametri  
 `ppdanRoot`  
 \[out\] il nodo dell'applicazione di debug che utilizza documenti di script.  Può essere `NULL`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo restituisce il nodo dell'applicazione in cui i documenti di script da aggiungere.  Il metodo può restituire `NULL` per `ppdanRoot` se i documenti di script sono di primo livello.  
  
## Vedere anche  
 [Interfaccia IActiveScriptSiteDebug Interface](../../winscript/reference/iactivescriptsitedebug-interface.md)