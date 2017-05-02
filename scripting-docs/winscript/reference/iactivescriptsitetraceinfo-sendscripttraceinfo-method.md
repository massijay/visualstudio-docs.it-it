---
title: "Metodo IActiveScriptSiteTraceInfo::SendScriptTraceInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo IActiveScriptSiteTraceInfo::SendScriptTraceInfo
Invia le informazioni di traccia che includono il tipo di evento, il contesto e l'istruzione dello script.  
  
## Sintassi  
  
```  
HRESULT SendScriptTraceInfo(   
    [in] SCRIPTTRACEINFO stiEventType,   
    [in] GUID guidContextID,   
    [in] DWORD dwScriptContextCookie,   
    [in] LONG lScriptStatementStart,   
    [in] LONG lScriptStatementEnd,   
    [in] DWORD64 dwReserved   
);   
```  
  
#### Parametri  
 `stiEventType`  
 Il tipo di evento.  
  
 `guidContextId`  
 Il GUID del contesto.  
  
 `dwScriptContextCookie`  
 I cookie del contesto.  
  
 `lScriptStatementStart`  
 La posizione dell'inizio dell'istruzione di script.  
  
 `lScriptStatementEnd`  
 La posizione della fine dell'istruzione di script.  
  
 `dwReserved`  
 Riservato.