---
title: "Procedura: esaminare il modello di contenuto dei nodi tramite la visualizzazione modello di contenuto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura: esaminare il modello di contenuto dei nodi tramite la visualizzazione modello di contenuto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene descritto come esaminare i nodi utilizzando [Visualizzazione modello di contenuto](../xml-tools/content-model-view.md).  
  
### Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto  
  
1.  Creare un nuovo file XML Schema.  
  
2.  Fare clic su **Utilizzare l'editor XML per visualizzare e modificare il file di XML Schema sottostante** nella visualizzazione iniziale.  
  
3.  Copiare il codice di esempio XML Schema da [XML Schema di esempio: schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md) e incollarlo per sostituire il codice aggiunto per impostazione predefinita al nuovo file XSD.  
  
4.  Selezionare l'elemento `purchaseOrder` in Schema Explorer facendo clic con il pulsante destro del mouse sull'elemento `purchaseOrder` nell'editor XML e selezionando **Mostra in XML Explorer**.  
  
5.  Fare clic con il pulsante destro del mouse su `purchaseOrder` in XML Explorer e selezionare **Mostra nella visualizzazione modello di contenuto**.  
  
     Nella visualizzazione modello di contenuto viene visualizzato l'elemento `purchaseOrder` sulla relativa area di progettazione.  
  
6.  Espandere i nodi `shipTo`, `billTo` e `items` facendo doppio clic su ogni nodo o facendo clic sulla doppia freccia a destra di ogni nodo.  
  
     I nodi dell'elemento `purchaseOrder` ora sono espansi ed è possibile visualizzare il modello di contenuto dell'elemento.  
  
7.  Fare clic su qualsiasi nodo nell'elemento `purchaseOrder` e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.  
  
8.  Fare clic sul pulsante **Mostra documentazione** nella barra degli strumenti XSD per attivare o disattivare la documentazione.È anche possibile fare clic con il pulsante destro del mouse sull'area di progettazione per attivare o disattivare la documentazione.  
  
9. Fare clic con il pulsante destro del mouse sul nodo `purchaseOrder` e selezionare **Genera XML di esempio** per visualizzare il documento di istanza XML.