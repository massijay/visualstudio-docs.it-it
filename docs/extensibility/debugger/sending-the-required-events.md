---
title: "Inviare gli eventi richiesti | Microsoft Docs"
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
  - "debug [Debugging SDK], eventi necessaria"
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Inviare gli eventi richiesti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilizzare questa procedura per inviare gli eventi di necessari.  
  
## Processo per l'invio di eventi obbligatori  
 Gli eventi seguenti sono obbligatori, in questo ordine quando si creano un motore di \(DE\) debug e allegandole a un programma:  
  
1.  Inviare un oggetto evento di [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) gestione \(SDM\) di debug della sessione quando il DE viene inizializzato per eseguire il debug di uno o più programmi di un processo.  
  
2.  Quando il programma da sottoporre a debug è associato a, inviare un oggetto evento di [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a SDM.  Questo evento può essere un evento bloccato, come la progettazione del motore.  
  
3.  Se il programma è collegato a quando il processo viene avviata, inviare un oggetto evento di [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) a SDM per notificare all'IDE di nuovo thread.  Questo evento può essere un evento bloccato, come la progettazione del motore.  
  
4.  Inviare un oggetto evento di [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM quando il programma sottoposto a debug è terminato o quando la connessione al programma viene completato.  Questo evento deve essere un evento bloccato.  
  
5.  Se l'applicazione eseguire il debug viene avviata, inviare un oggetto evento di [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) a SDM quando la prima istruzione del codice nell'architettura della fase di esecuzione sta per essere eseguita.  Questo evento è sempre un evento bloccato.  In avanzare nella sessione di debug, l'ide si arresta a questo evento.  
  
> [!NOTE]
>  Molti linguaggi utilizzano gli inizializzatori o esterno globali, funzioni precompilate \(dalla raccolta o da \_Main CRT\) all'inizio del codice.  Se la lingua del programma di cui si sta eseguendo il debug è presente uno di questi tipi di elementi prima del punto di ingresso iniziale, questo codice viene eseguito e l'evento del punto di ingresso viene inviato al punto di ingresso dell'utente, come **principale** o `WinMain`, viene raggiunto.  
  
## Vedere anche  
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)