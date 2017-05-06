---
title: "Associating Custom Data with SharePoint Tools Extensions"
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
  - "projects [SharePoint development in Visual Studio], associating custom data"
  - "project items [SharePoint development in Visual Studio], associating custom data"
  - "SharePoint project items, associating custom data"
  - "SharePoint projects, associating custom data"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Associating Custom Data with SharePoint Tools Extensions
  È possibile aggiungere dati personalizzati a determinati oggetti nelle estensioni degli strumenti di SharePoint.  Ciò si rivela utile quando si dispone di dati in una determinata parte dell'estensione a cui si desidera accedere da un'altra parte di codice dell'estensione in un secondo momento.  Anziché implementare un modo personalizzato per archiviare i dati e accedere a essi è possibile associare i dati a un oggetto nell'estensione e quindi recuperarli successivamente dallo stesso oggetto.  
  
 L'aggiunta di dati personalizzati agli oggetti risulta utile anche quando si desidera conservare i dati attinenti a un elemento specifico in Visual Studio.  Le estensioni degli strumenti di SharePoint vengono caricate solo una volta in Visual Studio. Di conseguenza, è possibile che l'estensione utilizzi in qualsiasi momento diversi elementi di vario tipo \(ad esempio progetti, elementi di progetto o nodi **Server Explorer**\).  Se si dispone di dati personalizzati attinenti solo a un elemento specifico, è possibile aggiungerli all'oggetto che lo rappresenta.  
  
 Quando si aggiungono dati personalizzati agli oggetti nelle estensioni degli strumenti di SharePoint, i dati non vengono conservati.  I dati sono disponibili solo per la durata dell'oggetto.  Dopo che l'oggetto viene recuperato dalla procedura di Garbage Collection, i dati verranno persi.  
  
 Nelle estensioni del sistema di progetto SharePoint è inoltre possibile salvare dati di tipo stringa che vengono conservati dopo lo scaricamento di un'estensione.  Per ulteriori informazioni, vedere [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Oggetti che possono contenere dati personalizzati  
 È possibile aggiungere dati personalizzati a qualsiasi oggetto nel modello a oggetti degli strumenti di SharePoint che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>.  Questa interfaccia definisce solo una proprietà, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, che rappresenta una raccolta di oggetti dati personalizzati.  I tipi seguenti implementano <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## Aggiunta e recupero di dati personalizzati  
 Per aggiungere dati personalizzati a un oggetto in un'estensione degli strumenti di SharePoint, ottenere la proprietà <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> dell'oggetto a cui si desidera aggiungere i dati, quindi utilizzare il metodo <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> per aggiungerli all'oggetto.  
  
 Per recuperare dati personalizzati da un oggetto in un'estensione degli strumenti di SharePoint, ottenere la proprietà <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> dell'oggetto, quindi utilizzare uno dei metodi seguenti:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>.  Questo metodo restituisce **true** se l'oggetto dati esiste oppure **false** se non esiste.  È possibile utilizzare questo metodo per recuperare istanze di tipi di valore o tipi di riferimento.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>.  Questo metodo restituisce l'oggetto dati se questo esiste. In caso contrario, restituisce **null**.  È possibile utilizzare questo metodo solo per recuperare istanze di tipi di riferimento.  
  
 Nell'esempio di codice seguente viene illustrato come stabilire se un determinato oggetto dati è già associato a un elemento di progetto.  Se l'oggetto dati non è già associato all'elemento di progetto, il codice aggiunge l'oggetto alla proprietà <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> dell'elemento di progetto.  Per vedere questo esempio nel contesto di un esempio più esaustivo, vedere [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#13)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#13)]  
  
## Vedere anche  
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)  
  
  