---
title: "Utilizzo di Progettazione flussi di lavoro legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Visual Studio 2005 Extensions for Windows Workflow Foundation, informazioni"
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Utilizzo di Progettazione flussi di lavoro legacy
La [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy fornita da [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] può essere utilizzata per fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o a [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Per accedere alla finestra di progettazione legacy, selezionare l'opzione **.NET Framework 3.0** o l'opzione **.NET Framework 3.5** nell'elenco a discesa nella parte superiore della finestra **Nuovo progetto**.L'opzione predefinita in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] è **.NET Framework 4** e viene utilizzata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] consente di creare graficamente le applicazioni di [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] utilizzando l'interfaccia utente comune di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].Le applicazioni del [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] sono composte da passaggi del processo del flusso di lavoro chiamati attività.Per creare un flusso di lavoro, creare le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **Casella degli strumenti** nell'area di progettazione.  
  
 Nella tabella seguente sono elencate le funzionalità principali di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per Windows Workflow Foundation.  
  
|Funzionalità|Descrizione|  
|------------------|-----------------|  
|Attività di trascinamento della selezione|Trascinare le attività dalla **Casella degli strumenti** nella superficie dell'area di progettazione per creare un flusso di lavoro.|  
|Browser delle proprietà|La finestra **Proprietà** standard in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è utilizzata per configurare le proprietà di un'attività.|  
|Zoom|L'icona **Livello di zoom** a forma di binocolo si trova sotto la barra di scorrimento verticale sul lato destro dell'area di progettazione.Fare clic sul binocolo e selezionare una percentuale di zoom per eseguire lo zoom avanti o indietro dell'elemento grafico del flusso di lavoro.È inoltre possibile utilizzare le opzioni del cursore a forma di lente di ingrandimento dell'icona **Panoramica** per eseguire lo zoom avanti e indietro.|  
|Panoramica|L'icona **Panoramica**, un cerchio contenente quattro frecce incrociate che puntano in quattro direzioni, si trova sotto la barra di scorrimento verticale sul lato destro dell'area di progettazione esattamente sotto l'icona dello zoom a forma di binocolo.Facendo clic sull'icona di panoramica, le opzioni del cursore seguenti verranno offerte da un menu a comparsa:<br /><br /> -   Il cursore a forma di lente di ingrandimento  **Zoom avanti** consente di ingrandire in avanti facendo clic sull'area di progettazione.<br />-   Il cursore a forma di lente di ingrandimento **Zoom indietro** consente di ingrandire indietro facendo clic sull'area di progettazione.<br />-   Il cursore a forma di mano **Strumento di navigazione** consente di agganciare e spostare la visualizzazione di un flusso di lavoro nell'area di progettazione.<br />-   Il cursore a freccia **Impostazione predefinita** consente di tornare dagli altri cursori al cursore della freccia predefinito.|  
|Scorrimento automatico|Se si ha un grande flusso di lavoro, è necessario posizionare un'attività oltre la visualizzazione visibile dell'area di progettazione.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di trascinare un'attività verso il bordo dell'area di progettazione nel punto più vicino a dove si desidera inserire l'attività.La visualizzazione dell'area di progettazione scorre automaticamente in quella direzione.|  
|Smart tag|Le attività la cui configurazione non è completa o valida sono contrassegnate da un'icona di punto esclamativo.È possibile fare clic sull'icona e visualizzare un elenco a discesa di richieste di configurazione esistenti sull'attività.È quindi possibile utilizzare la finestra **Proprietà** per configurare l'attività in modo appropriato.Quando tutte le proprietà sono valide per l'attività, l'icona di punto esclamativo scompare.|  
  
## In questa sezione  
 [Finestre del flusso di lavoro di Visual Studio \(legacy\)](../workflow-designer/visual-studio-workflow-windows-legacy.md)  
  
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)  
  
 [Visualizzazioni del flusso di lavoro sequenziale \(legacy\)](../workflow-designer/sequential-workflow-views-legacy.md)  
  
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)  
  
 [Utilizzo di temi in flussi di lavoro \(legacy\)](../workflow-designer/using-themes-in-workflows-legacy.md)  
  
 [Utilizzo della finestra di progettazione flusso di lavoro di una macchina a stati \(legacy\)](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)  
  
 [Utilizzo dell'ActivityDesigner legacy](../workflow-designer/using-the-legacy-activity-designer.md)  
  
 [Finestra di progettazione legacy per la Guida interfaccia utente di Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)  
  
## Vedere anche  
 [Sviluppo dei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65010)