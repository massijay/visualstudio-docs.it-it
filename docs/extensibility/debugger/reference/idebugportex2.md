---
title: "IDebugPortEx2 | Microsoft Docs"
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
  - "IDebugPortEx2"
helpviewer_keywords: 
  - "Interfaccia IDebugPortEx2"
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfacciaamministratore \(SDM\) di debug della sessione controllare i programmi e processi in esecuzione su una porta.  
  
## Sintassi  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia lo stesso oggetto che implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## Note per i chiamanti  
 Le chiamate di SDM [QueryInterface](/visual-cpp/atl/queryinterface) su `IDebugPort2` interfaccia per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugPortEx2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Viene avviato un file eseguibile.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Riprende l'esecuzione di un processo.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina se un processo può essere terminato.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|termina un processo.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ottiene l'ID processo di porta stesso.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ottiene un programma associato a un nodo di programma.|  
  
## Note  
 Questa interfaccia è in genere privata tra lo SDM e il fornitore di porte personalizzato.  
  
 Se lo si desidera, un \(DE\) motore di debug possibile trovare questa interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) sull'interfaccia passata a [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) e l'utilizzo [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) l'avvio del programma.  Questo non è un requisito, tuttavia e un DE possibile apportare eventuali necessario eseguire per l'avvio del programma di richiesta.  
  
## Requisiti  
 intestazione: portpriv.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)