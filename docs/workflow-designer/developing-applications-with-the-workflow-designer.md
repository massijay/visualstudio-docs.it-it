---
title: "Sviluppo di applicazioni con Progettazione flussi di lavoro | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DefaultWorkflowDesigner"
  - "DefaultWorkflowDesigner.UI"
helpviewer_keywords: 
  - "Progettazione flussi di lavoro di Visual Studio 2010 [WFD]"
  - "Progettazione flussi di lavoro di Visual Studio 2010 [WFD], cenni preliminari"
  - "Progettazione flussi di lavoro [WFD]"
  - "Progettazione flussi di lavoro [WFD], cenni preliminari"
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
caps.handback.revision: 17
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Sviluppo di applicazioni con Progettazione flussi di lavoro
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] consiste in un debugger e una finestra di progettazione visiva per il debug e la costruzione grafica di applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] nella versione [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] ospitata nell'ambiente di sviluppo di [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Consente di creare un'applicazione di flussi di lavoro compositi, una libreria attività o un servizio [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] tramite l'utilizzo di modelli e ActivityDesigner.[!INCLUDE[crabout](../test/includes/crabout_md.md)] i flussi di lavoro, vedere [Windows Workflow Foundation](../Topic/Windows%20Workflow%20Foundation.md).  
  
 Di seguito sono indicate diverse nuove caratteristiche di progettazione che fanno la distinzione tra questa nuova versione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] e le versioni precedenti di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] è basato su [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)].Questo aspetto migliora l'esperienza con gli ActivityDesigner e le prestazioni nei casi di flussi di lavoro complessi e di grandi dimensioni.  
  
-   Le attività personalizzate sono ora progettate con [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)]. L'utilizzo del modello di programmazione e di XAML per la creazione di ActivityDesigner è stato semplificato.  
  
-   È stata implementata un'attività Flowchart, in modo da visualizzare il flusso di programma utilizzando lo stile comune di modellazione del diagramma di flusso.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] presenta una nuova finestra di progettazione variabili che consente di dichiarare e assegnare un ambito alle variabili nei flussi di lavoro, associandole alle attività.  
  
-   In [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fornisce funzionalità IntelliSense complete quando vengono create espressioni di Visual Basic nei flussi di lavoro di [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
-   L'esperienza di debug si estende ora a XAML, per consentire l'impostazione dei punti di interruzione nella definizione del flusso di lavoro XAML e di eseguire istruzioni nel codice XAML in fase di esecuzione, diventando in questo modo simile all'esperienza del codice gestito.  
  
-   La riallocazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] esternamente a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene semplificata in modo significativo rispetto alle versioni precedenti dal momento che ora è sufficiente specificare solo alcune righe di codice.  
  
-   La nuova attività <xref:System.Activities.Statements.Flowchart> e il relativo [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md) consentono di visualizzare il flusso di programma utilizzando lo stile comune di modellazione del diagramma di flusso.  
  
-   Le attività di messaggistica sono state migliorate per consentire la scrittura di servizi [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] completamente dichiarativi \(senza codice\).  
  
-   La funzionalità **Aggiungi riferimento al servizio…** consente di generare automaticamente le attività che accedono ai servizi Web.  
  
## In questa sezione  
 [Utilizzo di Progettazione flussi di lavoro](../workflow-designer/using-the-workflow-designer.md)  
 Viene illustrato come creare nuove attività e progetti flusso di lavoro utilizzando le finestre di progettazione incorporate e come utilizzare gli altri strumenti forniti dalla finestra di progettazione per gestire argomenti, variabili, espressioni, importazioni e navigazioni.  
  
 [Utilizzo degli ActivityDesigner](../workflow-designer/using-the-activity-designers.md)  
 Vengono descritte le categorie di attività e modelli e le relative finestre di progettazione forniti dal sistema.  
  
 [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Viene illustrato come eseguire routine di debug tradizionali nonché il debug di espressioni e codice XAML.  
  
 [Guida dell'interfaccia utente della finestra di progettazione dei flussi di lavoro](../workflow-designer/workflow-designer-ui-help.md)  
 Contiene argomenti della Guida sensibili al contesto per finestre di dialogo fornite dalla [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] nonché linee guida sulle funzionalità della shell della finestra di progettazione, le scelte rapide da tastiera e i messaggi di errore.  
  
 [Sviluppo di applicazioni flusso di lavoro destinate a Framework .NET 3.0 o Framework .NET 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Contiene le linee guida sull'utilizzo della finestra di progettazione legacy che viene destinata a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [Riallocazione della finestra di progettazione &#91;esempi WF&#93;](../Topic/Designer%20ReHosting.md)  
 In questo esempio viene illustrato come creare il layout WPF per contenere la finestra di progettazione.  
  
 [ActivityDesigner personalizzati](../Topic/Custom%20Activity%20Designers.md)  
 In questa sezione sono contenuti esempi di attività in cui vengono utilizzate finestre di progettazione personalizzate da visualizzare nella progettazione flussi di lavoro.