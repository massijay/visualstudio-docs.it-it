---
title: "IActiveScript::GetScriptThreadState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadState"
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadState
Recupera lo stato corrente di un thread dello script.  
  
## Sintassi  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### Parametri  
 `stidThread`  
 \[in\] identificatore del thread per il quale lo stato viene richiesto, o uno degli identificatori speciali dei thread:  
  
|Valore|Significato|  
|------------|-----------------|  
|SCRIPTTHREADID\_BASE|Il thread di base; ovvero il thread in cui il motore di scripting è stata creata un'istanza.|  
|SCRIPTTHREADID\_CURRENT|Il thread attualmente in esecuzione.|  
  
 `pstsState`  
 \[out\] indirizzo di una variabile che riceve lo stato del thread desiderato.  Lo stato viene visualizzato da uno dei valori costanti denominati definiti dall'enumerazione [Enumerazione SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md).  Se questo parametro non identifica il thread corrente, lo stato può cambiare in qualsiasi momento.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\).|  
  
## Note  
 Questo metodo può essere chiamato dai thread non di base senza con conseguente callout di non base agli oggetti host o a un'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)