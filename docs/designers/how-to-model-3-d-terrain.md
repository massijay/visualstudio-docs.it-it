---
title: "Procedura: Modellare un modello tridimensionale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 17
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: Modellare un modello tridimensionale
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo documento viene illustrato come utilizzare Editor di modello per creare un modello di campo 3D.  
  
 In questo documento vengono illustrate queste attività:  
  
-   Aggiunta di oggetti a una scena  
  
-   Selezionare le facce e i punti  
  
-   Traslare le selezioni  
  
-   Mediante lo strumento **Suddividere la faccia**  
  
-   Aggiunta di un frame a un oggetto nell'area di progettazione  
  
## Creazione di un modello di terreno tridimensionale  
 È possibile creare un campo tridimensionale suddividendo un piano per creare le facce aggiuntive, quindi modificando i vertici per creare caratteristiche di campo interessanti.  
  
 Al termine, il modello dovrebbe risultare simile al seguente:  
  
 ![Scena 3D che illustra un modello di terreno](~/designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 Prima di iniziare, assicurarsi che la finestra **Proprietà** e la **casella degli strumenti** siano visualizzate.  
  
#### Per creare un modello di campo tridimensionale  
  
1.  Creare un modello tridimensionale da utilizzare.  Per informazioni su come aggiungere un modello al progetto, vedere la sezione della Guida introduttiva in [Editor modello](../designers/model-editor.md).  
  
2.  Aggiungere un piano alla scena.  Nella **Casella degli strumenti** in **Forme** selezionare **Piano** e spostarlo nell'area di progettazione.  
  
    > [!TIP]
    >  Per semplificare l'utilizzo dell'oggetto piano, è possibile inserirlo in un frame nell'area di progettazione.  In modalità **Seleziona** selezionare l'oggetto piano, quindi sulla barra degli strumenti Editor modello scegliere il pulsante **Oggetto frame**.  
  
3.  Immettere la modalità di selezione icona.  Sulla barra degli strumenti di Editor di modello, scegliere **Seleziona faccia**.  
  
4.  Suddividere il piano.  In modalità selezione della faccia, selezionare una volta il piano per attivarlo per la selezione e quindi selezionarlo ancora per selezionare la sua faccia.  Sulla barra degli strumenti di Editor di modello, scegliere **Suddividere faccia**.  Per aggiungere nuovi vertici al piano che la dividano in quattro parti uguali.  
  
5.  Creare ulteriori suddivisioni.  Con i nuovi volti ancora selezionati, selezionare due volte ancora **Suddividere la faccia**.  Viene così creato un totale di 64 facce.  Creando più suddivisioni, è possibile fornire al terreno maggiore dettaglio.  
  
6.  Immettere la modalità di selezione punto.  Sulla barra degli strumenti di Editor di modello, scegliere **Seleziona punto**.  
  
7.  Modificare un punto per creare una funzionalità di campo.  In modalità Seleziona punto, selezionare uno dei punti quindi sulla barra degli strumenti Editor di modello, scegliere lo strumento **Traslazione**.  Nell'area di progettazione verrà visualizzata una casella che rappresenta il punto.  Utilizzare la freccia verde per spostare la casella, quindi modificare l'altezza del punto.  Ripetere questo passaggio per i punti diversi per creare funzionalità interessanti del campo.  
  
    > [!TIP]
    >  È possibile selezionare vari punti contemporaneamente per modificarli in modo uniforme.  
  
 Il modello di campo è completo.  Di seguito viene nuovamente mostrato il modello finale, con applicata l'ombreggiatura di Phong:  
  
 ![Scena 3D che illustra un modello di terreno](~/designers/media/digit-terrain-model.png "Digit\-Terrain\-Model")  
  
 È possibile utilizzare questo modello di campo per visualizzare l'effetto dello shader sfumato descritta in [Procedura: Creare uno shader con sfumatura basata sulla geometria](../designers/how-to-create-a-geometry-based-gradient-shader.md).  
  
## Vedere anche  
 [Editor modello](../designers/model-editor.md)