---
title: "IActiveScript::GetCurrentScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetCurrentScriptThreadID"
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetCurrentScriptThreadID
Recupera un identificatore scripting\-motore\- definito per il thread attualmente in esecuzione.  L'identificatore può essere utilizzato nelle successive chiamate ai metodi di esecuzione\- controllo del thread di script come metodo [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md).  
  
## Sintassi  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### Parametri  
 `pstidThread`  
 \[out\] l'indirizzo di una variabile che riceve identificatore del thread script è associato al thread corrente.  L'interpretazione di questo identificatore viene lasciato al motore di scripting, ma può essere una sola copia dell'identificatore di thread di windows.  Se il thread Win32 termina, questo identificatore è e successivamente può essere assegnato a un altro thread.  
  
## Valore restituito  
 Restituisce `S_OK` se l'operazione riesce, o `E_POINTER` se un puntatore non valido è stato specificato.  
  
## Note  
 Questo metodo può essere chiamato dai thread non di base senza con conseguente callout di non base agli oggetti host o a un'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)