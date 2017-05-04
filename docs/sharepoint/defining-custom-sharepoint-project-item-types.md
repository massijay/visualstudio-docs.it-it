---
title: "Defining Custom SharePoint Project Item Types | Microsoft Docs"
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
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Defining Custom SharePoint Project Item Types
  Definire un nuovo tipo di elemento di progetto SharePoint quando si desidera creare un nuovo genere di elemento di progetto SharePoint.  Ad esempio, Visual Studio non include gli elementi di progetto SharePoint per l'aggiunta di campi o azioni personalizzate a un sito di SharePoint.  È possibile definire tipi personalizzati di elementi di progetto SharePoint per la creazione di campi, azioni personalizzate o altri tipi di componenti di SharePoint.  
  
## Attività per la definizione di tipi di elementi di progetto SharePoint  
 Per definire un tipo di elemento di progetto personalizzato, compilare un assembly di Visual Studio Extension che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  Per ulteriori informazioni, vedere [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Quando si definisce un tipo di elemento di progetto personalizzato, è possibile aggiungervi la seguente funzionalità.  
  
-   Aggiungere una voce di menu di scelta rapida a un elemento di progetto.  La voce di menu viene visualizzata quando si apre il menu di scelta rapida per l'elemento di progetto in **Esplora soluzioni** fare clic con il pulsante destro del mouse sull'elemento di progetto o scegliendolo e scegliendo lo spostamento \+ chiavi F10.  Per ulteriori informazioni, vedere [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Aggiungere una proprietà personalizzata all'elemento di progetto.  La proprietà viene visualizzata nella finestra **Proprietà** quando si seleziona l'elemento di progetto in **Esplora soluzioni**.  Per ulteriori informazioni, vedere [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Per consentire ad altri sviluppatori di utilizzare l'elemento di progetto in Visual Studio, creare un file con estensione spdata e un modello di elemento o un modello di progetto associato all'elemento di progetto.  Per ulteriori informazioni, vedere [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Informazioni sulla relazione tra tipi di elementi di progetto e istanze di elementi di progetto  
 Quando si definisce un tipo di elemento di progetto SharePoint, l'estensione viene caricata in Visual Studio quando un elemento di progetto del tipo associato viene aggiunto a un progetto SharePoint.  Ad esempio, se si definisce un nuovo tipo di elemento di progetto **Azione personalizzata**, l'estensione viene caricata in Visual Studio quando un utente aggiunge un elemento di progetto **Azione personalizzata** a un progetto.  In Visual Studio viene utilizzata la stessa istanza dell'estensione per tutte le istanze del tipo di elemento di progetto associato.  Nell'esempio precedente se l'utente aggiunge al progetto un secondo elemento di progetto **Azione personalizzata**, per personalizzare il secondo elemento di progetto verrà utilizzata la stessa istanza dell'estensione.  
  
 Per accedere a una specifica istanza del tipo di elemento di progetto personalizzato, gestire uno degli eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> del parametro *projectItemTypeDefinition* nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Ad esempio per determinare quando un elemento di progetto del tipo personalizzato viene aggiunto a un progetto, gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>.  Per ulteriori informazioni, vedere [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Vedere anche  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  