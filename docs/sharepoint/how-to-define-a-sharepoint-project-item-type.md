---
title: "How to: Define a SharePoint Project Item Type | Microsoft Docs"
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
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# How to: Define a SharePoint Project Item Type
  Definire un tipo di elemento di progetto quando si desidera creare un elemento di progetto SharePoint personalizzato.  Per ulteriori informazioni, vedere [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### Per definire un tipo di elemento di progetto  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Creare una classe che consente di implementare l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  
  
4.  Aggiungere gli attributi seguenti alla classe:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Questo attributo consente a Visual Studio di individuare e caricare l'implementazione dell'oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  Passare il tipo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> al costruttore di attributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  In una definizione del tipo di elemento di progetto, questo attributo consente di specificare l'identificatore di stringa per il nuovo elemento di progetto.  È consigliabile utilizzare il formato *nome società*.*nome funzionalità* per assicurarsi che tutti gli elementi di progetto dispongano di un nome univoco.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>.  Questo attributo consente di specificare l'icona da visualizzare per questo elemento di progetto in **Esplora soluzioni**.  Questo attributo è facoltativo; se non viene applicato alla classe, Visual Studio consente di visualizzare un'icona predefinita per l'elemento di progetto.  Se si imposta questo attributo, passare il nome completo di un'icona o bitmap incorporata nell'assembly.  
  
5.  Nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> utilizzare i membri del parametro *projectItemTypeDefinition* per definire il comportamento del tipo di elemento di progetto.  Questo parametro è un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> che fornisce accesso agli eventi definiti nelle interfacce <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>.  Per accedere a una specifica istanza del tipo di elemento di progetto personalizzato, gestire eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>, quali <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come definire un semplice tipo di elemento di progetto.  Con questo tipo di elemento di progetto viene scritto un messaggio nella finestra **Output** e nella finestra **Elenco errori** quando un utente aggiunge un elemento di progetto di questo tipo a un progetto.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemtype.cs#2)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemtype.vb#2)]  
  
 In questo esempio viene utilizzato il servizio del progetto SharePoint per scrivere il messaggio nella finestra **Output** e nella finestra **Elenco errori**.  Per ulteriori informazioni, vedere [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilazione del codice  
 In questo esempio sono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Distribuzione dell'elemento di progetto  
 Per consentire ad altri sviluppatori di utilizzare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto.  Per ulteriori informazioni, vedere [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Per distribuire l'elemento di progetto, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly, il modello e qualsiasi altro file che si desidera distribuire con l'elemento di progetto.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  