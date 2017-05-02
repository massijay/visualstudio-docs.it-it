---
title: "IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SynchronousCallInDebuggerThread"
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SynchronousCallInDebuggerThread
Fornisce un meccanismo per il chiamante al codice di esecuzione nel thread del debugger.  
  
## Sintassi  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### Parametri  
 `pptc`  
 \[in\] l'oggetto alla chiamata.  
  
 `dwParam1`  
 \[in\] primo parametro per passare a `IDebugThreadCall::ThreadCallHandler` il metodo.  
  
 `dwParam2`  
 \[in\] secondo parametro per passare a `IDebugThreadCall::ThreadCallHandler` il metodo.  
  
 `dwParam3`  
 \[in\] terzo parametro per passare a `IDebugThreadCall::ThreadCallHandler` il metodo.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 I motori del linguaggio e gli host utilizzano generalmente questo metodo per implementare oggetti a thread libero sulle semplici implementazioni multithread.  
  
## Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)