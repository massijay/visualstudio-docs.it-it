---
title: "IActiveScriptSite::OnEnterScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnEnterScript"
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnEnterScript
All'host che il motore di scripting ha avviato il codice di script.  
  
## Sintassi  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## Valore restituito  
 Se ha esito positivo restituisce `S_OK`.  
  
## Note  
 Il motore di scripting deve chiamare questo metodo in ogni voce o rientro nel motore di scripting.  Ad esempio, se lo script chiama un oggetto che viene generato un evento gestito nel motore di scripting, il motore di scripting deve chiamare `IActiveScriptSite::OnEnterScript` prima di eseguire l'evento e deve chiamare il metodo [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) dopo aver eseguito l'evento ma prima di restituire l'oggetto che ha generato l'evento.  Le chiamate al metodo possono essere annidate.  Ogni chiamata a questo metodo richiede una chiamata corrispondente a `IActiveScriptSite::OnLeaveScript`.  
  
## Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)