---
title: "IDebugEngineLaunch2 | Microsoft Docs"
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
  - "IDebugEngineLaunch2"
helpviewer_keywords: 
  - "Interfaccia IDebugEngineLaunch2"
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Utilizzato dal motore \(DE\) di debug per avviare e interrompere i programmi.  
  
## Sintassi  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## Note per gli implementatori  
 Questa interfaccia viene implementata da un oggetto personalizzato DE se vi sono requisiti particolari per avviare un processo che non può essere gestito interamente da una porta personalizzata.  Questa operazione è in genere il caso in cui il DE fa parte di un interprete e il processo sottoposto a debug è uno script: l'interprete deve essere avviato in primo luogo quindi lo script viene caricato e avviato.  Una porta possibile avviare l'interprete, ma lo script può richiedere una gestione speciale \(ovvero la posizione in cui il DE dispone di un ruolo\).  Questa interfaccia è implementata solo se esistono requisiti univoci per avviare un programma che una porta personalizzata non può gestire.  
  
## Note per i chiamanti  
 Questa interfaccia viene chiamata dall'amministratore di debug della sessione \(SDM\) se lo SDM possibile ottenere questa interfaccia [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) ISAPI \(utilizzando QueryInterface\).  Se tale interfaccia può essere ottenuta, lo SDM sa che il DE vi sono requisiti particolari e chiama questa interfaccia per l'avvio del programma anziché avere l'avvio della porta.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugEngineLaunch2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Viene avviato un processo l'utilizzo di DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Riprende elaborano l'esecuzione.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina se un processo può essere terminato.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|termina un processo.|  
  
## Requisiti  
 intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)