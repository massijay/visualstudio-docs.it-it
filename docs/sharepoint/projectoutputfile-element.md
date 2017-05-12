---
title: "ProjectOutputFile Element"
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
  - "ProjectOutputFile element"
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# ProjectOutputFile Element
  Rappresenta l'output di un progetto separato da includere con l'elemento di progetto quando viene distribuito a SharePoint.  
  
## Sintassi  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## Tipo  
 **ProjectOutputFileType**  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**ProjectId**|Attributo **xs:string** obbligatorio.<br /><br /> GUID del progetto dipendente che dispone dell'output che si desidera includere.  Questo valore corrisponde all'elemento **ProjectGuid** del file di progetto dipendente.|  
|**ProjectPath**|Attributo **xs:string** obbligatorio.<br /><br /> Il percorso relativo, includendo il nome del file di progetto del progetto dipendente che dispone dell'output che si desidera includere.  Questo percorso è relativo alla cartella radice del progetto SharePoint che contiene l'elemento di progetto SharePoint.|  
|**Target**|Attributo **xs:string** facoltativo.<br /><br /> Il percorso dove l'output del progetto dipendente deve essere distribuito nel server SharePoint,  relativo alla  cartella radice di distribuzione.  La cartella radice di distribuzione è determinata dal tipo di distribuzione specificato dall'attributo **Type**.<br /><br /> Per ulteriori informazioni, vedere le descrizioni per le proprietà **Deployment Path** and **Deployment Root** sugli elementi di progetto di SharePoint in  [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Attributo **xs:string** obbligatorio.<br /><br /> Il tipo di distribuzione da utilizzare per l'output del progetto dipendente.  Per ulteriori informazioni sui possibili valori, vedere la descrizione per la proprietà **Deployment Type** degli elementi di progetto di SharePoint in [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'elemento di progetto SharePoint quando viene distribuito a SharePoint.|  
  
## Note  
 Utilizzare l'elemento **ProjectOutputFile** per includere l'output di un progetto da nella distribuzione dell'elemento di progetto di SharePoint.  È possibile specificare un progetto diverso o lo stesso progetto che contiene l'elemento del progetto.  Per ulteriori informazioni, vedere [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nome schema**|Schema dell'elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## Vedere anche  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  