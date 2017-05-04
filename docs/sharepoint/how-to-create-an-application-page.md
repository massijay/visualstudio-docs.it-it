---
title: "Procedura: creare una pagina applicazione | Microsoft Docs"
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
  - "pagine applicazione [sviluppo per SharePoint in Visual Studio], aggiunta"
  - "pagine applicazione [sviluppo per SharePoint in Visual Studio], creazione"
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Procedura: creare una pagina applicazione
  È possibile creare una pagina Web ASP.NET per uno o più siti SharePoint.  In SharePoint queste pagine sono dette pagine applicazione.  A differenza di una pagina di sito, in una pagina applicazione è contenuto code\-behind eseguito nella pagina.  Per ulteriori informazioni, vedere [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### Per creare una pagina applicazione  
  
1.  Aprire o creare un progetto SharePoint in Visual Studio.  
  
     Per ulteriori informazioni, vedere [Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Scegliere il nodo di progetto in **Esplora soluzioni**.  
  
3.  Sulla barra dei menu scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
4.  Nella finestra di dialogo **Aggiungi nuovo elemento**, espandere il nodo **SharePoint**, quindi scegliere l'elemento **2010**.  
  
5.  Nell'elenco di modelli SharePoint, scegliere **Pagina applicazione**.  
  
6.  Nella casella **Nome** specificare un nome per la pagina applicazione, quindi scegliere il pulsante **Aggiungi**.  
  
     In Visual Studio verranno aggiunti al progetto alcuni file e cartelle.  Per ulteriori informazioni su questi file, vedere [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     Nella visualizzazione **Origine** della finestra di progettazione di Visual Web Developer, viene visualizzato il file di pagina ASP.NET.  È possibile progettare la pagina aggiungendo i controlli dalla **Casella degli strumenti** e collocandoli nei segnaposti del contenuto.  Per ulteriori informazioni, vedere [Visualizzazione Origine, Progettazione pagine Web](http://msdn.microsoft.com/it-it/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Se si vuole gestire gli eventi del controllo, aggiungere il codice al file di codice per la pagina dell'applicazione.  
  
     Il file di codice viene visualizzato se si espande il nodo per il file della pagina ASP.NET e ha un'estensione .cs o .vb, a seconda del linguaggio del progetto.  Per un esempio end\-to\-end relativo a come creare una pagina applicazione, vedere [Procedura dettagliata: creazione di una pagina di un'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## Vedere anche  
 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/it-it/9c31f93b-c8fb-4599-9b14-6194ec8c7539)   
 [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Procedura dettagliata: creazione di una pagina di un'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  