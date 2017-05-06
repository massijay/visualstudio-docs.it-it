---
title: "SharePoint Project Item Schema Reference"
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
  - "FeatureProperty element"
  - "SafeControls element"
  - "SafeControl element"
  - ".spdata files"
  - "ExtensionData element"
  - "FeatureProperties element"
  - "ProjectOutputFile element"
  - "Files element"
  - "ProjectItemFolder element"
  - "ProjectItemFile element"
  - "ExtensionDataItem element"
  - "ProjectItem element"
ms.assetid: 12b63cbc-bf94-4175-bfa8-2117943d00d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint Project Item Schema Reference
  In Visual Studio viene utilizzato lo schema degli elementi di progetto SharePoint per convalidare il contenuto dei file spdata.  Un file spdata specifica il contenuto e il comportamento di un elemento di progetto SharePoint.  Per ulteriori informazioni sul contenuto degli elementi di progetto SharePoint, vedere [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Lo schema degli elementi di progetto SharePoint è denominato ProjectItemModelSchema.xsd e viene installato per impostazione predefinita in %Programmi \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas.  
  
 L'elemento radice è l'elemento [ProjectItem](../sharepoint/projectitem-element.md).  Nella tabella riportata di seguito vengono descritti tutti gli elementi definiti dallo schema.  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi dati personalizzati associati all'elemento di progetto SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Rappresenta un elemento dati personalizzato associato all'elemento di progetto SharePoint, nel formato chiave\/valore.  Sia la chiave che il valore devono essere stringhe.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Rappresenta una raccolta di valori di proprietà inclusi in una funzionalità quando viene distribuita in SharePoint.  Dopo aver distribuito una funzionalità, è possibile accedere ai valori della proprietà nel codice.|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Rappresenta una proprietà personalizzata inclusa in una funzionalità quando viene distribuita in SharePoint.  Dopo aver distribuito una funzionalità, è possibile accedere alla proprietà nel codice.|  
|[File](../sharepoint/files-element.md)|Specifica i file da distribuire con l'elemento di progetto SharePoint, ad esempio un file di elemento della funzionalità o l'output di un progetto.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Rappresenta un file di SharePoint, ad esempio un file di elemento della funzionalità, da includere nell'elemento di progetto quando viene distribuito in SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Rappresenta una cartella mappata.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Rappresenta l'output di un progetto da includere nell'elemento di progetto quando viene distribuito in SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Rappresenta un controllo ASPX o una Web part definita come sicura per l'accesso di un utente in qualsiasi pagina ASPX del sito di SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part definite come sicure per l'accesso di un utente in qualsiasi pagina ASPX del sito di SharePoint.|  
  
## Vedere anche  
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  