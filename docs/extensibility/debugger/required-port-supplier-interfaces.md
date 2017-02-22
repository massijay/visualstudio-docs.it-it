---
title: "Porta richiesta fornitore interfacce | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fornitori di porte, le interfacce richieste"
  - "debug [Debugging SDK], porta fornitori"
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Porta richiesta fornitore interfacce
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

un fornitore di porte deve implementare [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) l'interfaccia.       [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Poiché buchi di alimentazioni di un fornitore di porte, è possibile distribuirli.  Pertanto, deve implementare le interfacce seguenti:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Viene descritta la porta e può enumerare tutti i processi in esecuzione sulla porta.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Consente di avviare e interrompere i processi sulla porta.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Fornisce un meccanismo per i programmi in esecuzione all'interno del contesto di questa porta per notificarlo di creazione e distruzione del nodo del programma.  Per ulteriori informazioni, vedere [Nodi di programma](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     fornisce un punto di connessione per [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## Operazione dei fornitori di porte  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) Il consumer riceve le notifiche quando il processo e i programmi vengono creati e vengono eliminati su una porta.  Una porta è obbligatoria inviare [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando un processo viene creato e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando un processo viene eliminata la porta.  Una porta è obbligatoria inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando un programma viene creato e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando un programma eliminato in un processo sulla porta.  
  
 Una porta in genere invia il programma crea ed elimina gli eventi in risposta [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) ai metodi e, rispettivamente.  
  
 Poiché una porta possibile avviare e interrompere i processi fisici che i programmi logici, queste interfacce devono essere implementate dal motore di debug:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Viene descritto il processo fisico.  Almeno i seguenti metodi devono essere distribuiti:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [Metodo GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Fornisce una soluzione per lo SDM possa connettersi e rimuovere se stesso da un processo.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Viene illustrato il programma logico.  Almeno i seguenti metodi devono essere distribuiti:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     fornisce una modalità per lo SDM all'attaccatura a questo programma.  
  
## Vedere anche  
 [Implementazione di un fornitore di porta](../../extensibility/debugger/implementing-a-port-supplier.md)