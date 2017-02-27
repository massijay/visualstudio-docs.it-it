---
title: "Visualizzazioni delle attivit&#224; (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "attività, visualizzazioni attività"
  - "visualizzazioni attività"
  - "visualizzazioni, attività"
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Visualizzazioni delle attivit&#224; (legacy)
Per molte delle attività fornite da [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], dalle quali vengono creati i flussi di lavoro, sono disponibili numerose visualizzazioni Progettazione in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy.Quando si trascina un ActivityDesigner dalla **Casella degli strumenti** nell'area di progettazione e quando successivamente si seleziona l'attività, è possibile passare tra le diverse visualizzazioni Progettazione utilizzando il menu **Flusso di lavoro** oppure facendo clic con il pulsante destro del mouse sull'attività selezionata.Quando si sposta il puntatore sul nome di un'attività selezionata, viene inoltre visualizzato un insieme a discesa di schede che è possibile utilizzare per passare tra le diverse visualizzazioni.  
  
 Ogni attività dispone di almeno una visualizzazione. Si tratta della visualizzazione predefinita che viene aperta quando si trascina un ActivityDesigner dalla **Casella degli strumenti** nell'area di progettazione.Questa visualizzazione predefinita dell’attività è disponibile come opzione **Visualizza \[tipo di attività\]** nei menu e nella scheda, ad esempio, **Visualizzazione Parallel**.La maggior parte delle attività hanno visualizzazioni aggiuntive e attività diverse possono avere visualizzazioni diverse.Ad esempio, il l'attività [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) ha la visualizzazione di compensazione e l'attività [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) ha una visualizzazione degli eventi.Molte delle attività fornite da Windows Workflow Foundation dispongono delle visualizzazioni di progettazione **Visualizzazione gestore annullamento** e **Visualizzazione errori** per visualizzare [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) e [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) ad esse associate.  
  
 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.  
  
|Opzione di menu\/scheda|Descrizione|  
|-----------------------------|-----------------|  
|**Visualizzazione \[tipo di attività\]**|Selezionare questo menu o opzione della scheda per visualizzare la rappresentazione grafica predefinita dell'attività selezionata.|  
|**Visualizza gestore annullamento**|Selezionare questo menu o opzione della scheda per visualizzare l’attività [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associate all’attività selezionata.|  
|**Visualizza gestore errori**|Selezionare questo menu o opzione della scheda per visualizzare l’attività [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associate all’attività selezionata.|  
|**Visualizza gestore di compensazione**|Selezionare questo menu o opzione della scheda per visualizzare l’attività [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associata all’attività selezionata [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Visualizzazione del gestore di eventi**|Selezionare questo menu o opzione della scheda per visualizzare l’attività [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associata all’attività selezionata [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Per ulteriori informazioni su visualizzazioni simili, vedere  [Visualizzazioni del flusso di lavoro sequenziale \(legacy\)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## Vedere anche  
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)   
 [Visualizzazioni del flusso di lavoro sequenziale \(legacy\)](../workflow-designer/sequential-workflow-views-legacy.md)