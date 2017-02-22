---
title: "IDebugPortEvents2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2::Event"
helpviewer_keywords: 
  - "IDebugPortEvents2::Event"
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo invia eventi che consentono la creazione e l'eliminazione dei processi e dei programmi su una porta.  
  
## Sintassi  
  
```cpp#  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```c#  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### Parametri  
 `pMachine`  
 \[in\]  [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Un oggetto che rappresenta il server di debug \(esiste uno per ogni istanza di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]\) in cui si verificato l'evento.  
  
 `pPort`  
 \[in\]  [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Un oggetto che rappresenta la porta in cui si verificato l'evento.  
  
 `pProcess`  
 \[in\]  [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Un oggetto che rappresenta il processo in cui si verificato l'evento.  
  
 `pProgram`  
 \[in\]  [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Un oggetto che rappresenta il programma in cui si verificato l'evento.  
  
 `pEvent`  
 \[in\]  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) un oggetto che identifica l'evento.  Gli eventi possibili sono:  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 \[in\]  Il GUID dell'evento.  Poiché l'evento viene eseguito il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) cast prima di chiamare questo metodo, questo identificatore rende più facile determinare quale evento nell'invio.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)