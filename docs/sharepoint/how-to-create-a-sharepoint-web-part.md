---
title: "Procedura: creare una web part di SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Web part [sviluppo per SharePoint in Visual Studio], aggiunta"
  - "Web part [sviluppo per SharePoint in Visual Studio], creazione"
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Procedura: creare una web part di SharePoint
  È possibile creare e personalizzare una Web part aggiungendo un elemento **Web part** a qualsiasi progetto SharePoint e modificando manualmente o tramite una finestra di progettazione il file di codice della Web part.  Per ulteriori informazioni, vedere [Procedura: creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### Per creare una web part di SharePoint  
  
1.  Aprire o creare un progetto SharePoint.  
  
     Per ulteriori informazioni, vedere [Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Selezionare il nodo del progetto SharePoint in **Esplora soluzioni** e scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento**, espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
4.  Nell'elenco di modelli di SharePoint, scegliere **Web part**.  
  
5.  Nella casella **Nome** specificare un nome per l'elemento web part, quindi fare click sul pulsante **Aggiungi**.  
  
     L'elemento web part verrà visualizzato in **Esplora soluzioni**.  Per ulteriori informazioni sui file inclusi in una web part, fare riferimento a [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  In **Esplora soluzioni**, aprire il file di codice della Web part appena creato.  
  
     Se ad esempio il nome della propria web part è WebPart1, aprire WebPart1.vb \(in Visual Basic\) o WebPart1.cs \(in C\#\).  
  
7.  Nel file di codice, aggiungere controlli al metodo <xref:System.Web.UI.Control.CreateChildControls%2A>.  
  
     Per un esempio, vedere [Procedura dettagliata: creazione di una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## Vedere anche  
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Procedura: creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procedura dettagliata: creazione di una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Procedura dettagliata: creazione di una web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  