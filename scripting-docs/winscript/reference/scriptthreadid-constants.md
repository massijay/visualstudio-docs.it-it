---
title: "Costanti SCRIPTTHREADID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADID"
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Costanti SCRIPTTHREADID
Utilizzata per specificare il tipo di thread.  
  
## Sintassi  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## Costanti  
  
|Costante|Valore|Significato|  
|--------------|------------|-----------------|  
|SCRIPTTHREADID\_CURRENT|0xFFFFFFFD|Il thread attualmente in esecuzione.|  
|SCRIPTTHREADID\_BASE|0xFFFFFFFE|Il thread di base; ovvero il thread in cui il motore di scripting è stata creata un'istanza.|  
|SCRIPTTHREADID\_ALL|0xFFFFFFFF|Tutti i thread.|  
  
## Note  
 Il tipo `SCRIPTTHREADID` viene utilizzato da `IActiveScript::GetCurrentScriptThreadID`, da `IActiveScript::GetScriptThreadID`, da `IActiveScript::GetScriptThreadState`e da `IActiveScript::InterruptScriptThread`, ma le costanti possono essere utilizzate solo da `IActiveScript::GetScriptThreadState` e da `IActiveScript::InterruptScriptThread`.  
  
## Vedere anche  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)