---
title: "Interfacce di base | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK], interfacce di base"
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfacce di base
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Le interfacce seguenti sono le interfacce principali per il debugger l'estensione utilizzando [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## Descrizione  
 Queste interfacce sono utilizzate principalmente per creare il motore di \(DE\) debug.  Sono organizzati in base alle categorie:  
  
-   [Punti di interruzione](#Breakpoints)  
  
-   [contesti](#Contexts)  
  
-   [server principale](#CoreServer)  
  
-   [I motori di debug](#DebugEngines)  
  
-   [Documenti](#Documents)  
  
-   [Eventi](#Events)  
  
-   [espressioni](#Expressions)  
  
-   [Memoria](#Memory)  
  
-   [Moduli](#Modules)  
  
-   [porte](#Ports)  
  
-   [Processi](#Processes)  
  
-   [Programmi](#Programs)  
  
-   [Proprietà](#Properties)  
  
-   [Stack frame](#StackFrames)  
  
-   [Thread](#Threads)  
  
-   [Visualizzatori di tipi](#TypeVisualizers)  
  
 Le entità che possono implementare interfacce sono:  
  
-   motore di debug \(DE\)  
  
-   fornitore di porte \(PS\)  
  
-   analizzatore di espressioni \(EE\)  
  
-   Visual Studio \(VS\)  
  
##  <a name="Breakpoints"></a> Punti di interruzione  
 Queste interfacce sono correlate all'implementazione e la verifica dei punti di interruzione.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Rappresenta un punto di interruzione associati a una posizione di memoria.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Inviato da DE quando un punto di interruzione verrà associato a una posizione di memoria.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Rappresenta un checksum del documento per una richiesta del punto di interruzione.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Inviato da DE quando un punto di interruzione non riesce a essere associato a una posizione di memoria.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Inviato da DE quando viene raggiunto un punto di interruzione.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|rappresenta una richiesta di punto di interruzione; utilizzata nella creazione di un punto di interruzione in attesa.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|rappresenta una richiesta di punto di interruzione; utilizzata nella creazione di un punto di interruzione in attesa.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Rappresenta le informazioni utilizzate per associare un punto di interruzione.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Inviato da DE quando un punto di interruzione è separato da una posizione di memoria.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|rappresenta un punto di interruzione non valido \(restituito da `IDebugBreakpointErrorEvent2`\).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Rappresenta le informazioni di risoluzione su un punto di interruzione non valido.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Rappresenta un percorso in una funzione in cui viene impostato un punto di interruzione.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Rappresenta un punto di interruzione che deve essere associato, utilizzata nella creazione di un punto di interruzione associato.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Rappresenta un'enumerazione su un set di punti di interruzione associati.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Rappresenta un'enumerazione su un set di punti di interruzione che potrebbero non essere associati a una posizione di memoria.|  
  
##  <a name="Contexts"></a> contesti  
 Queste interfacce rappresentano i vari tipi di contesti nel programma sottoposto a debug.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|rappresenta la posizione iniziale di un'istruzione di codice.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Estende [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) l'interfaccia per consentire il recupero del modulo e interfacce gestite.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|rappresenta una posizione in un documento.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|rappresenta il contesto in cui valutare un'espressione.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Rappresenta la posizione iniziale in memoria di una raccolta di byte.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Rappresenta un contesto dello stack frame a un punto di interruzione o a un'eccezione.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Rappresenta un contesto dello stack frame a un punto di interruzione o a un'eccezione.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Rappresenta un'enumerazione su un set di contesti di codice.|  
  
##  <a name="CoreServer"></a> server principale  
 Queste interfacce rappresentano il computer in cui un programma sta eseguendo il debug.  Questi sono implementati da [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ma possono essere chiamati nei motori di debug.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Fornisce l'accesso alle porte e i fornitori di porte nonché informazioni sul computer.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Rappresenta [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) un oggetto debug remoto di supportare.|  
  
##  <a name="DebugEngines"></a> I motori di debug  
 Queste interfacce rappresentano i motori di debug e i relativi eventi associati.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|rappresenta un motore di debug personalizzato.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Rappresenta un motore di debug personalizzato che supporta il caricamento dei simboli, di JustMyCode e delle eccezioni.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Inviato da ogni nuova istanza di DE per indicare è pronto per gestire le attività di debug.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Rappresenta un motore di debug personalizzato che supporta che iniziano i programmi.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|rappresenta un nodo di programma che gestisce i motori di debug più.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Fornisce una soluzione per lo SDM di ottenere un'interfaccia al motore di debug da un thread, da un programma, uno stack frame.|  
  
##  <a name="Documents"></a> Documenti  
 Queste interfacce rappresentano i documenti \(file di origine\) e i relativi elementi associati.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Inviato da DE per richiedere un documento per essere aperte.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Rappresenta un flusso delle istruzioni smontate da un documento.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Rappresenta un documento fornito da DE, specificando un nome e una classe PerID \(CLSID\).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Rappresenta un checksum per un documento di debug e di passare il checksum tra i componenti.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Rappresenta un contesto del documento, a una posizione in un documento che corrisponde a un particolare istruzione e il contesto di codice.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Rappresenta una posizione generale all'interno di un documento.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Rappresenta una posizione in un file di origine come offset del carattere.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Rappresenta un documento di testo fornito da DE \(derivata da [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\), fornendo il testo effettivo.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Inviato da DE per specificare le modifiche in un file di origine presente in memoria.|  
  
##  <a name="Events"></a> Eventi  
 Queste interfacce rappresentano tutti gli eventi inviati tra il DE e l'amministratore \(SDM\) di debug della sessione.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Inviato da DE per richiedere un documento per essere aperte.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Il motore \(DE\) di debug invia questa interfaccia gestione \(SDM\) di debug della sessione per impostare il messaggio della barra di stato durante il caricamento dei simboli.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Inviato da DE quando un per interrompere il programma è stato completato.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Inviato da DE quando un punto di interruzione verrà associato.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Inviato da DE quando un punto di interruzione non riesce a essere associato.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Inviato da DE quando viene raggiunto un punto di interruzione.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Inviato da DE quando un punto di interruzione viene separato.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Inviato da DE per determinare se deve essere interrotta in una determinata posizione.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Inviato da DE per specificare le modifiche in un file di origine presente in memoria.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Inviato da ogni nuova istanza di DE per indicare è pronto per gestire le attività di debug.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Inviato da DE per indicare il programma sottoposto a debug è pronta per eseguire la prima istruzione.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Interfaccia utilizzata da altre interfacce eventi, che potrebbe restituire un errore, fornire messaggi di errore leggibili.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE, PS|interfaccia di base da cui tutte le altre interfacce eventi sono derivate.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Rappresenta un'interfaccia implementata da SDM a cui gli eventi \(espressi come oggetti che implementano un'interfaccia eventi particolare\) vengono inviati.|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Inviato da DE quando un'eccezione si è verificata nel programma sottoposto a debug.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Inviato da DE quando una valutazione asincrona di espressione è completa.|  
|IDebugFindSymbolEvent2||OBSOLETO.  NOT UTILIZZARE.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Inviato da DE quando l'elaborazione per un'eccezione intercettata è stato completato.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Inviato da DE quando un programma ha completato il caricamento.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Inviato da DE per avere la visualizzazione dell'IDE un messaggio informativo all'utente.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Inviato da DE quando un modulo viene caricato o scaricato.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Segnala l'interfaccia utente del debugger di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] per avvertire l'utente che i simboli non potrebbero trovarsi nell'eseguibile avviato.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Inviato da DE per avere la visualizzazione dell'IDE una stringa arbitraria.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, DE|Inviato da una porta per comunicare gli eventi di porta a ogni listener.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Inviato da DE o dalla porta quando un processo è stato creato.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Inviato da DE o dalla porta quando un processo è stato eliminato.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Inviato da DE o dalla porta quando un programma è stato creato.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Inviato da DE o dalla porta quando un programma è stato eliminato.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Consente a un modulo di debug per eseguire l'override del comportamento predefinito dell' interfaccia utente di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]al termine di una sessione di debug.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Inviato dal motore \(DE\) di debug gestione \(SDM\) di debug della sessione quando il nome di un programma.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Inviato da DE quando una nuova proprietà \(rappresentato dall'interfaccia di `IDebugProperty2` \) è stata creata.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Inviato da DE quando una proprietà è stata eliminata.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Inviato da DE quando avanzare da o su una funzione in modo che il valore restituito è in grado di visualizzare.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Consente ai motori di debug per leggere le impostazioni metrica in modalità remota.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Inviato da DE quando un passaggio in, in, o da un'istruzione è stato completato.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Inviato da DE per indicare l'esito positivo o negativo di caricamento dei simboli per un modulo.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Inviato da DE quando è stato creato un thread.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Inviato da DE quando un thread è stato eliminato.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Inviato da DE quando un thread ha modificato il nome.|  
  
##  <a name="Expressions"></a> espressioni  
 Queste interfacce rappresentano le espressioni da valutare in un contesto specifico.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|rappresenta un'espressione da valutare.  Verificato [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) dall'interfaccia.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Rappresenta un contesto in cui un'espressione viene valutata.  Verificato [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) dall'interfaccia.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Inviato da DE quando una valutazione asincrona di espressione è completa.|  
  
##  <a name="Memory"></a> Memoria  
 Queste interfacce rappresentano sequenze di byte in memoria.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Rappresenta una sequenza di byte in memoria che può essere letto o essere scritto su.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|rappresenta una posizione in memoria di una sequenza di byte.|  
  
##  <a name="Modules"></a> Moduli  
 Queste interfacce rappresentano un modulo, che corrisponde a un eseguibile o al file DLL.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Rappresenta un singolo file eseguibile o DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Rappresenta [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) un oggetto simboli di supportare.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Inviato da DE quando un modulo viene caricato o scaricato.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Rappresenta le informazioni del server di origine contenute in un file PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Rappresenta un'enumerazione su un set di moduli ritenuti da [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a> porte  
 Queste interfacce rappresentano le porte e i fornitori di porte.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|Rappresenta la porta predefinita nel computer locale.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Abilita il modulo di debug che utilizza DCOM per chiedere all'interfaccia utente di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] per assicurarsi che il firewall non bloccare il debug remoto.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|rappresenta una porta.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Inviato da una porta per comunicare gli eventi di porta a ogni listener.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Rappresenta una porta che consente di avviare e interrompere i processi.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Utilizzato per eseguire e annullare la registrazione dei programmi con una porta; è possibile accedere ai programmi di brano attualmente in corso di debug.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|rappresenta un'interfaccia utente personalizzata per selezionare la porta.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Rappresenta una richiesta per una porta da cui una nuova porta verrà creata o trova.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|rappresenta un fornitore di porte.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Rappresenta un fornitore di porte che possono persistere \(salvataggio su disco informazioni sulle porte che ha creato.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Consente all'interfaccia utente di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] per visualizzare il testo nella sezione di **informazioni di trasporto** della finestra di dialogo di **Connettersi da elaborare** .|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Consente di eseguire query per ottenere informazioni sul computer di destinazione.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|Rappresenta un'enumerazione su un set di porte.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Rappresenta un'enumerazione su un set di fornitori di porte.|  
  
##  <a name="Processes"></a> Processi  
 Queste interfacce rappresentano i processi, un singolo file eseguibile che contiene uno o più programmi.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Rappresenta un processo in esecuzione su un computer.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Rappresenta un processo attivamente supporta il debug \(utilizzato per sostituire il passaggio, continuare e metodi [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Execute interfaccia\).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Inviato da DE o dalla porta quando un processo è stato creato.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Inviato da DE o dalla porta quando un processo è stato eliminato.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Rappresenta un processo che deve tenere traccia della sessione è associata a.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|rappresenta un'enumerazione di un set di processi su una porta.|  
  
##  <a name="Programs"></a> Programmi  
 Queste interfacce rappresentano i programmi, unità logiche di esecuzione che non corrispondono a un eseguibile o a un modulo fisico.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Rappresenta [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) un oggetto che deve essere eseguito di interagisce con altri programmi in corso il debug contemporaneamente.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Rappresenta un'unità logica di esecuzione.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Inviato da DE o dalla porta quando un programma è stato creato.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Inviato da DE o dalla porta quando un programma è stato eliminato.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Rappresenta [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) un oggetto che può essere gestito dai motori di debug più.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Rappresenta [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che deve essere in grado di tenere traccia della sessione è associata a.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Rappresenta [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) un oggetto che può restituire informazioni sul processo in cui è in esecuzione.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Rappresenta un programma che può essere eseguito il debug.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Consente un nodo di programma da parte di un tentativo di effettuare la connessione al programma associato.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Fornisce una soluzione per lo SDM eseguire una query un DE sui programmi controllati da tale DE.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Utilizzato dal DES per registrare i programmi con lo SDM per mostrare corso il debug.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Rappresenta [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) in grado di effettuare il marshalling delle interfacce tramite il thread o elabora i limiti.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|rappresenta un'enumerazione di un set di programmi.|  
  
##  <a name="Properties"></a> Proprietà  
 Queste interfacce rappresentano le proprietà, un valore associato a un contesto specifico, in genere il risultato della valutazione di un'espressione.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Rappresenta [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) in cui è possibile visualizzare il relativo valore in modo personalizzato.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Rappresenta un valore di uno stack frame, un documento, o del risultato della valutazione di un'espressione.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Rappresenta arbitrariamente [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) un oggetto stringhe lunghe di supportare.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Inviato da DE quando una nuova proprietà \(rappresentato [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) dall'interfaccia è stata creata.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Inviato da DE quando una proprietà è stata eliminata.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Rappresenta un riferimento a una proprietà che può trovarsi all'esterno di tutti gli stack frame specifico.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Rappresenta un'enumerazione su un insieme [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) di strutture che descrivono le variabili, registri, i parametri e le espressioni.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Rappresenta un'enumerazione su un insieme [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) di strutture.|  
  
##  <a name="StackFrames"></a> Stack frame  
 Queste interfacce rappresentano uno stack frame, un contesto in cui un punto di interruzione o un'eccezione si è verificato.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Rappresenta un contesto in cui un punto di interruzione o un'eccezione si è verificato.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Rappresenta [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) un oggetto che può gestire le eccezioni rilevate.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Rappresenta un'enumerazione sul set di strutture [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) che specificano la sequenza di chiamata di funzione utilizzata per ricevere a uno stack frame specifico.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Rappresenta un'enumerazione su un insieme [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) di strutture, che descrivono gli stack frame.|  
  
##  <a name="Threads"></a> Thread  
 Queste interfacce rappresentano i thread e gli eventi associati.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Rappresenta un thread di esecuzione.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Inviato da DE quando è stato creato un thread.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Inviato da DE quando un thread è stato eliminato.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Inviato da DE quando un thread ha modificato il nome.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Rappresenta un'enumerazione su un set di thread.|  
  
##  <a name="TypeVisualizers"></a> Visualizzatori di tipi  
 Queste interfacce forniscono il supporto per i visualizzatori di tipi.  Queste interfacce sono normalmente implementate da un analizzatore di espressioni.  
  
|Interfaccia|Implementato da|Descrizione|  
|-----------------|---------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Rappresenta una matrice di byte da presentare a un visualizzatore del tipo.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Fornisce metodi per ottenere l'accesso ai dati per essere passato a un visualizzatore del tipo.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Rappresenta una proprietà che fornisce l'accesso [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) alle implementazioni di.|  
  
## Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Creazione di un motore di Debug personalizzato](../../../extensibility/debugger/creating-a-custom-debug-engine.md)