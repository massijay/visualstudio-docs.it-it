---
title: "IDebugApplication::HandleRuntimeError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleRuntimeError"
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleRuntimeError
Determina il thread corrente di bloccare e invia una notifica di errore all'IDE del debugger.  
  
## Sintassi  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### Parametri  
 `pErrorDebug`  
 \[in\] l'errore che si è verificato.  
  
 `pScriptSite`  
 \[in\] il sito script del thread.  
  
 `pbra`  
 \[out\] azione da eseguire quando il debugger riattiva l'applicazione.  
  
 `perra`  
 \[out\] azione da eseguire quando il debugger riattiva l'applicazione in caso di errore.  
  
 `pfCallOnScriptError`  
 \[out\] contrassegni che è `TRUE` se il motore chiama il metodo `IActiveScriptSite::OnScriptError`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Un motore di linguaggio chiama questo metodo nel contesto di un thread che causa un errore di runtime.  Questo metodo fa nel thread corrente di bloccare e invia una notifica di errore da inviare all'IDE del debugger.  Quando l'ide del debugger riattiva l'applicazione, questo metodo restituisce con l'azione da intraprendere.  
  
> [!NOTE]
>  Mentre nell'errore in fase di esecuzione, il motore di linguaggio può essere chiamato dal thread per eseguire tali attività come enumera stack frame oppure valutare le espressioni.  
  
## Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Enumerazione ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)