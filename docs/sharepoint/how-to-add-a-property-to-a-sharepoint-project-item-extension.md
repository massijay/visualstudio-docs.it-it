---
title: "How to: Add a Property to a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# How to: Add a Property to a SharePoint Project Item Extension
  È possibile utilizzare un'estensione di elemento di progetto per aggiungere una proprietà a qualsiasi elemento di progetto SharePoint già installato in Visual Studio.  La proprietà viene visualizzata nella finestra **Proprietà** quando l'elemento di progetto viene selezionato in **Esplora soluzioni**.  
  
 I passaggi seguenti presuppongono che sia già stata creata un'estensione di elemento di progetto.  Per ulteriori informazioni, vedere [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### Per aggiungere una proprietà a un'estensione di elemento di progetto  
  
1.  Definire una classe con una proprietà pubblica che rappresenta la proprietà da aggiungere a un tipo di elemento di progetto.  Per aggiungere più proprietà a un tipo di elemento di progetto, è possibile definire tutte le proprietà nella stessa classe o in classi diverse.  
  
2.  Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> dell'implementazione di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> del parametro *projectItemType*.  
  
3.  Nel gestore dell'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> aggiungere un'istanza della classe di proprietà alla raccolta <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> del parametro degli argomenti dell'evento.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come aggiungere una proprietà denominata **Example Property** all'elemento di progetto Ricevitore di eventi.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionproperty.vb#8)]  
  
### Informazioni sul codice  
 Per garantire che ogni volta che si verifica l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> venga utilizzata la stessa istanza della classe `CustomProperties`, nell'esempio di codice l'oggetto delle proprietà viene aggiunto alla proprietà <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> dell'elemento di progetto la prima volta che si verifica questo evento.  Il codice recupera questo oggetto ogni volta che si verifica di nuovo questo evento.  Per ulteriori informazioni sull'utilizzo della proprietà <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> per associare i dati agli elementi di progetto, vedere [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Per rendere persistenti le modifiche al valore della proprietà, la funzione di accesso **set** della proprietà `ExampleProperty` salva il nuovo valore nella proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> dell'oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> a cui è associata la proprietà.  Per ulteriori informazioni sull'utilizzo della proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> per rendere persistenti i dati con gli elementi di progetto, vedere [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Specifica del comportamento delle proprietà personalizzate  
 È possibile definire la modalità di visualizzazione e il comportamento di una proprietà personalizzata nella finestra **Proprietà** applicando alla definizione di proprietà gli attributi ottenuti dallo spazio dei nomi <xref:System.ComponentModel>.  Gli attributi seguenti sono utili in molti scenari:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: specifica il nome della proprietà visualizzata nella finestra **Proprietà**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: specifica la stringa descrittiva visualizzata nella parte inferiore della finestra **Proprietà** quando si seleziona la proprietà.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: specifica il valore predefinito della proprietà.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: specifica una conversione personalizzata tra la stringa visualizzata nella finestra **Proprietà** e un valore di proprietà non di tipo stringa.  
  
-   <xref:System.ComponentModel.EditorAttribute>: specifica un editor personalizzato da utilizzare per modificare la proprietà.  
  
## Compilazione del codice  
 Per questi esempi è necessario un progetto Libreria di classi con riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  