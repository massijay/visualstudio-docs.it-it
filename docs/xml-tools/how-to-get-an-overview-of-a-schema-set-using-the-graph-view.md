---
title: "Procedura: ottenere una panoramica di un set di schemi tramite la visualizzazione grafico | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# Procedura: ottenere una panoramica di un set di schemi tramite la visualizzazione grafico
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene descritto come utilizzare la [visualizzazione grafico](../xml-tools/graph-view.md) per ottenere una visualizzazione di alto livello dei nodi in un set di schemi e delle relazioni tra i nodi.  
  
### Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto  
  
1.  Creare un nuovo file XML Schema e salvare il file come Relationships.xsd.  
  
2.  Fare clic sul collegamento **Utilizzare l'editor XML per visualizzare e modificare il file di XML Schema sottostante** nella visualizzazione iniziale.  
  
3.  Copiare il codice di esempio XML Schema da [XML Schema di esempio: relazioni](../xml-tools/sample-xsd-file-relationships.md) e incollarlo per sostituire il codice aggiunto per impostazione predefinita al nuovo file XSD.  
  
4.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML e selezionare **Progettazione visualizzazioni**.  
  
5.  Selezionare la visualizzazione grafico dalla barra degli strumenti XSD.  
  
6.  Selezionare il nodo **Set di schemi** in XML Schema Explorer e trascinarlo nell'area di progettazione della visualizzazione grafico.Dovrebbero essere visualizzati i nodi globali e le frecce che collegano i nodi tra cui intercorrono relazioni.  
  
     ![Visualizzazione grafico](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Fare clic su qualsiasi nodo nell'area di progettazione e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.  
  
8.  Fare clic con il pulsante destro del mouse su qualsiasi nodo dell'elemento nell'area di progettazione e selezionare **Genera XML di esempio** per visualizzare il documento di istanza XML.