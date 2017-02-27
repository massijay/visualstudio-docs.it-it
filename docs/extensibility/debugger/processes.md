---
title: "Processi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK], processi"
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Processi
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In termini di architettura del debugger, **un processo**:  
  
-   è un contenitore per un set di programmi.  È strettamente analogo a un processo di windows, che è un contenitore per un set di thread.  
  
-   Può identificarsi per nome, l'identificatore, l'identificatore o fisico.  
  
-   È possibile enumerare tutti i programmi in esecuzione \(e i relativi thread\).  
  
-   Può autodescriversi, la porta che è in esecuzione e il computer che la contiene.  
  
-   Può creare uno o più programmi, terminare qualsiasi programma che crea, o provocano un programma a arrestata.  
  
-   È [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) rappresentato da un'interfaccia, creata quando il processo viene avviato.  Avvio di un processo da qualsiasi l'amministratore \(SDM\) di debug della sessione o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Il pacchetto di debug possibile allegare un modulo di \(DE\) debug a un processo chiamando [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md).  Ciò significa che si connette di DE a tutti i programmi possibili in esecuzione nel processo che può gestire.  Ad esempio, se si connette di DE di Common Language Runtime in un processo, viene aggiunta solo ai programmi che eseguono codice gestito.  
  
## Vedere anche  
 [Programs](../../extensibility/debugger/programs.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Eseguire il debug del pacchetto](../../extensibility/debugger/debug-package.md)   
 [Il motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)