---
title: "IActiveScriptSite::OnScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptError"
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptError
All'host che un errore di esecuzione si verifica quando il motore l'esecuzione dello script.  
  
## Sintassi  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### Parametri  
 `pase`  
 \[in\] indirizzo dell'interfaccia [IActiveScriptError](../../winscript/reference/iactivescripterror.md) dell'oggetto errore.  Un host può utilizzare questa interfaccia per ottenere informazioni sull'errore di esecuzione.  
  
## Valore restituito  
 Restituisce `S_OK` se l'errore è stato gestito correttamente, o un OLE definita nel codice di errore.  
  
## Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)