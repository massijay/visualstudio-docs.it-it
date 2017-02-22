---
title: "IDebugProcess2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2"
helpviewer_keywords: 
  - "Interfaccia IDebugProcess2"
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un processo in esecuzione in una porta.  Se la porta è la porta locale, quindi `IDebugProcess2` rappresenta in genere un processo fisico nel computer locale.  
  
## Sintassi  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata da un fornitore di porte personalizzato per gestire programmi come gruppo.  Questa interfaccia deve essere implementata dal fornitore di porte.  
  
 Il modulo di debug implementa anche l'interfaccia se supporta avviare un programma [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)tramite.  
  
## Note per i chiamanti  
 Questa interfaccia è denominata principalmente dall'amministratore di debug della sessione \(SDM\) per interagire con un gruppo di programmi identificati in questo processo.  
  
 chiamata [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) o [GetProcess](../Topic/IDebugPort2::GetProcess.md) ottenere questa interfaccia.  Questa interfaccia viene restituito chiamando `IDebugEngineLaunch2::LaunchSuspended`.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugProcess2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ottiene una descrizione del processo.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera i programmi contenuti in questo processo.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ottiene il titolo, il nome descrittivo, o il nome file del processo.|  
|[Metodo GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ottiene l'istanza di un server su cui è assegnato questo processo viene eseguito.|  
|[Termina](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|termina il processo.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Connette al processo.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se lo SDM possibile rimuovere il processo.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Rimuove il debugger al processo.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ottiene l'identificatore del processo del sistema.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|ottiene un identificatore univoco globale per questo processo.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> \[DEPRECATO\]|Ottiene il nome della sessione che esegue il debug del processo.<br /><br /> \[DEPRECATO.  DOVREBBE RESTITUIRE SEMPRE `E_NOTIMPL`\].|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera i thread del processo.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Le richieste che il programma seguente che esegue codice in questa interruzione del processo.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ottiene la porta da questo processo è in esecuzione.|  
  
## Note  
 `IDebugProcess2` contiene una o [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) più interfacce.  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../Topic/IDebugPort2::GetProcess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Successivo](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)