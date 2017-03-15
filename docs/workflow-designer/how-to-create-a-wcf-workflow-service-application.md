---
title: "Procedura: creare un&#39;applicazione del servizio flusso di lavoro WCF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: creare un&#39;applicazione del servizio flusso di lavoro WCF
Le applicazioni di servizi flusso di lavoro di [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] sono servizi di comunicazioni distribuite che scambiano messaggi con i client oltre i limiti dei processi.L'implementazione del contratto di servizio sul lato servizio viene eseguita in modo dichiarativo tramite le attività del flusso di lavoro [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] in modo analogo ai servizi flusso di lavoro legacy di .NET Framework 3.5.  
  
### Per creare un'applicazione di servizi flusso di lavoro WCF  
  
1.  Avviare [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
3.  Nel riquadro **Modelli installati** selezionare **WCF** o **Flusso di lavoro** dal gruppo **Visual C\#** o **Visual Basic** a seconda del linguaggio scelto.  
  
4.  Nel riquadro centrale selezionare **Applicazione di servizi flusso di lavoro WCF**.  
  
5.  Nella casella **Nome** immettere un nome descrittivo che renda il progetto facilmente identificabile.  
  
6.  Nella casella **Percorso** immettere la directory nella quale si desidera salvare il progetto o fare clic su **Sfoglia** per passare a tale directory.  
  
7.  Nella casella **Soluzione** selezionare per creare una soluzione nuova e fare clic su **OK**.  
  
    > [!NOTE]
    >  Se si desidera aggiungere un'applicazione console del flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e selezionare **Aggiungi**, quindi **Nuovo progetto** per aprire la finestra di dialogo **Nuovo progetto**.Procedere come descritto sopra in questa procedura.  
  
8.  Il modello di progetto crea una definizione di servizio come XAML.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] viene aperto sulla visualizzazione Progettazione con un'attività <xref:System.Activities.Statements.Sequence> che contiene un set di attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>.  
  
## Vedere anche  
 [Procedura: creare un'attività](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)