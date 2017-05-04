---
title: "ProjectItemFile Element | Microsoft Docs"
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
  - "ProjectItemFile element"
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ProjectItemFile Element
  Rappresenta un file di SharePoint, ad esempio un file di elemento della funzionalità, da includere nell'elemento di progetto quando viene distribuito in SharePoint.  
  
## Sintassi  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## Tipo  
 **ProjectItemFileType**  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Source**|Attributo **xs:string** obbligatorio.<br /><br /> Il nome del file da distribuire con l'elemento di progetto.|  
|**Target**|Attributo **xs:string** facoltativo.<br /><br /> La cartella dove il file verrà distribuito in SharePoint, relativa alla cartella radice di distribuzione.  La cartella radice di distribuzione è determinata dal tipo di distribuzione specificato dall'attributo **Type**.  Se non è specificato l'attributo **Target**, il file sarà distribuito a una cartella con il nome specificato nell'attributo **Source**.<br /><br /> Per ulteriori informazioni, vedere le descrizioni per le proprietà **Deployment Path** and **Deployment Root** sugli elementi di progetto di SharePoint in  [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Attributo **xs:string** obbligatorio.<br /><br /> Il tipo di distribuzione per il file.  Per ulteriori informazioni sui possibili valori, vedere la descrizione per la proprietà **Deployment Type** degli elementi di progetto di SharePoint in [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[File](../sharepoint/files-element.md)|Specifica i file da includere con l'elemento di progetto SharePoint quando viene distribuito a SharePoint.|  
  
## Note  
 I file SharePoint cui si fa riferimento in genere negli elementi **ProjectItemFile** includono file dell'elemento della funzionalità \(Elements.xml\), file di schema per le definizioni dell'elenco \(Schema.xml\) e file della definizione di Web part per i Web part \(webpart\).  
  
## Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nome schema**|Schema dell'elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## Vedere anche  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  