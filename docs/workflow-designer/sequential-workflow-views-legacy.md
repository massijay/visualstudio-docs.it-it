---
title: "Visualizzazioni del flusso di lavoro sequenziale (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "visualizzazioni del flusso di lavoro sequenziale"
  - "flussi di lavoro sequenziali, visualizzazioni"
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Visualizzazioni del flusso di lavoro sequenziale (legacy)
In [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] è presente un'utilità [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy che è possibile utilizzare per fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o a [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] consente di creare graficamente le applicazioni di [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] utilizzando dell'interfaccia utente comune di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].Le applicazioni del [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] sono composte da passaggi del processo del flusso di lavoro chiamati attività.Per creare un flusso di lavoro, creare le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **Casella degli strumenti** nell'area di progettazione.  
  
 Quando si crea un flusso di lavoro sequenziale, rappresentato da un'attività [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), diventano disponibili tre visualizzazioni del flusso di lavoro.Queste visualizzazioni sono accessibili dal menu **Flusso di lavoro** e dal menu di scelta rapida nell'area di progettazione.  
  
 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.  
  
|Opzione di menu\/scheda|Descrizione|  
|-----------------------------|-----------------|  
|**Visualizza Flusso di lavoro sequenziale**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza Flusso di lavoro sequenziale** nel menu di scelta rapida per aprire la visualizzazione **Flusso di lavoro sequenziale** in cui viene mostrata la rappresentazione grafica basata sull'attività del flusso di lavoro sequenziale.In alternativa, selezionare **Visualizza Flusso di lavoro sequenziale** nel menu **Flusso di lavoro**.|  
|**Visualizza gestore annullamento**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza gestore annullamento** nel menu di scelta rapida per aprire la visualizzazione **Flusso di lavoro sequenziale** in cui viene mostrata l'attività [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associata al flusso di lavoro.In alternativa, selezionare **Visualizza gestore annullamento** nel menu **Flusso di lavoro**.|  
|**Visualizza gestore errori**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza gestori errori** nel menu di scelta rapida per aprire la visualizzazione **Errori** in cui viene mostrata l'attività [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associata al flusso di lavoro.In alternativa, selezionare **Visualizza gestori errori** dal menu **Flusso di lavoro**.|  
  
 Per ulteriori informazioni su visualizzazioni simili, vedere [Visualizzazioni delle attività \(legacy\)](../workflow-designer/activity-views-legacy.md).  
  
## Vedere anche  
 [Visualizzazioni delle attività \(legacy\)](../workflow-designer/activity-views-legacy.md)   
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Modalità di creazione flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65014)