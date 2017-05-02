---
title: "Enumerazione SCRIPTTHREADSTATE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Enumerazione SCRIPTTHREADSTATE"
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Enumerazione SCRIPTTHREADSTATE
Specifica lo stato di un thread nel motore di scripting.  Questa enumerazione è utilizzata dal metodo [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md).  
  
## Sintassi  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE\_NOTINSCRIPT|Il thread specificato attualmente non è assistendo un evento basati su script, elabora il testo immediatamente eseguito lo script, o non esegue una macro dello script.|  
|SCRIPTTHREADSTATE\_RUNNING|Il thread specificato è in assistendo un evento basati su script, elabora il testo immediatamente eseguito lo script, o esegue una macro dello script.|  
  
## Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)