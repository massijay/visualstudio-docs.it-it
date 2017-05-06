---
title: "How to: Add a Shortcut Menu Item to SharePoint Projects"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Add a Shortcut Menu Item to SharePoint Projects
  È possibile aggiungere una voce di menu di scelta rapida a qualsiasi progetto SharePoint.  La voce di menu viene visualizzata quando un utente fa clic con il pulsante destro del mouse su un nodo di progetto in **Esplora soluzioni**.  
  
 Nei passaggi seguenti si suppone che sia già stata creata un'estensione di progetto.  Per ulteriori informazioni, vedere [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### Per aggiungere una voce di menu di scelta rapida ai progetti SharePoint  
  
1.  Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> dell'implementazione di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> del parametro *projectService*.  
  
2.  Nel gestore eventi dell'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> aggiungere un nuovo oggetto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> alla raccolta <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> del parametro degli argomenti dell'evento.  
  
3.  Nel gestore eventi <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> del nuovo oggetto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> effettuare le attività da eseguire quando un utente fa clic sulla voce del menu di scelta rapida.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta rapida ai nodi di progetto SharePoint in **Esplora soluzioni**.  Quando l'utente fa clic con il pulsante destro del mouse su un nodo di progetto e sceglie la voce di menu **Write Message to Output Window**, viene visualizzato un messaggio nella finestra **Output** di Visual Studio.  In questo esempio viene utilizzato il servizio di progetto SharePoint per visualizzare il messaggio.  Per ulteriori informazioni, vedere [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/vb/extension/projectitemextensionmenu.vb#1)]  
  
## Compilazione del codice  
 Per questo esempio è necessario un progetto Libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  