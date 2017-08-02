---
title: "Procedura: Modificare il punto pivot di un modello tridimensionale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 14
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: Modificare il punto pivot di un modello tridimensionale
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo documento viene illustrato come utilizzare l'editor di modello per modificare *il punto pivot* di un modello tridimensionale.  Il punto pivot è il punto nello spazio che definisce il centro matematico dell'oggetto per la rotazione e il ridimensionamento.  
  
 In questo documento viene illustrata questa attività:  
  
-   Modifica del punto di perno di un oggetto  
  
## Modificare il punto pivot di un modello 3D  
 È possibile ridefinire l'origine di un modello tridimensionale modificandone il punto pivot.  
  
 Verificare che le finestre **Proprietà** e **Casella degli strumenti** siano visualizzate.  
  
#### Per modificare il punto pivot di un modello tridimensionale  
  
1.  Iniziare con un modello tridimensionale esistente, come quello descritto in [Procedura: Creare un modello tridimensionale di base](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md).  
  
2.  Immettere la modalità perno.  Sulla barra degli strumenti **Modalità editor modello**, scegliere il pulsante **Modalità perno** per attivare la modalità perno.  Verrà visualizzata una casella intorno al pulsante **Modalità perno** per indicare che l'Editor modello è ora in modalità perno.  In modalità perno, le operazioni di traduzione influiscono sul punto di perno dell'oggetto anziché della struttura dell'oggetto nello spazio globale.  
  
3.  Modificare il punto di perno dell'oggetto.  In modalità **Seleziona** selezionare l'oggetto, quindi sulla barra degli strumenti **Visualizzatore modello** scegliere lo strumento **Traslazione**.  Nell'area di progettazione verrà visualizzata una casella che rappresenta il punto pivot.  Sposta la casella per modificare il punto di perno dell'oggetto.  
  
     Spostando la casella, è possibile spostare il punto pivot in tutte e tre le dimensioni.  Per traslare il punto pivot lungo un asse, spostare la freccia corrispondente a quell'asse.  La casella e le frecce diventano di colore giallo per indicare l'asse interessata dall'operazione di traslazione.  
  
     È inoltre possibile specificare il punto pivot utilizzando la proprietà **Conversione perno** nella finestra **Proprietà**.  
  
    > [!TIP]
    >  È possibile visualizzare l'effetto del nuovo punto pivot ruota l'oggetto.  Per ruotarlo, utilizzare lo strumento **Ruota** o modificare la proprietà **Rotazione**.  
  
 Qui un modello con punto pivot modificato:  
  
 ![Modello di casa con punto pivot modificato](~/docs/designers/media/digit-modified-model.png "Digit\-Modified\-Model")  
  
## Vedere anche  
 [Procedura: Creare un modello tridimensionale di base](../Topic/How%20to:%20Create%20a%20Basic%203-D%20Model.md)   
 [Editor modello](../designers/model-editor.md)