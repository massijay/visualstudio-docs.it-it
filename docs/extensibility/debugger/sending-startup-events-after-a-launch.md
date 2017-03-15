---
title: "L&#39;invio di eventi di avvio dopo il lancio di un | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], eventi di avvio"
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# L&#39;invio di eventi di avvio dopo il lancio di un
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Una volta che il \(DE\) motore di debug è connesso al programma, invia una serie di eventi di avvio della sessione di debug.  
  
 Gli eventi di avvio inviati alla sessione di debug sono inclusi i seguenti:  
  
-   Un evento di creazione del motore.  
  
-   Un evento di creazione del programma.  
  
-   Eventi di caricamento di creazione e del modulo del thread.  
  
-   Un evento completo di caricamento, inviato quando il codice viene caricato ed è pronto per l'esecuzione, ma prima che il codice venga eseguito  
  
    > [!NOTE]
    >  Quando questo evento ha proseguito fino, le variabili globali vengono inizializzate e l'esecuzione della routine di avvio.  
  
-   Altri possibili eventi di caricamento di creazione e del modulo del thread.  
  
-   Un evento di punto di ingresso, che segnala che il programma ha raggiunto il punto di ingresso principale, come **principale** o `WinMain`.  Questo evento viene in genere non viene inviato se si connette di DE a un programma già in esecuzione.  
  
 A livello di codice, il DE innanzitutto invia l'amministratore \(SDM\) di debug della sessione un'interfaccia di [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , che rappresenta un evento di creazione del motore, è seguito da [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), che rappresenta un evento di creazione del programma.  
  
 In genere ciò è seguita da uno o più eventi di caricamento di eventi di creazione di thread di [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) e il modulo di [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .  
  
 Quando il codice viene caricato ed è pronto per l'esecuzione, ma prima che il codice venga eseguito, il DE invia lo SDM un evento completo del caricamento di [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) .  Infine, se il programma non è in esecuzione, il DE invia un evento di punto di ingresso di [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , segnalazione che il programma ha raggiunto il punto di ingresso principale ed è pronto per il debug.  
  
## Vedere anche  
 [Controllo di esecuzione](../../extensibility/debugger/control-of-execution.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)