---
title: "IActiveScriptSite::OnLeaveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnLeaveScript"
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnLeaveScript
All'host che il motore di scripting ha restituito dal codice di script.  
  
## Sintassi  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## Valore restituito  
 Se ha esito positivo restituisce `S_OK`.  
  
## Note  
 Il motore di scripting deve chiamare questo metodo prima di restituire il controllo a un'applicazione chiamante entrato nel motore di scripting.  Ad esempio, se lo script chiama un oggetto che viene generato un evento gestito nel motore di scripting, il motore di scripting deve chiamare il metodo [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) prima di eseguire l'evento e deve chiamare `IActiveScriptSite::OnLeaveScript` dopo aver eseguito l'evento prima di restituire l'oggetto che ha generato l'evento.  Le chiamate al metodo possono essere annidate.  Ogni chiamata a `IActiveScriptSite::OnEnterScript` richiede una corrispondente chiamata a questo metodo.  
  
## Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)