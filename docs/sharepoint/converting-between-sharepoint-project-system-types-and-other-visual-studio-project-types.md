---
title: "Converting Between SharePoint Project System Types and Other Visual Studio Project Types | Microsoft Docs"
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
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Converting Between SharePoint Project System Types and Other Visual Studio Project Types
  In alcuni casi si dispone di un oggetto nel sistema di progetto SharePoint e si desidera utilizzare le funzionalità di un oggetto corrispondente nel modello a oggetti di automazione o di integrazione di Visual Studio o viceversa.  In questi casi, è possibile utilizzare il metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> del servizio di progetto SharePoint per convertire l'oggetto in un oggetto di un altro modello a oggetti.  
  
 Si consideri ad esempio il caso in cui si dispone di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> ma si desidera utilizzare metodi disponibili soltanto in un oggetto <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  In tal caso, è possibile utilizzare il metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> per convertire l'oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> in un oggetto <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Per ulteriori informazioni sui modelli a oggetti di automazione e di integrazione di Visual Studio, vedere [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Tipi di conversioni  
 Nella tabella seguente vengono elencati i tipi che questo metodo consente di convertire tra il sistema di progetto SharePoint e gli altri modelli a oggetti di Visual Studio.  
  
|Tipo di sistema di progetto SharePoint|Tipi corrispondenti nei modelli a oggetti di automazione e di integrazione|  
|--------------------------------------------|--------------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> oppure<br /><br /> Qualsiasi interfaccia nel modello a oggetti di integrazione di Visual Studio che viene implementato dall'oggetto COM sottostante per il progetto.  Queste interfacce comprendono <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> \(o un'interfaccia derivata\) e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  Per un elenco delle interfacce principali che vengono implementate dai progetti, vedere [Componenti di base del modello di progetto](../extensibility/internals/project-model-core-components.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> oppure<br /><br /> Valore <xref:System.UInt32> \(anche denominato VSITEMID\) che consente di identificare il membro del progetto nell'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> in cui è contenuto.  Questo valore può essere passato al parametro *itemid* di alcuni metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.|  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come utilizzare il metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> per convertire un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> in un oggetto <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#2)]  
  
 L'esempio presenta i seguenti requisiti:  
  
-   Un'estensione del sistema del progetto di SharePoint che disponga di un riferimento all'assembly EnvDTE.dll.  Per ulteriori informazioni, vedere [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Codice che registra il metodo`projectService_ProjectAdded` per gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  Per un esempio, vedere [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## Vedere anche  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  