---
title: "Saving Data in Extensions of the SharePoint Project System | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint project items, saving string data"
  - "project items [SharePoint development in Visual Studio], saving string data"
  - "projects [SharePoint development in Visual Studio], saving string data"
  - "SharePoint projects, saving string data"
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Saving Data in Extensions of the SharePoint Project System
  Quando si estende il sistema di progetto SharePoint è possibile salvare dati di tipo stringa che vengono conservati dopo la chiusura di un progetto SharePoint.  I dati sono in genere associati a un elemento di progetto particolare o al progetto stesso.  
  
 Se si dispone di dati che non è necessario salvare in modo permanente, è possibile aggiungerli a qualsiasi oggetto nel modello a oggetti degli strumenti di SharePoint che implementa l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>.  Per ulteriori informazioni, vedere [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## Salvataggio di dati associati a un elemento di progetto  
 Quando si dispone di dati associati a un elemento del progetto SharePoint specifico, ad esempio il valore di una proprietà che si aggiunge a un elemento di progetto, è possibile salvare i dati nel file con estensione spdata per l'elemento di progetto.  Per effettuare questa operazione, utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>.  I dati aggiunti a questa proprietà vengono salvati nell'elemento **ExtensionData** nel file con estensione spdata dell'elemento di progetto.  Per ulteriori informazioni, vedere [ExtensionData Element](../sharepoint/extensiondata-element.md).  
  
 Nell'esempio di codice seguente viene illustrato come utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> per salvare il valore di una proprietà di tipo stringa definita in un tipo di elemento di progetto SharePoint personalizzato.  Per vedere questo esempio nel contesto di un esempio più esaustivo, vedere [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#14)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#14)]  
  
## Salvataggio di dati associati a un progetto  
 Quando si dispone di dati a livello di progetto, ad esempio il valore di una proprietà aggiunta ai progetti SharePoint, è possibile salvare i dati nel file di progetto \(con estensione csproj o vbproj\) o nel file delle opzioni utente del progetto \(il file csproj.user o vbproj.user\).  I file in cui si sceglie di salvare i dati dipende dalla modalità di utilizzo del dati desiderata:  
  
-   Se si desidera che i dati siano disponibili per tutti gli sviluppatori che aprono il progetto SharePoint, salvare i dati nel file di progetto.  Questo file viene sempre archiviato nei database del controllo del codice sorgente, in modo i dati presenti nel file siano a disposizione degli altri sviluppatori che estraggono il progetto.  
  
-   Se si desidera che i dati siano disponibili solo per lo sviluppatore corrente che ha il progetto SharePoint aperto in Visual Studio, salvare i dati nel file delle opzioni utente del progetto.  Questo file non viene generalmente archiviato nei database del controllo del codice sorgente, pertanto i dati presenti nel file non sono a disposizione degli altri sviluppatori che estraggono il progetto.  
  
### Salvataggio dei dati nel file di progetto  
 Per salvare i dati nel file di progetto, convertire un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> in un oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>, quindi utilizzare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>.  Nell'esempio di codice riportato di seguito viene illustrato come utilizzare il metodo per salvare il valore di una proprietà del progetto nel file di progetto.  Per vedere questo esempio nel contesto di un esempio più esaustivo, vedere [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#3)]
 [!code-vb[SpExt_SPCustomPrjProperty#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#3)]  
  
 Per ulteriori informazioni sulla conversione degli oggetti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> in altri tipi di oggetti nel modello a oggetti di automazione o di integrazione di Visual Studio, vedere [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### Salvataggio dei dati nel file delle opzioni utente del progetto  
 Per salvare i dati nel file delle opzioni utente del progetto, utilizzare la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  Nell'esempio di codice riportato di seguito viene illustrato come utilizzare la proprietà per salvare il valore di una proprietà del progetto nel file delle opzioni utente del progetto.  Per vedere questo esempio nel contesto di un esempio più esaustivo, vedere [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#2)]
 [!code-vb[SpExt_SPCustomPrjProperty#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#2)]  
  
## Vedere anche  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  