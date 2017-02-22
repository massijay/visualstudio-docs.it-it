---
title: "Tipi di evento supportati | Microsoft Docs"
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
  - "debug [Debugging SDK], supportato eventi"
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Tipi di evento supportati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio che esegue il debug attualmente sono supportati i seguenti tipi di evento:  
  
-   eventi asincroni  
  
     Informare l'amministratore \(SDM\) di debug della sessione e l'ide che lo stato dell'applicazione sottoposta a debug viene modificato.  Questi eventi vengono elaborati allo svago di SDM e dell'IDE.  Non viene ricevuta alcuna risposta inviata al \(DE\) motore di debug una volta che viene elaborato.  [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) Le interfacce e [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) sono esempi di eventi asincroni.  
  
-   eventi sincroni  
  
     Informare lo SDM e l'ide che lo stato dell'applicazione sottoposta a debug viene modificato.  L'unica differenza tra questi eventi e gli eventi asincroni è che la risposta inviata tramite il metodo [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) .  
  
     Inviare un evento sincrono è utile se è necessario un DE di continuare a sviluppare dopo l'ide si riceve ed elabora l'evento.  
  
-   Eventi sincroni, arrestare o interrompere gli eventi  
  
     Informare lo SDM e l'ide che l'applicazione di cui si esegue il debug della chiusura del codice.  Quando si invia un evento bloccato utilizzando il metodo [Evento](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) il parametro è obbligatoria.  Arrestando gli eventi sono ha proseguito fino da una chiamata a quella dei metodi seguenti:  
  
    -   [Esegui](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Passaggio](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continua](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Le interfacce [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di eventi di arresto.  
  
    > [!NOTE]
    >  gli eventi arrestare asincroni non sono supportati.  È un errore per inviare un evento bloccato asincrono.  
  
## Descrizione  
 Dell'implementazione effettiva degli eventi dipende dalla progettazione di DE.  Il tipo di ogni evento inviato è determinato dai relativi attributi, che vengono impostati quando si progetta il DE.  Ad esempio, un DE possibile inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) come evento asincrono, mentre un altro può inviarlo come evento bloccato.  
  
 Nella tabella seguente vengono specificati che programmano e parametri del thread al quale eventi di necessari nonché tipi di evento.  Qualsiasi evento può essere sincrono.  nessun evento deve essere sincrono.  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) l'interfaccia è obbligatoria per tutti gli eventi.  
  
|Evento|IDebugProgram2|IDebugThread2|Arrestare gli eventi|  
|------------|--------------------|-------------------|--------------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obbligatorio|Obbligatorio|Sì|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obbligatorio|Obbligatorio|Sì|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obbligatorio|Obbligatorio|No|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Non consentito|Non consentito|No|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Non consentito|Non consentito|No|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obbligatorio|Obbligatorio|Sì|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|può essere|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obbligatorio|Obbligatorio|Sì|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|può essere|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obbligatorio|Obbligatorio|Sì|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obbligatorio|Obbligatorio|Sì|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|può essere|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|No|  
|IDebugStopCompleteEvent2|Obbligatorio|Obbligatorio|Sì|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obbligatorio|Obbligatorio|Sì|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|No|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obbligatorio|Obbligatorio|No|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obbligatorio|Obbligatorio|No|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|concedere, ma non obbligatorio|concedere, ma non obbligatorio|No|  
  
## Vedere anche  
 [L'invio di eventi](../../extensibility/debugger/sending-events.md)