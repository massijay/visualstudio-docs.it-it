---
title: "IDebugEventCallback2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2::Event"
helpviewer_keywords: 
  - "IDebugEventCallback2::Event"
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Invia una notifica degli eventi di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```c#  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### Parametri  
 `pEngine`  
 \[in\]  [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) Un oggetto che rappresenta il motore di debug \(DE\) che nell'invio questo evento.  Un DE è necessario compilare questo parametro.  
  
 `pProcess`  
 \[in\]  [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Un oggetto che rappresenta il processo in cui si verifica l'evento.  Questo parametro viene riempito dall'amministratore di debug della sessione \(SDM\).  Un DE passa sempre un valore null per questo parametro.  
  
 `pProgram`  
 \[in\]  [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Un oggetto che rappresenta il programma in cui si verifica.  Per la maggior parte degli eventi, questo parametro non è un valore null.  
  
 `pThread`  
 \[in\]  [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Un oggetto che rappresenta il thread in cui si verifica.  Per interrompere gli eventi, questo parametro non può essere un valore null mentre lo stack frame viene ottenuto dal parametro.  
  
 `pEvent`  
 \[in\]  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) un oggetto che rappresenta l'evento di debug.  
  
 `riidEvent`  
 \[in\]  GUID che identifichi interfaccia eventi per verificare dal parametro di `pEvent` .  
  
 `dwAttrib`  
 \[in\]  Una combinazione di flag [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) dall'enumerazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Nel chiamare questo metodo, il parametro di `dwAttrib` deve corrispondere al valore restituito [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) dal metodo come è stato chiamato sull'oggetto evento passato nel parametro di `pEvent` .  
  
 Tutti gli eventi di debug vengono inseriti in modo asincrono, indipendentemente dal fatto che un evento stesso è asincrono o meno.  Quando un DE chiama questo metodo, il valore restituito non indica se l'evento è stato elaborato, ma solo se l'evento è stato ricevuto.  Infatti, nella maggior parte dei casi, l'evento non è stato elaborato quando questo metodo restituisce.  
  
## Vedere anche  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)