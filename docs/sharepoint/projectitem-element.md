---
title: "ProjectItem Element | Microsoft Docs"
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
  - "ProjectItem element"
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# ProjectItem Element
  Rappresenta un elemento di progetto SharePoint.  Si tratta dell'elemento radice obbligatorio del file spdata.  
  
## Sintassi  
  
```  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**DefaultFile**|Attributo **xs:string** facoltativo.<br /><br /> Il percorso relativo, includendo il nome file, del file che viene visualizzato nell'editor di Visual Studio quando si apre l'elemento di progetto SharePoint in **Esplora soluzioni**.  Il percorso è relativo dalla cartella che contiene il file spdata.|  
|**FeatureReceiverClass**|Attributo **xs:string** facoltativo.<br /><br /> Il nome completo di una classe ricevitore di funzionalità per questo elemento di progetto SharePoint.  Per ulteriori informazioni su questi ricevitori di funzionalità, vedere [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Attributo **xs:string** facoltativo.<br /><br /> Specifica il nome completo di un assembly che definisce un ricevitore di funzionalità per questo elemento del progetto SharePoint.  Per ulteriori informazioni su questi ricevitori di funzionalità, vedere [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  Per ulteriori informazioni sui nomi completi dell'assembly, vedere [Nomi degli assembly](../Topic/Assembly%20Names.md).|  
|**SupportedTrustLevels**|Attributo **xs:string** facoltativo.<br /><br /> Specifica i livelli di attendibilità che questo elemento del progetto SharePoint supporta.  Il valore può essere una delle seguenti stringhe: Sandboxed, FullTrust o All.  Il valore All specifica sia Sandboxed e FullTrust.<br /><br /> In un tipo di elemento di progetto SharePoint personalizzato, il valore di questo attributo corrisponde al valore che viene assegnato alla proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo da specificare lo stesso livello di attendibilità specificato nella proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>.|  
|**SupportedDeploymentScopes**|Attributo **xs:string** facoltativo.<br /><br /> Specifica gli ambiti di distribuzione che l'elemento del progetto SharePoint supporta.  Questo valore è una stringa delimitata da virgole che si compone di una o più delle seguenti stringhe: Farm, site, Web, WebApplication o Package.  Ad esempio,  "Web, Sito".<br /><br /> In un tipo di elemento di progetto SharePoint personalizzato, il valore di questo attributo corrisponde al valore che viene assegnato alla proprietà  <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> nell'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo da specificare lo stesso livello di attendibilità specificato nella proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>.|  
|**Type**|Attributo **xs:string** obbligatorio.<br /><br /> Identificatore per l'elemento di progetto SharePoint  In un tipo di elemento di progetto SharePoint personalizzato, l'identificatore è la stringa che si passa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Per ulteriori informazioni vedere [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Per un elenco degli identificatori relativo agli elementi di progetto SharePoint incorporati e inclusi in Visual Studio, vedere [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di elementi dati personalizzati associati all'elemento di progetto SharePoint.<br /><br /> È possibile includere solo un elemento **ExtensionData**.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di valori di proprietà inclusi in una funzionalità quando viene distribuita in SharePoint.<br /><br /> È possibile includere solo un elemento **FeatureProperties**.|  
|[File](../sharepoint/files-element.md)|Elemento **FileCollectionType** facoltativo.<br /><br /> Specifica i file da distribuire con l'elemento di progetto SharePoint, quali file di elemento della funzionalità e l'output di progetti non\-SharePoint dipendenti.<br /><br /> È necessario includere un elemento **Files** o un  **ProjectItemFolder**, ma non entrambi.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Elemento **ProjectItemFolderType** facoltativo.<br /><br /> Rappresenta una cartella mappata.<br /><br /> È necessario includere un elemento **Files** o un  **ProjectItemFolder**, ma non entrambi.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di controlli ASPX e Web part definite come sicure per l'accesso di un utente in qualsiasi pagina ASPX del sito di SharePoint.<br /><br /> È possibile includere solo un elemento **SafeControls**.|  
  
### Elementi padre  
 Nessuno.  
  
## Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nome schema**|Schema dell'elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## Vedere anche  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  