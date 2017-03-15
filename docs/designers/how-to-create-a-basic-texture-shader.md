---
title: "Procedura: Creare uno shader con trama di base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
caps.latest.revision: 23
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 23
---
# Procedura: Creare uno shader con trama di base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo documento viene illustrato come utilizzare la finestra di Progettazione shader e il linguaggio DGSL per creare uno shader di trama singola.  Questo shader imposta il colore finale direttamente sui valori RGB e alfa che vengono campionati dalla trama.  
  
 In questo documento vengono illustrate queste attività:  
  
-   Rimozione di nodi da un grafico shader  
  
-   Aggiunta di nodi a un grafico  
  
-   Impostare i parametri dello shader  
  
-   Impostare il parametro di visibilità  
  
-   Connessione di nodi  
  
## Creazione di uno shader della trama di base  
 È possibile implementare uno shader a trama singola di base scrivendo i valori di colore e alfa di un esempio di trama direttamente nel colore di output finale.  
  
 Prima di iniziare, assicurarsi che la finestra **Proprietà** e la **casella degli strumenti** siano visualizzate.  
  
#### Per creare uno shader di trama di base  
  
1.  Creare uno shader DGSL da utilizzare.  Per informazioni su come aggiungere uno shader DGSL al progetto, vedere la sezione della Guida introduttiva in [Finestra di progettazione shader](../designers/shader-designer.md).  
  
2.  Eliminare il nodo **Colore punto**.  In modalità **Seleziona** selezionare il nodo **Colore punto**, quindi nella barra dei menu scegliere **Modifica** ed **Elimina**.  In questo modo si crea lo spazio per il nodo che viene aggiunto nel passaggio successivo.  
  
3.  Aggiungere un nodo **Campione trama** al grafico.  Nella **Casella degli strumenti** in **Trama** selezionare **Campione trama** e spostarlo nell'area di progettazione.  
  
4.  Aggiungere un nodo **Coordinata trama** al grafico.  Nella **Casella degli strumenti** in **Trama** selezionare **Coordinata trama** e spostarla nell'area di progettazione.  
  
5.  Scegliere una trama da applicare.  In modalità **Seleziona**, selezionare il nodo **Campione trama**, quindi nella finestra **Proprietà**, specificare la trama da utilizzare tramite la proprietà **Nome file**.  
  
6.  Verificare che trama sia accessibile pubblicamente.  Selezionare il nodo **Campione trama**, quindi nella finestra **Proprietà** impostare la proprietà **Accesso** su **Pubblico**.  Ora è possibile impostare la trama da un altro strumento, come **Editor modello**.  
  
7.  Connettere le coordinate di trama all'esempio di trama.  In modalità **Seleziona** spostare il terminale **Output** del nodo **Coordinata trama** nel terminale **UV** il nodo **Campione trama**.  Questa connessione esegue la campionatura della trama in corrispondenza delle coordinate specificate.  
  
8.  Connettere l'esempio di trama al colore finale.  Spostare il terminale **RGB** del nodo **Campione trama** nel terminale **RGB** del nodo **Colore finale**, quindi spostare il terminale **Alfa** del nodo **Campione trama** nel terminale **Alfa** del nodo **Colore finale**.  
  
 Nella figura seguente viene mostrato il grafico di shader completato e un'anteprima dello shader applicato a un cubo.  
  
> [!NOTE]
>  In questa illustrazione, un piano viene utilizzato come forma di anteprima, e una trama è stata specificata per illustrare meglio l'effetto dello shader.  
  
 ![Grafico shader e anteprima del relativo effetto](../designers/media/digit-texture-effect.png "Digit\-Texture\-Effect")  
  
 Alcune forme potrebbero fornire anteprime ottimizzate per alcuni pixel.  Per ulteriori informazioni su come visualizzare in anteprima gli shader nella finestra di Progettazione shader, vedere [Finestra di progettazione shader](../designers/shader-designer.md).  
  
## Vedere anche  
 [Procedura: Applicare uno shader a un modello tridimensionale](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Editor immagini](../designers/image-editor.md)   
 [Finestra di progettazione shader](../designers/shader-designer.md)   
 [Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md)