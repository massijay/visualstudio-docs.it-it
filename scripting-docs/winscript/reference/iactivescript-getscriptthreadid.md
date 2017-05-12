---
title: "IActiveScript::GetScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadID"
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadID
Recupera un identificatore scripting\-motore\- definito per il thread associato al thread specificato Win32.  
  
## Sintassi  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### Parametri  
 `dwWin32ThreadID` ,  
 \[in\] identificatore di thread di un thread di esecuzione Win32 nel processo corrente.  Utilizzare la funzione [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) per recuperare identificatore del thread attualmente in esecuzione.  
  
 `pstidThread` ,  
 \[out\] indirizzo di una variabile che riceve identificatore del thread di script associato al thread specificato Win32.  L'interpretazione di questo identificatore viene lasciato al motore di scripting, ma può essere una sola copia dell'identificatore di thread di windows.  Si noti che se il thread Win32 termina, questo identificatore è e successivamente può essere assegnato a un altro thread.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\) e pertanto non è stata avuto esito negativo.|  
  
## Note  
 L'identificatore recuperato per le successive chiamate ai metodi di controllo di esecuzione thread di script come metodo [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md).  
  
 Questo metodo può essere chiamato dai thread non di base senza con conseguente callout di non base agli oggetti host o a un'interfaccia [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md).  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)