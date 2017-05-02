---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug"
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
All'host su un errore di runtime script quando l'amministratore del processo di debug non trova un debugger Just\-in\-time\- dello script.  
  
 Per implementare un debugger nell'host, è necessario gestire [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md).  Sulla base di un'azione utente, l'host può o connettere il debugger e restituiscono, o restituire avviare il debugger nel parametro di OnScriptErrorDebug `pfEnterDebugger`.  È inoltre necessario implementare questa interfaccia per ottenere la notifica sull'errore di runtime anche se non esistono debugger esterni che possono essere interpretati dall'amministratore del processo di debug.  
  
## Sintassi  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Parametri  
 `pErrorDebug`  
 \[in\] l'errore di runtime che si è verificato.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 \[out\] se chiamare [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) se l'utente decide di continuare senza debug.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 È inoltre necessario implementare questa interfaccia per ottenere una notifica.  
  
## Vedere anche  
 [Interfaccia IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)