---
title: "IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteInterruptPoll::QueryContinue"
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteInterruptPoll::QueryContinue
Consente a un host di specificare uno script che deve terminare.  
  
## Sintassi  
  
```  
HRESULT QueryContinue();  
```  
  
#### Parametri  
 Questo metodo non accetta parametri.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|La chiamata è riuscita e l'host consente lo script di continuare l'esecuzione.|  
|`S_FALSE`|La chiamata è riuscita e l'host è necessario che lo script termina.|  
  
## Note  
 Lo script ospitato dovrebbe terminare a meno che il valore restituito del metodo `QueryContinue` sia `S_OK`.  Un valore restituito `S_FALSE` indica che le richieste host in modo esplicito che lo script termina.  
  
 Un host multithreading può utilizzare il metodo `IActiveScript::InterruptScriptThread` per terminare uno script.  
  
## Vedere anche  
 [Interfaccia IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)