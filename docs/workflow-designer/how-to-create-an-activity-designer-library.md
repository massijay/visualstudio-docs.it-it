---
title: "Procedura: creare una libreria ActivityDesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: creare una libreria ActivityDesigner
Gli ActivityDesigner personalizzati consentono di creare un'interfaccia utente per un'attività personalizzata o standard.È possibile controllare la complessità dell'interfaccia utente e creare più ActivityDesigner per un'attività.Questo scenario consente di creare finestre di progettazione personalizzate per diversi destinatari.  
  
### Per creare una libreria ActivityDesigner  
  
1.  Avviare [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi selezionare **Progetto…** per aprire la finestra di dialogo **Nuovo progetto**.  
  
3.  Nel riquadro **Tipi progetto** selezionare **Flusso di lavoro** dal gruppo **Visual C\#** o **Visual Basic** a seconda del linguaggio preferito.  
  
4.  Nel riquadro **Modelli** selezionare **Libreria ActivityDesigner**.  
  
5.  Nella casella **Nome** immettere un nome descrittivo che renda il progetto facilmente identificabile.  
  
6.  Nella casella **Percorso** immettere la directory nella quale si desidera salvare il progetto o fare clic su **Sfoglia** per passare a tale directory.  
  
7.  Nella casella **Soluzione**, digitare un nome descrittivo per la soluzione, quindi fare clic su **OK**.  
  
    > [!NOTE]
    >  Se si desidera aggiungere un'applicazione console del flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e selezionare **Aggiungi**, quindi **Nuovo progetto** per aprire la finestra di dialogo **Nuovo progetto**.Procedere come descritto sopra in questa procedura.  
  
8.  Il modello di progetto crea una definizione dell'ActivityDesigner in XAML mentre il file di implementazione code\-behind è in codice sorgente.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] verrà visualizzato con l'area di disegno per l'ActivityDesigner.  
  
9. Trascinare i controlli di [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] dalla **Casella degli strumenti** nell'area di progettazione per utilizzarli nell'ActivityDesigner personalizzato.Per un esempio relativo all'implementazione di un ActivityDesigner personalizzato, vedere [Procedura: Creare un ActivityDesigner personalizzato](../Topic/How%20to:%20Create%20a%20Custom%20Activity%20Designer.md).  
  
    > [!WARNING]
    >  Gli ActivityDesigner personalizzati possono essere utilizzati per le attività personalizzate nonché per le attività [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] predefinite.  
  
## Vedere anche  
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)