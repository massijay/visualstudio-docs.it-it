---
title: "Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Method_Details"
  - "VS.SharePointTools.BDC.Explorer"
  - "VS.SharePointTools.BDC.Diagram"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Esplora integrazione applicativa dei dati"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], finestra di progettazione"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dettagli metodo"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], strumenti visivi"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Esplora integrazione applicativa dei dati"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], finestra di progettazione"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dettagli metodo"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], strumenti visivi"
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati
  È possibile progettare un modello di integrazione applicativa dei dati tramite la finestra di progettazione dell'integrazione applicativa dei dati, la finestra **Dettagli metodo di integrazione applicativa dei dati** e tramite **Esplora integrazione applicativa dei dati**.  
  
 **Esplora integrazione applicativa dei dati** consente di esplorare il modello, eseguire ricerche nel modello e definire descrittori di tipo.  
  
## Finestra di progettazione BDC  
 La finestra di progettazione dell'integrazione applicativa dei dati consente di definire le entità nel modello e disporre visivamente le relazioni tra di esse.  Utilizzare la finestra di progettazione dell'integrazione applicativa dei dati per portare a termine le attività seguenti:  
  
-   Aggiungere entità al modello.  
  
-   Rimuovere entità dal modello.  
  
-   Definire associazioni tra entità.  
  
 Per aprire la Finestra di progettazione dell'integrazione applicativa dei dati, fare doppio clic sul file modello nel progetto, o aprire il menu di scelta rapida per il file di modello e quindi scegliere **Apri**.  Aggiungere un'entità al modello trascinando o copiando una **Entità** dalla **Casella degli strumenti** alla finestra di progettazione.  Per creare un'associazione tra due entità, seleziona il controllo **Gruppo associazioni** nella **Casella degli strumenti**, selezionare la prima entità, quindi selezionare la seconda entità.  
  
## Finestra Dettagli metodo di integrazione applicativa dei dati  
 Utilizzare la finestra **Dettagli metodo di integrazione applicativa dei dati** per definire i parametri, le istanze e descrittori di filtro di un metodo.  
  
 È possibile generare rapidamente metodi Finder, Finder specifico, Creator, Updater e Deleter nella finestra **Dettagli metodo di integrazione applicativa dei dati**.  Quando si generano questi metodi, in Visual Studio vengono aggiunti al metodo metadati, ad esempio parametri, istanze e descrittori di tipo.  È possibile modificare questi metadati per soddisfare le esigenze dello scenario specifico.  
  
 Per aprire la finestra **Dettagli metodo di integrazione applicativa dei dati**, scegliere **Visualizza**, **Altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
 Per visualizzare i metodi nella finestra **Dettagli metodo di integrazione applicativa dei dati**, selezionare l'entità nella Finestra di progettazione dell'integrazione applicativa dei dati.  I metodi dell'entità selezionata vengono visualizzati nella finestra **Dettagli metodo di integrazione applicativa dei dati**.  Se non si seleziona un'entità nella Finestra di progettazione dell'integrazione applicativa dei dati, nella finestra **Dettagli metodo di integrazione applicativa dei dati** non verranno visualizzate informazioni.  
  
 Espandere o comprimere nodi nella finestra **Dettagli metodo di integrazione applicativa dei dati** per definire i parametri, le istanze e descrittori di filtro.  Utilizzare **Esplora integrazione applicativa dei dati** per definire descrittori di tipo.  
  
## Esplora integrazione applicativa dei dati  
 In **Esplora integrazione applicativa dei dati** vengono visualizzati gli elementi che costituiscono il modello.  Per aprire **Esplora integrazione applicativa dei dati**, sulla barra dei menu, scegliere **Visualizza**, **Altre finestre**, **Esplora integrazione applicativa dei dati**.  Per esplorare il modello, espandere i nodi in **Esplora integrazione applicativa dei dati**.  Ogni nodo rappresenta un elemento nell'XML del file modello.  
  
 Mentre si selezionano nodi in **Esplora integrazione applicativa dei dati**, le proprietà di ogni nodo che sono state selezionate vengo visualizzate nella finestra **Proprietà**.  Molte di queste proprietà corrispondono agli attributi contenuti nel file modello.  È possibile eseguire ricerche nel modello tramite la casella di ricerca nella parte superiore di **Esplora integrazione applicativa dei dati**.  
  
> [!NOTE]  
>  In **Esplora integrazione applicativa dei dati** non vengono visualizzati identificatori, proprietà personalizzate, stringhe localizzate, gruppi di associazioni, azioni, descrittori di filtro, elenchi di controllo di azioni e valori di parametro predefiniti.  
  
### Definizione di descrittori di tipo  
 Utilizzare **Esplora integrazione applicativa dei dati** per definire descrittori di tipo.  In Esplora integrazione applicativa dei dati è possibile definire un descrittore di tipo una sola volta e riutilizzarlo in altre parti del modello.  A questo scopo, copiare un descrittore di tipo e incollarlo in qualsiasi altro parametro o descrittore di tipo.  
  
> [!NOTE]  
>  Le modifiche apportate a un descrittore di tipo originale non influiscono sulle relative copie.  
  
 Per ulteriori informazioni, vedere [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## Vedere anche  
 [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)   
 [Procedura: aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)   
 [Procedura dettagliata: creazione di un elenco esterno in SharePoint tramite il servizio di integrazione applicativa dei dati](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  