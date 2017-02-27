---
title: "Procedura: Applicare uno shader a un modello tridimensionale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 15
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 15
---
# Procedura: Applicare uno shader a un modello tridimensionale
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo documento viene illustrato come utilizzare l'Editor dei modello per applicare uno shader DGSL a un modello 3D.  
  
 In questo documento viene illustrata questa attività:  
  
-   Applicare uno shader a un modello tridimensionale  
  
## Applicare uno shader a un modello tridimensionale  
 È possibile applicare un effetto shader a un modello 3D per conferirgli un aspetto interessante.  
  
 Prima di iniziare, assicurarsi che la finestra **Proprietà** venga visualizzata.  
  
#### Per applicare uno shader a un modello tridimensionale  
  
1.  Iniziare con una scena tridimensionale che contiene uno o più modelli.  Se non si dispone di una scena tridimensionale appropriata, crearne una come descritto in [Procedura: Creare un modello tridimensionale di base](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md).  È inoltre necessario disporre di uno shader DGSL applicabile al modello.  Se non si dispone di uno shader appropriato, crearne uno come descritto in [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md) e verificare che sia stato salvato in un file prima di continuare.  
  
2.  In modalità **Seleziona**, selezionare il modello a cui si desidera applicare lo shader, quindi nella finestra **Proprietà**, nella proprietà **Nome file** del gruppo di proprietà **Effetto**, specificare lo shader DGSL che si desidera applicare al modello.  
  
 Di seguito è riportato un modello a cui è stato applicato l'effetto colore di base:  
  
 ![Scena 3D che illustra l'effetto colore di base](../designers/media/digit-3d-model-effect.png "Digit\-3D\-Model\-Effect")  
  
 Dopo avere applicato lo shader a un modello, è possibile aprirlo nella finestra di progettazione dello shader selezionando il modello, quindi nella finestra **Proprietà**, nella proprietà **\(Avanzate\)** del gruppo di proprietà **Effetto**, scegliere il pulsante con i puntini di sospensione \(**...**\).  
  
## Vedere anche  
 [Procedura: Creare un modello tridimensionale di base](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)   
 [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md)   
 [Editor modello](../designers/model-editor.md)   
 [Finestra di progettazione shader](../designers/shader-designer.md)