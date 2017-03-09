---
title: "Procedura: creare una libreria del flusso di lavoro di macchina a stati (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "progetti, libreria del flusso di lavoro di una macchina a stati"
  - "librerie del flusso di lavoro di una macchina a stati"
  - "flussi di lavoro, libreria del flusso di lavoro di una macchina a stati"
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: 6
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: creare una libreria del flusso di lavoro di macchina a stati (legacy)
Seguire questi passaggi per creare un progetto libreria flusso di lavoro di una macchina a stati utilizzando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy fornita da [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### Per creare un progetto libreria del flusso di lavoro di una macchina a stati  
  
1.  Avviare Visual Studio.  
  
2.  Scegliere **Nuovo** dal menu **File** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
3.  Selezionare l'opzione **.NET Framework 3.0** o l'opzione **.NET Framework 3.5** nell'elenco a discesa nella parte superiore della finestra **Nuovo progetto** per accedere alla finestra di progettazione legacy.  
  
    > [!NOTE]
    >  L'opzione predefinita in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] è **.NET Framework 4**.Questa opzione viene utilizzata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e non utilizza la finestra di progettazione legacy.  
  
4.  Nel riquadro **Tipi di progetto**, selezionare Visual C\# o Visual Basic \(in **Altri linguaggi**\) e quindi selezionare **Flusso di lavoro**.  
  
5.  Nel riquadro **Modelli** selezionare **Libreria del flusso di lavoro della macchina a stati**.  
  
6.  Nella casella **Nome**, immettere un nome descrittivo che renda il progetto facilmente identificabile.  
  
7.  Nella casella **Percorso** immettere la directory nella quale si desidera salvare il progetto o fare clic su **Sfoglia** per passare a tale directory.  
  
     Se si desidera creare una directory della soluzione per il progetto, selezionare la casella di controllo **Crea directory per la soluzione** e immettere un nome nella casella **Nome della soluzione**.  
  
8.  Scegliere **OK**.  
  
## Vedere anche  
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [State Machine Workflows](http://msdn.microsoft.com/it-it/f0b837d0-9d74-41dc-9724-13acbcd3c433)