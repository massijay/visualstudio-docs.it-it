---
title: "ProjectItemFolder Element | Microsoft Docs"
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
  - "ProjectItemFolder element"
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# ProjectItemFolder Element
  Rappresenta una cartella mappata.  
  
## Sintassi  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## Tipo  
 **ProjectItemFolderType**  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Target**|Attributo **xs:string** obbligatorio.<br /><br /> Il percorso della cartella nell'installazione di SharePoint cui corrisponde la cartella mappata, relativa alla cartella radice distribuzione.  La cartella radice di distribuzione è determinata dal tipo di distribuzione specificato dall'attributo **Type**.<br /><br /> Per ulteriori informazioni, vedere le descrizioni per le proprietà **Deployment Path** and **Deployment Root** sugli elementi di progetto di SharePoint in  [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Attributo **xs:string** obbligatorio.<br /><br /> Il tipo di distribuzione per la cartella mappata.  Per ulteriori informazioni sui possibili valori, vedere la descrizione per la proprietà **Deployment Type** degli elementi di progetto di SharePoint in [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint.  Si tratta dell'elemento radice obbligatorio del file spdata.|  
  
## Note  
 Per ulteriori informazioni sulle cartelle mappate, vedere [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nome schema**|Schema dell'elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## Vedere anche  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  