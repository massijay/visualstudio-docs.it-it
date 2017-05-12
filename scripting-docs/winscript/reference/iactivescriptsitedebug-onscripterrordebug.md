---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::OnScriptErrorDebug"
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::OnScriptErrorDebug
Consente a uno SmartHost determinare come gestire gli errori di runtime.  
  
## Sintassi  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Parametri  
 `pErrorDebug`  
 \[in\] l'errore di runtime che si è verificato  
  
 `pfEnterDebugger`  
 \[out\] contrassegni indica se l'errore passare al debugger di eseguire il debug JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 \[out\] contrassegni indica se chiamare `IActiveScriptSite::OnScriptError` quando l'utente decide di continuare senza debug.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati al valore nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Uno SmartHost possibile utilizzare questo metodo per determinare come gestire gli errori di runtime.  
  
## Vedere anche  
 [Interfaccia IActiveScriptSiteDebug Interface](../../winscript/reference/iactivescriptsitedebug-interface.md)