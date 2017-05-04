---
title: "How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension
  È possibile aggiungere una voce di menu di scelta rapida a un elemento di progetto SharePoint esistente utilizzando un'estensione di elemento di progetto.  La voce di menu viene visualizzata quando un utente fa clic con il pulsante destro del mouse sull'elemento di progetto in **Esplora soluzioni**.  
  
 I passaggi seguenti presuppongono che sia già stata creata un'estensione di elemento di progetto.  Per ulteriori informazioni, vedere [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### Per aggiungere una voce di menu di scelta rapida in un'estensione di elemento di progetto  
  
1.  Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> dell'implementazione di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>, gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> del parametro *projectItemType*.  
  
2.  Nel gestore eventi dell'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> aggiungere un nuovo oggetto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> alla raccolta <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> del parametro degli argomenti dell'evento.  
  
3.  Nel gestore eventi <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> del nuovo oggetto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> effettuare le attività da eseguire quando un utente fa clic sulla voce del menu di scelta rapida.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta rapida all'elemento di progetto Ricevitore di eventi.  Quando l'utente fa clic con il pulsante destro del mouse sull'elemento di progetto in **Esplora soluzioni** e seleziona la voce di menu **Write Message to Output Window**, in Visual Studio viene visualizzato un messaggio nella finestra **Output**.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionmenu.vb#1)]  
  
 In questo esempio viene utilizzato il servizio di progetto SharePoint per scrivere il messaggio nella finestra **Output**.  Per ulteriori informazioni, vedere [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilazione del codice  
 Per questo esempio è necessario un progetto Libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  