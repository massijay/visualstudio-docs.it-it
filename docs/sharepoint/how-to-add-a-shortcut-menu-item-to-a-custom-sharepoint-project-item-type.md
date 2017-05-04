---
title: "How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type | Microsoft Docs"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile aggiungere una voce di menu di scelta rapida all'elemento di progetto.  La voce di menu viene visualizzata quando un utente fa clic con il pulsante destro del mouse sull'elemento di progetto in **Esplora soluzioni**.  
  
 I passaggi seguenti presuppongono che sia già stato definito il tipo di elemento di progetto SharePoint personalizzato.  Per ulteriori informazioni, vedere [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### Per aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto personalizzato  
  
1.  Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> dell'implementazione di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> del parametro *projectItemTypeDefinition*.  
  
2.  Nel gestore eventi dell'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> aggiungere un nuovo oggetto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> alla raccolta <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> del parametro degli argomenti dell'evento.  
  
3.  Nel gestore eventi <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> per il nuovo oggetto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>, eseguire le attività da eseguire quando un utente sceglie la voce di menu di scelta rapida.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto personalizzato.  Quando l'utente apre il menu di scelta rapida l'elemento di progetto in **Esplora soluzioni** e sceglie la voce di menu **Scrivi messaggio su finestra di output**, verrà visualizzato un messaggio nella finestra **Output**.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypemenu.vb#4)]  
  
 In questo esempio viene utilizzato il servizio di progetto SharePoint per scrivere il messaggio nella finestra **Output**.  Per ulteriori informazioni, vedere [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilazione del codice  
 Per questo esempio è necessario un progetto Libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Distribuzione dell'elemento di progetto  
 Per consentire ad altri sviluppatori di utilizzare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto.  Per ulteriori informazioni, vedere [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Per distribuire l'elemento di progetto, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly, il modello e qualsiasi altro file che si desidera distribuire con l'elemento di progetto.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  