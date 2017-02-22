---
title: "Procedura: creare un&#39;applicazione console flusso di lavoro | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: creare un&#39;applicazione console flusso di lavoro
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] consente di creare flussi di lavoro per l'esecuzione di processi di utenti o di sistema.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fornisce l'area di progettazione per la creazione di tali flussi.La [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] può essere utilizzata per creare flussi di lavoro dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o può essere integrata in altre applicazioni che riallocano la finestra di progettazione.  
  
 In questo argomento viene descritto come utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] per creare un flusso di lavoro in un'applicazione console.  
  
### Per creare un'applicazione console flusso di lavoro  
  
1.  Avviare [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
3.  Nel riquadro **Modelli installati** selezionare **Flusso di lavoro** dal gruppo **Visual C\#** o **Visual Basic** a seconda del linguaggio preferito.  
  
4.  Nel riquadro centrale selezionare **Applicazione console flusso di lavoro**.  
  
5.  Nella casella **Nome** immettere un nome descrittivo che renda il progetto facilmente identificabile.  
  
6.  Nella casella **Percorso** immettere la directory nella quale si desidera salvare il progetto o fare clic su **Sfoglia** per passare a tale directory.  
  
7.  Nella casella **Soluzione** immettere il nome per la nuova soluzione.Fare clic su **OK** per creare l'applicazione.  
  
    > [!NOTE]
    >  Se si desidera aggiungere un'applicazione console del flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e selezionare **Aggiungi**, quindi **Nuovo progetto** per aprire la finestra di dialogo **Nuovo progetto**.Procedere come descritto sopra in questa procedura.  
  
8.  Il modello di progetto crea una definizione del flusso di lavoro in XAML mentre la definizione dell'applicazione console è in codice sorgente.In [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] verrà visualizzata l'area di disegno per il flusso di lavoro creato.  
  
9. Per creare un flusso di lavoro, trascinare attività o altri elementi del flusso di lavoro dalla **Casella degli strumenti** nell'area di progettazione nel flusso di lavoro.  
  
## Vedere anche  
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)