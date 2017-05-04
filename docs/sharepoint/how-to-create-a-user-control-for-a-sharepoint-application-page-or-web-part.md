---
title: "Procedura: creare un controllo utente per una web part o una pagina applicazione di SharePoint | Microsoft Docs"
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
  - "controlli utente [sviluppo per SharePoint in Visual Studio], aggiunta"
  - "controlli utente [sviluppo per SharePoint in Visual Studio], creazione"
ms.assetid: 492ea376-7188-4b5a-a2eb-adc0e3f51484
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: creare un controllo utente per una web part o una pagina applicazione di SharePoint
  È possibile creare controlli utente personalizzati che forniscono funzionalità personalizzate per la propria soluzione SharePoint ed è possibile riutilizzare tale funzionalità all'interno del proprio progetto.  È possibile includere i controlli utente in una web part o in una pagina di applicazione, aggiungere altri controlli ASP.NET e di SharePoint, e definire proprietà e metodi per il controllo.  Per ulteriori informazioni sui controlli utente, vedere [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) e [Controlli utente e controlli server in SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### Per creare un controllo utente per SharePoint  
  
1.  Aprire o creare un progetto SharePoint in Visual Studio.  
  
     Vedere [Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Scegliere il nodo di progetto in **Esplora soluzioni**.  
  
3.  Nella barra dei menu, scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.  
  
4.  Nel riquadro **Installato**, selezionare il nodo **Office\/SharePoint**.  
  
5.  Nell'elenco di modelli di SharePoint, scegliere **Controllo utente \(solo soluzione farm\)**.  
  
    > [!NOTE]  
    >  I controlli utente possono essere utilizzati solo nelle soluzioni della farm.  
  
6.  Nella casella **Nome** specificare un nome per il controllo utente, quindi scegliere il pulsante **Aggiungi**.  
  
     In Visual Studio verranno aggiunti al progetto alcuni file e cartelle.  Per ulteriori informazioni su questi file, vedere [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Per impostazione predefinita, il file del controllo utente viene riprodotto nella visualizzazione **Origine** della finestra di progettazione di Visual Web Developer.  In questa visualizzazione, è possibile modificare il markup XML del controllo.  Passare alla visualizzazione **Progettazione** se si desidera progettare visivamente il controllo trascinando i controlli dalla **Casella degli strumenti**.  Vedere [NIB: Design View, Web Page Designer](http://msdn.microsoft.com/it-it/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Se si desidera gestire eventi che si verificano nel controllo, aggiungere codice al file di codice del controllo utente.  
  
     Il file viene visualizzato in **Esplora soluzioni** nel file di controllo utente e ha un'estensione .cs o .vb, a seconda del linguaggio del progetto.  
  
## Vedere anche  
 [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  