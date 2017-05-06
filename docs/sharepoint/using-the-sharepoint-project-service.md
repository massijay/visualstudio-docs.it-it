---
title: "Using the SharePoint Project Service"
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
helpviewer_keywords: 
  - "SharePoint project service"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: bfb6cbc7-6c28-4e1a-abb4-88f149e7712c
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Using the SharePoint Project Service
  Il sistema di progetti SharePoint include un servizio progetto che può essere usato per eseguire attività correlate al sistema di progetti.  Il servizio progetto è un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  
  
 È possibile accedere al servizio progetto di SharePoint in qualsiasi estensione degli strumenti di SharePoint.  È anche possibile accedervi in altri tipi di estensioni di Visual Studio, ad esempio i componenti aggiuntivi e i package VS.  Per altre informazioni, vedere [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## Funzionalità del servizio progetto  
 La tabella seguente elenca le attività che è possibile eseguire usando il servizio progetto di SharePoint e il metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> o la proprietà da usare per eseguire ogni attività.  
  
|Attività|Membro da usare|  
|--------------|---------------------|  
|Accesso a qualsiasi progetto SharePoint aperto in Visual Studio.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|  
|Accesso a tutti i tipi di elementi del progetto SharePoint disponibili \(inclusi i tipi di elementi incorporati e personalizzati del progetto\).|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|  
|Accesso a tutti i passaggi di distribuzione disponibili per i progetti SharePoint \(inclusi i passaggi di distribuzione incorporati e personalizzati\).|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|  
|Accesso agli eventi generati quando uno sviluppatore effettua il refactoring del codice in un progetto SharePoint.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|  
|Esecuzione di un *comando di SharePoint* personalizzato che consente di effettuare una chiamata nel modello a oggetti del server SharePoint.  Per altre informazioni sui comandi di SharePoint, vedere [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|  
|Conversione di un tipo del sistema del progetto SharePoint in un tipo del modello a oggetti di automazione o di integrazione di Visual Studio e viceversa.  Per altre informazioni, vedere [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|  
|Scrittura di messaggi nella finestra **Output** o nella finestra **Elenco errori** in Visual Studio.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|  
|Accesso ad altri servizi disponibili in Visual Studio.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|  
|Recupero del percorso della cartella di installazione del sito di SharePoint locale usato per il debug della soluzione.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|  
|Determinazione dell'installazione di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] o [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] nel computer.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|  
|Convalida di una funzionalità o un pacchetto in una soluzione SharePoint.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|  
  
## Vedere anche  
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Procedura: Ottenere un servizio dall'oggetto DTE](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  