---
title: "IDebugProcessEx2 | Microsoft Docs"
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
  - "IDebugProcessEx2"
helpviewer_keywords: 
  - "Interfaccia IDebugProcessEx2"
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfacciaamministratore \(SDM\) di debug della sessione notificare a un processo in fase di connessione o viene svuotato dal processo.  
  
## Sintassi  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia lo stesso oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) dell'interfaccia per:  
  
-   Supportare la verifica delle sessioni connesse a un processo  
  
-   Auto\-attaccatura di supporto tramite i motori di debug più  
  
 Il fornitore di porte personalizzato può implementare questa interfaccia se scegliere.  
  
## Note per i chiamanti  
  
-   Le chiamate di SDM [QueryInterface](/visual-cpp/atl/queryinterface) su `IDebugProcess2` interfaccia per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugProcessEx2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Notifica al processo di una sessione ora esegue il debug del processo.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Notifica al processo di una sessione si esegue il debug del processo.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Aggiunge i nodi di programma per un elenco dei motori di debug.|  
  
## Note  
 Questa interfaccia è privata tra lo SDM e il processo.  
  
## Requisiti  
 intestazione: Portpriv.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)