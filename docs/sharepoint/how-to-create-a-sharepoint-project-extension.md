---
title: "How to: Create a SharePoint Project Extension | Microsoft Docs"
ms.custom: ""
ms.date: "04/28/2017"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# How to: Create a SharePoint Project Extension
  Creare un'estensione di progetto quando si desidera aggiungere la funzionalità a qualsiasi progetto SharePoint aperto in Visual Studio.  Per ulteriori informazioni, vedere [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### Per creare un'estensione di progetto  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Creare una classe che consente di implementare l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  
  
4.  Aggiungere l'oggetto <xref:System.ComponentModel.Composition.ExportAttribute> alla classe.  Questo attributo consente a Visual Studio di individuare e caricare l'implementazione di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Passare il tipo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> al costruttore dell'attributo.  
  
5.  Nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> utilizzare i membri del parametro *projectService* per definire il comportamento dell'estensione.  Questo parametro è un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> che fornisce accesso agli eventi definiti nell'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come creare un'estensione di progetto semplice che gestisce la maggior parte degli eventi del progetto SharePoint definiti dall'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>.  Per testare il codice, creare un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], quindi aggiungere più progetti alla soluzione, modificare i valori di proprietà del progetto oppure eliminare o escludere un progetto.  L'estensione notifica gli eventi mediante la visualizzazione di messaggi nelle finestre **Output** ed **Elenco errori**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectextension.cs#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectextension.vb#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/savedatatoprojectfile.vb#3)]  
  
 In questo esempio viene utilizzato il servizio del progetto SharePoint per scrivere il messaggio nella finestra **Output** e nella finestra **Elenco errori**.  Per ulteriori informazioni, vedere [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Per esempi che illustrano come gestire gli eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>, vedere [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) e [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
## Compilazione del codice  
 In questo esempio sono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
  
  