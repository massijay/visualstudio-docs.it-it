---
title: "Procedura: creare applicazioni console del flusso di lavoro sequenziale (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "applicazioni console, flusso di lavoro sequenziale"
  - "flussi di lavoro sequenziali, applicazioni console"
  - "flussi di lavoro, applicazioni console"
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: creare applicazioni console del flusso di lavoro sequenziale (legacy)
Seguire questi passaggi per creare un progetto Applicazione console flusso di lavoro sequenziale utilizzando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy fornita da [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### Per creare un'applicazione console flusso di lavoro sequenziale  
  
1.  Avviare Visual Studio.  
  
2.  Scegliere **Nuovo** dal menu **File** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
3.  Selezionare l'opzione **.NET Framework 3.0** o l'opzione **.NET Framework 3.5** nell'elenco a discesa nella parte superiore della finestra **Nuovo progetto** per accedere alla finestra di progettazione legacy.  
  
    > [!NOTE]
    >  L'opzione predefinita in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] è **.NET Framework 4**.Questa opzione viene utilizzata per creare applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e non utilizza la finestra di progettazione legacy.  
  
4.  Nel riquadro **Tipi di progetto**, selezionare progetti Visual C\# o progetti Visual Basic, \(sotto **Altri linguaggi**\), quindi selezionare **Flusso di lavoro**.  
  
5.  Nel riquadro **Modelli** selezionare  **Applicazione console del flusso di lavoro sequenziale**.  
  
6.  Nella casella **Nome**, immettere un nome descrittivo che renda il progetto facilmente identificabile.  
  
7.  Nella casella **Percorso** immettere la directory nella quale si desidera salvare il progetto o fare clic su **Sfoglia** per passare a tale directory.  
  
     Verrà aperta la finestra di progettazione Windows Forms nella quale verrà visualizzato il Form1 del progetto creato.  
  
8.  Scegliere **OK**.  
  
     Verrà aperta la finestra di Progettazione flussi di lavoro e verrà visualizzata l'area di progettazione del flusso di lavoro sequenziale creato.  
  
9. Trascinare un'attività dalla **Casella degli strumenti** all'area di progettazione nell’area designata **Rilascia attività**.  
  
## Vedere anche  
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Developing Workflows](http://msdn.microsoft.com/it-it/557bcb1f-a7ab-49f6-8df7-2706b7001301)