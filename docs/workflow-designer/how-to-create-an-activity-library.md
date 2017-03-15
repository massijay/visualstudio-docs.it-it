---
title: "Procedura: creare una libreria attivit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: creare una libreria attivit&#224;
Le attività personalizzate sono utilizzate per modellare i processi aziendali particolari in un flusso di lavoro.Il modello Libreria attività in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] è stato fornito per consentire di creare tali attività personalizzate utilizzando visivamente [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
### Per creare una libreria attività flussi di lavoro  
  
1.  Avviare [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
3.  Nel riquadro **Tipi progetto** selezionare **Flusso di lavoro** dal gruppo di progetti **Visual C\#** o **Visual Basic** a seconda del linguaggio preferito.  
  
4.  Nel riquadro **Modelli** selezionare **Libreria attività**.  
  
5.  Nella casella **Nome** digitare un nome descrittivo che renda il progetto facilmente identificabile.  
  
6.  Nella casella **Percorso** digitare la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per cercarla e selezionarla.  
  
7.  Nella casella **Soluzione**, digitare un nome descrittivo per la soluzione, quindi fare clic su **OK**.  
  
    > [!NOTE]
    >  Se si desidera aggiungere un'applicazione console del flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e selezionare **Aggiungi**, quindi **Nuovo progetto** per aprire la finestra di dialogo **Nuovo progetto**.Procedere come descritto sopra in questa procedura.  
  
8.  Il modello di progetto crea una definizione di attività in XAML.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] verrà visualizzato con l'area di disegno per l'attività personalizzata.  
  
9. Trascinare un'attività dalla **Casella degli strumenti** nell'area della finestra di progettazione per includerla nell'attività personalizzata.  
  
    > [!CAUTION]
    >  È consentita una sola attività figlio nel corpo dell'attività personalizzata. L'attività in questione può tuttavia essere un oggetto CompositeActivity, quale <xref:System.Activities.Statements.Sequence> o <xref:System.Activities.Statements.Flowchart>.  
  
## Vedere anche  
 [Procedura: creare un'attività](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)