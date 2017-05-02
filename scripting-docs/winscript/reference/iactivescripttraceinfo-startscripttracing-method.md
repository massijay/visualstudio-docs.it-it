---
title: "Metodo IActiveScriptTraceInfo::StartScriptTracing | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo IActiveScriptTraceInfo::StartScriptTracing
Avviare l'analisi dello script.  
  
## Sintassi  
  
```  
HRESULT StartScriptTracing(   
    [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,   
    [in] GUID guidContextID   
);  
  
```  
  
#### Parametri  
 `pSiteTraceInfo`  
 Un puntatore a IActiveScriptSiteTraceInfo dell'host.  
  
 `guidContextId`  
 Il GUID del contesto.  
  
## Valore restituito  
 Restituire valori possibili di questo metodo sono i seguenti:  
  
1.  S\_OK: Riuscita.  
  
2.  E\_POINTER: `pSiteTraceInfo` è un puntatore null.  
  
3.  E\_NOTIMPL: non implementato.