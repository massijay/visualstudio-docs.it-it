---
title: "Attivit&#224; del flusso di lavoro legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "attività"
  - "attività del flusso di lavoro"
  - "flussi di lavoro, attività"
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Attivit&#224; del flusso di lavoro legacy
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] include un set predefinito di attività che forniscono funzionalità per i flussi di controllo, le condizioni, la gestione degli eventi, la gestione degli stati e la comunicazione con applicazioni e servizi.Durante la progettazione di flussi di lavoro, è possibile utilizzare le attività di sistema che sono fornite dalla [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] oppure è possibile creare attività personalizzate.  
  
 Nella tabella seguente è elencato il set di attività predefinito del framework di [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)].Molte, ma non tutte, di queste attività sono rappresentate da ActivityDesigner ai quali è possibile accedere dalla **Casella degli strumenti** di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Per creare un'attività, trascinare il relativo l'ActivityDesigner dalla **Casella degli strumenti** e rilasciarlo nell'area di progettazione.  
  
|Attività|Descrizione|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Utilizzata con l'attività **HandleExternalEventActivity** per le comunicazioni di input e di output con un servizio locale.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Utilizzato per contenere la logica di pulizia per un'attività annullata prima che sia terminata l’esecuzione di tutti i figli dell’attività.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Consente di aggiungere codice di Visual Basic o di C\# al flusso di lavoro.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Versione di compensazione di [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020).[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Versione compensabile di **TransactionScopeActivity**.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Consente di richiamare codice per annullare o compensare operazioni già eseguite dal flusso di lavoro quando si verifica un errore.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Wrapper per una o più attività che eseguono la compensazione per un'attività TransactionScopeActivity completata. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Esegue attività figlio in base a una condizione che si applica all'attività [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) stessa e in base a condizioni che si applicano separatamente a ogni attività figlio.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Consente di compilare ritardi nel flusso di lavoro basati su un intervallo di timeout.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Esegue il wrapping di una o di più attività eseguite quando si verifica un evento specificato.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Fornisce un framework per l'associazione di eventi a un'attività.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Esegue la relativa attività figlio contemporaneamente a un'attività [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018).[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Utilizzato per gestire un'eccezione di un tipo specificato.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Rappresenta un'attività composita che dispone di un elenco ordinato di attività figlio di tipo [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054).[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Utilizzata in combinazione con l'attività [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) per la comunicazione di input e output con un servizio locale.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività HandleExternalEvent](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Testa la condizione su ogni ramo ed esegue le attività sul primo ramo per il quale esiste una corrispondenza tra la condizione e **true**.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Rappresenta un ramo di un'attività [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033).[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Consente al flusso di lavoro di richiamare un servizio Web.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Consente al flusso di lavoro di richiamare un altro flusso di lavoro.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Attività composita contenente solo le attività figlio [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029).[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Fornisce una modalità per pianificare due o più rami di attività figlio  **SequenceActivity** per l'elaborazione contemporanea.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Utilizzare questa attività per rappresentare una raccolta di regole.Una regola è composta da condizioni e azioni risultanti.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Crea più istanze di un'unica attività figlio.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Fornisce una modalità semplice per collegare insieme più attività per l’esecuzione sequenziale.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Specifica una transizione a un nuovo stato.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Rappresenta uno stato in flusso di lavoro della macchina a stati.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Utilizzata in un'attività [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) come contenitore per le attività figlio che vengono eseguite all'uscita dell'attività **StateActivity**.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Utilizzata in un'attività [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) come contenitore per le attività figlio che vengono eseguite quando si accede all'attività **StateActivity**.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Sospende l'operazione del flusso di lavoro per abilitare l’intervento nell'evento di alcune condizioni di errore che richiedono attenzione speciale.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Esegue in sequenza le attività contenute in un dominio sincronizzato.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Consente di terminare immediatamente l'operazione del flusso di lavoro nel caso di una condizione di errore.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Consente di acquisire eccezioni aziendali generate come parte dei metadati di processo per un flusso di lavoro.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Fornisce un framework per la gestione di transazioni ed eccezioni.Per ulteriori informazioni, vedere [Utilizzo dell'attività TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Consente di definire l'occorrenza di un errore di servizio Web.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Riceve dati da un servizio Web.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Risponde a una richiesta di servizio Web eseguita a un flusso di lavoro.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Consente al flusso di lavoro di riprodurre a ciclo continuo fino a quando una condizione non viene soddisfatta.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] come creare attività personalizzate, vedere [Sviluppo di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65023) e [Utilizzo dell'ActivityDesigner legacy](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## Argomenti della sezione  
 [Visualizzazioni delle attività \(legacy\)](../workflow-designer/activity-views-legacy.md)  
 Descrive le diverse visualizzazioni di progettazione delle attività.  
  
 [Procedura: aggiungere attività nella Casella degli strumenti](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Illustra come aggiungere attività alla casella degli strumenti.  
  
 [Procedura: creare una condizione della regola dichiarativa \(legacy\)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Illustra la procedura per creare una condizione della regola dichiarativa.  
  
 [Procedura: creare un set di regole per l'attività PolicyActivity \(legacy\)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Illustra la procedura per creare un insieme di regole per l'attività PolicyActivity.  
  
 [Procedura: implementare un'operazione del contratto WCF \(legacy\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Illustra la procedura per implementare un'operazione del contratto [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
 [Procedura: richiamare un'operazione del contratto WCF \(legacy\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Illustra la procedura per richiamare un'operazione del contratto [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
## Vedere anche  
 [Attività di Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Sviluppo dei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Sviluppo di attività del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65023)