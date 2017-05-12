---
title: "IDebugApplication::HandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleBreakPoint"
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleBreakPoint
Determina il thread corrente di bloccare e invia una notifica del punto di interruzione all'IDE del debugger.  
  
## Sintassi  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### Parametri  
 `br`  
 \[in\] il motivo dell'interruzione.  
  
 `pbra`  
 \[out\] azione da eseguire quando il debugger riattiva l'applicazione.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Un motore di linguaggio chiama questo metodo nel contesto di un thread che viene rilevato un punto di interruzione.  Questo metodo blocca il thread corrente e invia una notifica del punto di interruzione all'IDE del debugger.  Quando il debugger riattiva l'applicazione, il parametro `pbra` specifica che azione da eseguire.  
  
> [!NOTE]
>  Il motore di linguaggio può essere chiamato dal thread per eseguire attività quali enumera gli stack frame oppure valutare le espressioni durante il punto di interruzione.  
  
 Questo metodo fa `IApplicationDebugger::onHandleBreakPoint` venga chiamato.  
  
## Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)