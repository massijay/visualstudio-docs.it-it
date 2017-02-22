---
title: "ActivityDesigner Parallel | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Parallel.UI"
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner Parallel
L'attività <xref:System.Activities.Statements.Parallel> esegue contemporaneamente una raccolta delle attività figlio.  
  
## Attività Parallel  
 L'attività <xref:System.Activities.Statements.Parallel> archivia le relative attività figlio in una raccolta <xref:System.Activities.Statements.Parallel.Branches%2A>.Utilizzare l'attività <xref:System.Activities.Statements.Parallel> anziché l'attività <xref:System.Activities.Statements.Sequence> se alcune delle attività figlio possono diventare inattive.  
  
 L'attività <xref:System.Activities.Statements.Parallel> include una proprietà <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> contenente un'espressione [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] specificata dall'utente.L'attività <xref:System.Activities.Statements.Parallel> valuta tale proprietà in seguito al completamento di ogni ramo.Se restituisce **True**, l'attività <xref:System.Activities.Statements.Parallel> viene completata senza eseguire gli altri rami.Se <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> non restituisce **True**, l'attività <xref:System.Activities.Statements.Parallel> viene completata dopo che tutte le relative attività figlio sono state completate.  
  
### Utilizzo dell'ActivityDesigner Parallel  
 L'ActivityDesigner **Parallel** è disponibile nella categoria **Flusso di controllo** della **Casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** sul lato sinistro della [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, selezionare **Casella degli strumenti** dal menu **Visualizza** oppure premere la combinazione CTRL\+ALT\+X.  
  
 L'ActivityDesigner **Parallel** può essere trascinato dalla **Casella degli strumenti** e rilasciato nel punto in cui in genere si posizionano gli ActivityDesigner nell'area della [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], ad esempio, all'interno dell'ActivityDesigner **Sequence**.Dopo averlo rilasciato in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], viene creata un'attività <xref:System.Activities.Statements.Parallel>, che per impostazione predefinita contiene una proprietà <xref:System.Activities.Activity.DisplayName%2A> di **Parallel** .  
  
 Per aggiungere un'attività alla raccolta <xref:System.Activities.Statements.Parallel.Branches%2A> dell'attività Parallel, trascinare un altro ActivityDesigner dalla **Casella degli strumenti** e rilasciarlo sul triangolo all'interno dell'ActivityDesigner **Parallel**.I triangoli si trovano di fianco alle attività contenute nei rami.È possibile aggiungere ulteriori attività ripetendo questa procedura.È possibile riordinare le attività trascinandole e rilasciandole all'interno dell'ActivityDesigner **Parallel**.  
  
### Proprietà di ParallelActivity in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà dell'attività Parallel e ne viene descritta la modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner.Il valore predefinito è **Parallel**.Facoltativamente, è possibile modificare il valore nella griglia **Proprietà** o direttamente nell'intestazione dell'ActivityDesigner.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la raccolta di attività figlio da eseguire.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Restituisce il risultato dopo il completamento di un ramo.Se restituisce **True**, i rami in sospeso pianificati vengono annullati.Se questa proprietà non è impostata o restituisce **False**, l'attività viene completata quando tutte le relative attività figlio sono state completate.Il valore predefinito è **null**.|  
  
## Vedere anche  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)