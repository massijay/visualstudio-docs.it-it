---
title: "How to: Create a SharePoint Project Item Extension | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create a SharePoint Project Item Extension
  Creare un'estensione di elemento del progetto quando si desidera aggiungere la funzionalità a un elemento del progetto SharePoint già installato in Visual Studio.  Per ulteriori informazioni, vedere [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
### Per creare un'estensione di elemento del progetto  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Creare una classe che consente di implementare l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  
  
4.  Aggiungere gli attributi seguenti alla classe:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Questo attributo consente a Visual Studio di individuare e caricare l'implementazione dell'oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Passare il tipo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> al costruttore di attributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  In un'estensione di elemento del progetto, questo attributo consente di identificare l'elemento del progetto che si desidera estendere.  Passare l'ID dell'elemento di progetto al costruttore dell'attributo.  Per un elenco degli ID degli elementi di progetto inclusi in Visual Studio, vedere [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  Nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> utilizzare i membri del parametro *projectItemType* per definire il comportamento dell'estensione.  Questo parametro è un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> che fornisce accesso agli eventi definiti nelle interfacce <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>.  Per accedere a una specifica istanza del tipo di elemento di progetto da estendere, gestire eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>, quali <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come creare una semplice estensione per l'elemento del progetto Ricevitore di eventi.  Ogni volta che l'utente aggiunge un elemento del progetto Ricevitore di eventi in un progetto SharePoint, questa estensione scrive un messaggio nella finestra **Output** e nella finestra **Elenco errori**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemextension.vb#1)]  
  
 In questo esempio viene utilizzato il servizio del progetto SharePoint per scrivere il messaggio nella finestra **Output** e nella finestra **Elenco errori**.  Per ulteriori informazioni, vedere [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilazione del codice  
 In questo esempio sono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  