---
title: "Files Element | Microsoft Docs"
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
  - "Files element"
ms.assetid: 3c611d5b-28f1-48a7-a068-63e01fa2f3aa
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Files Element
  Specifica i file da distribuire con l'elemento di progetto SharePoint, quali file di elemento della funzionalità e l'output di progetti non\-SharePoint dipendenti.  
  
## Sintassi  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## Tipo  
 **FileCollectionType**  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Elemento **ProjectItemFileType** facoltativo.<br /><br /> Rappresenta un file di SharePoint, ad esempio un file di elemento della funzionalità, da includere nell'elemento di progetto quando viene distribuito in SharePoint.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Elemento **ProjectOutputFileType** facoltativo.<br /><br /> Rappresenta l'output di un progetto da includere nell'elemento di progetto quando viene distribuito in SharePoint.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint.  Si tratta dell'elemento radice obbligatorio del file spdata.|  
  
## Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nome schema**|Schema dell'elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## Vedere anche  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  