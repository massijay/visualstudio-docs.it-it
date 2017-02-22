---
title: "Procedura: creare progetti di flusso di lavoro (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "progetti, flusso di lavoro"
  - "progetti di flusso di lavoro, creazione"
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: creare progetti di flusso di lavoro (legacy)
Seguire questi passaggi per creare un progetto [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che viene destinato a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o a [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].In questa procedura viene utilizzata la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy fornita da [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
### Per creare un progetto di flusso di lavoro  
  
1.  Avviare [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
3.  Selezionare l'opzione **.NET Framework 3.0** o l'opzione **.NET Framework 3.5** nell'elenco a discesa nella parte superiore della finestra **Nuovo progetto** per accedere alla finestra di progettazione legacy.  
  
    > [!NOTE]
    >  L'opzione predefinita in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] è **.NET Framework 4**.Questa opzione viene utilizzata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e non utilizza la finestra di progettazione legacy.  
  
4.  Nel riquadro **Tipi di progetto**, selezionare progetti Visual C\# o progetti Visual Basic, quindi selezionare **Flusso di lavoro**.  
  
5.  Nel riquadro **Modelli**, selezionare uno dei modelli di progetto installati:  
  
    -   Applicazione console del flusso di lavoro sequenziale  
  
    -   Libreria del flusso di lavoro sequenziale  
  
    -   Libreria delle attività del flusso di lavoro  
  
    -   Applicazione console del flusso di lavoro della macchina a stati  
  
    -   Libreria del flusso di lavoro di una macchina a stati  
  
    -   Progetto del flusso di lavoro vuoto  
  
6.  Nella casella **Nome**, immettere un nome descrittivo che renda il progetto facilmente identificabile.  
  
7.  Nella casella **Percorso** immettere la directory nella quale si desidera salvare il progetto o fare clic su **Sfoglia** per passare a tale directory.  
  
     Se si desidera creare una directory della soluzione per il progetto, selezionare la casella di controllo **Crea directory per la soluzione** e immettere un nome nella casella **Nome della soluzione**.  
  
8.  Scegliere **OK**.  
  
## Vedere anche  
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)