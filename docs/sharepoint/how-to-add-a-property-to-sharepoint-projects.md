---
title: "How to: Add a Property to SharePoint Projects | Microsoft Docs"
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
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Property to SharePoint Projects
  Per aggiungere una proprietà a un progetto SharePoint, è possibile utilizzare un'estensione di progetto.  La proprietà viene visualizzata nella finestra **Proprietà** quando il progetto viene selezionato in **Esplora soluzioni**.  
  
 Nei passaggi seguenti si suppone che sia già stata creata un'estensione di progetto.  Per ulteriori informazioni, vedere [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### Per aggiungere una proprietà a un progetto SharePoint  
  
1.  Definire una classe con una proprietà pubblica che rappresenta la proprietà da aggiungere ai progetti SharePoint.  Per aggiungere più proprietà, è possibile definire tutte le proprietà nella stessa classe o in classi diverse.  
  
2.  Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> dell'implementazione di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> gestire l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> del parametro *projectService*.  
  
3.  Nel gestore dell'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> aggiungere un'istanza della classe di proprietà alla raccolta <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> del parametro degli argomenti dell'evento.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come aggiungere due proprietà ai progetti SharePoint.  Una proprietà consente di conservarne i dati nel file delle opzioni utente del progetto \(il file csproj.user o vbproj.user\).  L'altra proprietà consente di conservarne i dati nel file di progetto \(il file con estensione csproj o vbproj\).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#1)]
 [!code-vb[SpExt_SPCustomPrjProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#1)]  
  
### Informazioni sul codice  
 Per garantire che ogni volta che si verifica l'evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> venga utilizzata la stessa istanza della classe `CustomProjectProperties`, nell'esempio di codice l'oggetto delle proprietà viene aggiunto alla proprietà <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> del progetto la prima volta che si verifica questo evento.  Il codice recupera questo oggetto ogni volta che si verifica di nuovo questo evento.  Per ulteriori informazioni sull'utilizzo della proprietà <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> per associare i dati ai progetti, vedere [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Per conservare le modifiche ai valori delle proprietà, le funzioni di accesso **set** per le proprietà utilizzano le seguenti API:  
  
-   `CustomUserFileProperty` utilizza la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> per salvarne il valore nel file delle opzioni utente del progetto.  
  
-   `CustomProjectFileProperty` utilizza il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> per salvarne il valore nel file di progetto.  
  
 Per ulteriori informazioni su come conservare i dati in questi file, vedere [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Specifica del comportamento delle proprietà personalizzate  
 È possibile definire la modalità di visualizzazione e il comportamento di una proprietà personalizzata nella finestra **Proprietà** applicando alla definizione di proprietà gli attributi ottenuti dallo spazio dei nomi <xref:System.ComponentModel>.  Gli attributi seguenti sono utili in molti scenari:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: specifica il nome della proprietà visualizzata nella finestra **Proprietà**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: specifica la stringa descrittiva visualizzata nella parte inferiore della finestra **Proprietà** quando si seleziona la proprietà.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: specifica il valore predefinito della proprietà.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: specifica una conversione personalizzata tra la stringa visualizzata nella finestra **Proprietà** e un valore di proprietà non di tipo stringa.  
  
-   <xref:System.ComponentModel.EditorAttribute>: specifica un editor personalizzato da utilizzare per modificare la proprietà.  
  
## Compilazione del codice  
 In questo esempio sono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione.  Per ulteriori informazioni, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vedere anche  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  