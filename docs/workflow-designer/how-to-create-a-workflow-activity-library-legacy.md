---
title: "Procedura: creare una libreria di attivit&#224; del flusso di lavoro (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "progetti, librerie delle attività del flusso di lavoro"
  - "librerie delle attività del flusso di lavoro"
  - "flussi di lavoro, progetti libreria di attività"
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: creare una libreria di attivit&#224; del flusso di lavoro (legacy)
Seguire questi passaggi per creare un progetto libreria attività flussi di lavoro utilizzando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy fornita da [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### Per creare un progetto libreria attività flussi di lavoro  
  
1.  Avviare Visual Studio.  
  
2.  Scegliere **Nuovo** dal menu **File** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
3.  Selezionare l'opzione **.NET Framework 3.0** o l'opzione **.NET Framework 3.5** nell'elenco a discesa nella parte superiore della finestra **Nuovo progetto** per accedere alla finestra di progettazione legacy.  
  
    > [!NOTE]
    >  L'opzione predefinita in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] è **.NET Framework 4**.Questa opzione viene utilizzata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e non utilizza la finestra di progettazione legacy.  
  
4.  Nel riquadro **Tipi di progetto**, selezionare Visual C\# o Visual Basic \(in **Altri linguaggi**\) e quindi selezionare **Flusso di lavoro**.  
  
5.  Nel riquadro **Modelli** selezionare **Libreria di attività del flusso di lavoro**.  
  
6.  Nella casella **Nome**, immettere un nome descrittivo che renda il progetto facilmente identificabile.  
  
7.  Nella casella **Percorso** immettere la directory nella quale si desidera salvare il progetto o fare clic su **Sfoglia** per passare a tale directory.  
  
     Se si desidera creare una directory della soluzione per il progetto, selezionare la casella di controllo **Crea directory per la soluzione** e immettere un nome nella casella **Nome della soluzione**.  
  
8.  Scegliere **OK**.  
  
## Vedere anche  
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Utilizzo dell'ActivityDesigner legacy](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)   
 [Developing Workflow Activities](http://msdn.microsoft.com/it-it/19876dfc-dfa5-4d52-b1f5-1d087474cc52)   
 [Windows Workflow Foundation Activities](http://msdn.microsoft.com/it-it/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)