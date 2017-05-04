---
title: "Panoramica di debug script ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Panoramica di debug script ActiveX"
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Panoramica di debug script ActiveX
Le interfacce in corso di debug degli script consentono il debug indipendente dalla lingua e protezione associato e supportano un'ampia varietà di ambienti di sviluppo.  
  
 ![Processo di Script Host](../winscript/media/scp56activdbgarchgif.png "Scp56ActivDbgArchgif")  
Figura 1  
  
 Un ambiente di debug indipendente dalla lingua può supportare qualsiasi linguaggio di programmazione o combinazione di linguaggi di programmazione, senza disporre di conoscenze specifiche di ognuno di questi linguaggi.  L'ambiente di debug supporta l'esecuzione di istruzioni tra linguaggi e i punti di interruzione.  In questi cenni preliminari viene principalmente concentrano sui linguaggi di script di supporto, quali VBScript e [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\).  
  
 Un debugger host associato automaticamente può essere utilizzato con qualsiasi host di scripting attivo, ad esempio Internet Explorer o un host personalizzato.  I controlli host che dal debugger presenta all'utente, dalla struttura ad albero del contenuto e la colorazione della sintassi dei documenti di debug.  Ciò consente al codice sorgente sottoposto a debug da visualizzare nel contesto del documento host.  Ad esempio, Internet Explorer può mostrare uno script in una pagina HTML.  
  
 Nelle sottosezioni riportate di seguito, ogni componente chiave nel debug attivo e le relative interfacce collegate vengono discusse.  Tuttavia, prima di continuare ulteriormente, vari impostano i concetti di debug attivi devono essere definiti:  
  
 applicazione host  
 L'applicazione che contiene i moduli di gestione di script e offre un set di script di oggetti \(o "modello a oggetti"\).  
  
 motore di linguaggio  
 Un componente che fornisce l'analisi, l'esecuzione e il debug delle astrazioni di un particolare linguaggio.  
  
 l'ide del debugger  
 L'applicazione che fornisce l'interfaccia utente di debug comunicazione con l'applicazione host e motori del linguaggio.  
  
 amministratore del computer di debug  
 Componente che gestisce il Registro di sistema dei processi dell'applicazione sottoponibili a debug.  
  
 amministratore del processo di debug  
 Componente che gestisce la struttura ad albero dei documenti sottoponibili a debug per una determinata applicazione, tenere traccia dei thread in esecuzione, e così via.  
  
 contesto di documento  
 Un contesto del documento è un'astrazione che rappresenta un intervallo specifico nel codice sorgente di un documento host.  
  
 contesto di codice  
 Un contesto di codice rappresenta una determinata posizione del codice in esecuzione di un modulo di linguaggio \("un puntatore all'istruzione virtual"\).  
  
 contesto dell'espressione  
 Un particolare contesto \(ad esempio, uno stack frame in cui le espressioni possono essere valutate nel motore di linguaggio.  
  
 esplorazione dell'oggetto  
 Una rappresentazione e indipendente da strutturata di un nome di oggetto, un tipo, un valore e oggetti secondari, appropriati per implementare un'interfaccia utente della finestra Espressioni di controllo".  
  
 In vengono forniti cenni preliminari su ciascun componente di debug attiva principali e di corrispondenza, interfacce collegate, seguiti dai dettagli di tali interfacce.  
  
## Motore di linguaggio  
 Il motore di linguaggio fornisce:  
  
-   Analisi ed esecuzione del linguaggio.  
  
-   Supporto di debug \(punti di interruzione e così via\).  
  
-   Valutazione di un'espressione.  
  
-   Colorazione della sintassi.  
  
-   Esplorazione dell'oggetto.  
  
-   Enumerazione e analisi dello stack.  
  
 Di seguito sono riportate le interfacce che un motore di gestione di script deve supportare per fornire il debug, la valutazione di un'espressione e passare l'oggetto.  Queste interfacce sono utilizzate dall'applicazione host eseguire il mapping tra il contesto di documento e i contesti di codice del motore e anche dall'interfaccia utente del debugger di eseguire la valutazione di un'espressione, l'enumerazione dello stack e passare l'oggetto.  
  
 [Interfaccia IActiveScriptDebug](../winscript/reference/iactivescriptdebug-interface.md)  
 Consente di enumerare contesto di codice e di colorazione della sintassi.  
  
 [Interfaccia IActiveScriptErrorDebug](../winscript/reference/iactivescripterrordebug-interface.md)  
 Contesti e stack frame del documento di restituisce per gli errori.  
  
 [Interfaccia IActiveScriptSiteDebug Interface](../winscript/reference/iactivescriptsitedebug-interface.md)  
 Collegamento fornito host dal modulo di gestione di script al debugger.  
  
 [Interfaccia IDebugCodeContext](../winscript/reference/idebugcodecontext-interface.md)  
 Fornisce un "puntatore a l" virtuale in un thread.  
  
 [Interfaccia IEnumDebugCodeContexts](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 Enumera i contesti di codice che corrispondono a un contesto del documento.  
  
 [Interfaccia IDebugStackFrame](../winscript/reference/idebugstackframe-interface.md)  
 Rappresenta uno stack frame logico nello stack di thread.  
  
 [Interfaccia IDebugExpressionContext](../winscript/reference/idebugexpressioncontext-interface.md)  
 Fornisce contesto in cui le espressioni possono essere valutate.  
  
 [Interfaccia IDebugStackFrameSniffer](../winscript/reference/idebugstackframesniffer-interface.md)  
 Consente di enumerare gli stack frame logici.  
  
 [Interfaccia IDebugExpression](../winscript/reference/idebugexpression-interface.md)  
 Rappresenta un'espressione in modo asincrono valutata.  
  
 [Interfaccia IDebugSyncOperation](../winscript/reference/idebugsyncoperation-interface.md)  
 Consente a un modulo di gestione di script sottrarre di un'operazione da eseguire durante annidato in un thread bloccato particolare.  
  
 [Interfaccia IDebugAsyncOperation](../winscript/reference/idebugasyncoperation-interface.md)  
 Fornisce l'accesso asincrono a un'operazione sincrona di debug.  
  
 [Interfaccia IDebugAsyncOperationCallBack](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 Fornisce eventi di stato correlati allo stato di avanzamento della valutazione dell'interfaccia di `IDebugAsyncOperation`.  
  
 [Interfaccia IEnumDebugExpressionContexts](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 Enumerare una raccolta di oggetti `IDebugExpressionContexts`.  
  
 [Interfaccia IProvideExpressionContexts](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 Consente di enumerare i contesti di espressione noti da un componenti specifici.  
  
 [Interfaccia IDebugFormatter](../winscript/reference/idebugformatter-interface.md)  
 Consente a un linguaggio o un IDE personalizzare la conversione tra valori VARIABILI o tipi e stringhe di VARTYPE.  
  
 [Interfaccia IDebugStackFrameSnifferEx](../winscript/reference/idebugstackframesnifferex-interface.md)  
 Enumera gli stack frame logici per il PDM.  
  
## Host  
 L'host:  
  
-   Ospita i motori del linguaggio.  
  
-   Fornisce un modello a oggetti \(set di oggetti che possono essere basati su script\).  
  
-   Definisce una struttura ad albero dei documenti che è possibile eseguire il debug e i relativi contenuti.  
  
-   Organizza gli script nelle applicazioni virtuali.  
  
 Esistono due tipi di host:  
  
-   Un host muto supporta solo le interfacce attive base di script.  Non è in grado di controllare la struttura o organizzazioni del documento; ciò dipende interamente da script forniti i motori di linguaggio.  
  
-   Uno SmartHost supporta un più ampio set di interfacce che consente di definire la struttura ad albero del documento, il contenuto del documento e la colorazione della sintassi.  Esiste un set di interfacce di supporto, descritta nella sezione secondaria seguente, che rendono notevolmente più semplice un host siano uno SmartHost.  
  
### Interfacce di supporto dello SmartHost  
 I metodi di `IDebugDocumentHelper` forniscono un set di interfacce notevolmente semplificata che un host può utilizzare per usufruire dei vantaggi di smart tag senza gestire la complessità di grandi dimensioni \(\) e potenza delle interfacce complete host.  
  
 Un host non è necessario utilizzare tali interfacce, normalmente.  Tuttavia utilizzando queste interfacce può evitare di distribuire o utilizzando una serie di interfacce più complesse.  
  
 [Interfaccia IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md)  
 Implementata da PDM e fornisce le implementazioni di interfacce necessarie per l'hosting intelligente.  
  
 [Interfaccia IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md)  
 Distribuito eventualmente da host per esporre funzionalità di protezione specifica, come colorazione della sintassi, il debugger.  
  
 Per ulteriori informazioni, vedere [Implementazione delle interfacce helper Smart Host](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### Interfacce complete di SmartHost  
 Di seguito è riportato l'intero set di interfacce che uno SmartHost deve implementare o utilizzare se non utilizza le interfacce di supporto.  
  
 Interfacce implementate dall'host:  
  
 [Interfaccia IDebugDocumentInfo](../winscript/reference/idebugdocumentinfo-interface.md)  
 Fornisce informazioni su un documento, che può essere creata un'istanza.  
  
 [Interfaccia IDebugDocumentProvider](../winscript/reference/idebugdocumentprovider-interface.md)  
 Fornisce i mezzi per creare un'istanza di un documento su richiesta.  
  
 [Interfaccia IDebugDocument](../winscript/reference/idebugdocument-interface.md)  
 L'interfaccia di base per tutti i documenti di debug.  
  
 [Interfaccia IDebugDocumentText](../winscript/reference/idebugdocumenttext-interface.md)  
 Fornisce l'accesso a una versione di testo al documento di debug.  
  
 [Interfaccia IDebugDocumentTextAuthor](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Consente la modifica della versione di testo al documento di debug.  
  
 [Interfaccia IDebugDocumentContext](../winscript/reference/idebugdocumentcontext-interface.md)  
 Fornisce una rappresentazione astratta di una parte del documento in fase di debug.  
  
 Interfacce implementate da PDM per conto dell'host:  
  
 [Interfaccia IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Estende le funzionalità dell'interfaccia di `IDebugDocumentProvider` fornendo un contesto all'interno di una struttura ad albero del progetto.  
  
## L'ide del debugger  
 L'ide è un'interfaccia utente di debug indipendente da.  Fornisce:  
  
-   Editor\/visualizzazione del documento.  
  
-   Gestione del punto di interruzione.  
  
-   Valutazione e finestre Espressioni di controllo dell'espressione.  
  
-   Esplorazione dello stack frame.  
  
-   Esplorazione classe o dell'oggetto.  
  
-   Esplorare la struttura virtuale dell'applicazione.  
  
 Interfacce implementate dal debugger:  
  
 [Interfaccia IApplicationDebugger](../winscript/reference/iapplicationdebugger-interface.md)  
 L'interfaccia primaria esposta da una sessione dell'IDE del debugger.  
  
 [Interfaccia IApplicationDebuggerUI](../winscript/reference/iapplicationdebuggerui-interface.md)  
 Fornisce un componente esterno maggiore controllo sull'interfaccia utente \(UI\) del debugger.  
  
 [Interfaccia IDebugExpressionCallBack](../winscript/reference/idebugexpressioncallback-interface.md)  
 Fornisce eventi di stato per lo stato di avanzamento di valutazione di `IDebugExpression`.  
  
 [Interfaccia IDebugDocumentTextEvents](../winscript/reference/idebugdocumenttextevents-interface.md)  
 Fornisce eventi che segnalano le modifiche al documento di testo collegato.  
  
 [Interfaccia IDebugApplicationNodeEvents](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 Fornisce l'interfaccia eventi per l'interfaccia di `IDebugApplicationNode`.  
  
### Debug Machine Manager  
 L'amministratore del computer di debug include il passaggio di collegamento tra le applicazioni e i debugger virtuali gestione e enumerano un elenco di applicazioni virtuali attivi.  
  
 [Interfaccia IDebugSessionProvider](../winscript/reference/idebugsessionprovider-interface.md)  
 Stabilisce una sessione di debug per un'applicazione in esecuzione.  
  
 [Interfaccia IMachineDebugManager](../winscript/reference/imachinedebugmanager-interface.md)  
 L'interfaccia primaria all'amministratore del computer di debug.  
  
 [Interfaccia IMachineDebugManagerCookie](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Simile all'interfaccia di `IMachineDebugManager`, ma a questa interfaccia supporta i cookie di debug.  
  
 [Interfaccia IMachineDebugManagerEvents](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Modifiche dei segnali nell'elenco in esecuzione di un'applicazione gestita dall'amministratore del computer di debug.  
  
 [Interfaccia IEnumRemoteDebugApplications](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Enumera le applicazioni in esecuzione su un computer.  
  
### Amministratore del processo di debug  
 Il PDM esegue le operazioni seguenti:  
  
-   Sincronizza il debug dei motori di linguaggio più.  
  
-   Gestisce una struttura ad albero dei documenti sottoponibili a debug.  
  
-   Unisce gli stack frame.  
  
-   Punti di interruzione e l'esecuzione di istruzioni di coordinate tra i motori del linguaggio.  
  
-   Thread tramite appositi.  
  
-   Gestisce un thread del debugger per l'elaborazione asincrona.  
  
-   Comunica con l'amministratore del computer di debug e l'ide del debugger.  
  
 Le seguenti interfacce fornite dall'amministratore del processo di debug.  
  
 [Interfaccia IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md)  
 Interfaccia primaria all'amministratore del processo di debug.  Tale interfaccia può creare, aggiungere, rimuovere o un'applicazione virtuale da un processo.  
  
 [Interfaccia IRemoteDebugApplication](../winscript/reference/iremotedebugapplication-interface.md)  
 Rappresenta un'applicazione in esecuzione.  
  
 [Interfaccia IDebugApplication](../winscript/reference/idebugapplication-interface.md)  
 Espone metodi di debug non gestibili da remoto con i motori del linguaggio e gli host.  
  
 [Interfaccia IRemoteDebugApplicationThread](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 Rappresenta un thread di esecuzione all'interno di un'applicazione particolare.  
  
 [Interfaccia IDebugApplicationThread](../winscript/reference/idebugapplicationthread-interface.md)  
 Consente ai motori del linguaggio e gli host di fornire la sincronizzazione dei thread e gestire i thread specifico, informazioni di debug stato.  
  
 [Interfaccia IEnumRemoteDebugApplicationThreads](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 Enumera i thread in esecuzione in un'applicazione.  
  
 [Interfaccia IDebugThreadCall](../winscript/reference/idebugthreadcall-interface.md)  
 Chiamate eseguire il marshalling di spedizione.  
  
 [Interfaccia IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Gestisce una posizione per un documento nella gerarchia.  
  
 [Interfaccia IEnumDebugApplicationNodes](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 Enumera i nodi figlio di un nodo associato a un'applicazione.  
  
 [Interfaccia IEnumDebugStackFrames](../winscript/reference/ienumdebugstackframes-interface.md)  
 Enumera gli stack frame che corrispondono a un thread, unite dai motori.  
  
 [Interfaccia IDebugCookie](../winscript/reference/idebugcookie-interface.md)  
 Consente un cookie di debug da impostare nel debugger dello script.  
  
 [Interfaccia IDebugHelper](../winscript/reference/idebughelper-interface.md)  
 Opera da factory per i visualizzatori oggetti e i punti di connessione semplici dai moduli di gestione di script.  
  
 [Interfaccia ISimpleConnectionPoint](../winscript/reference/isimpleconnectionpoint-interface.md)  
 Fornisce un modo semplice per la descrizione e l'enumerazione degli eventi generati su un punto di connessione specifico, per i moduli di gestione di script.  
  
## Vedere anche  
 [Interfacce del debugger dello script ActiveX](../winscript/reference/active-script-debugger-interfaces.md)