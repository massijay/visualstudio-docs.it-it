---
title: "ExtensionData Element | Microsoft Docs"
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
  - "ExtensionData element"
ms.assetid: caf6843b-dcf5-4688-a9eb-a424aae1beab
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ExtensionData Element
  Rappresenta una raccolta di elementi dati personalizzati associati all'elemento di progetto SharePoint.  
  
## Sintassi  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Elemento facoltativo.<br /><br /> Rappresenta un elemento dati personalizzato associato all'elemento di progetto SharePoint, nel formato chiave\/valore.  Sia la chiave che il valore devono essere stringhe.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Rappresenta un elemento di progetto SharePoint.  Si tratta dell'elemento radice obbligatorio del file spdata.|  
  
## Note  
 Quando si associano dati personalizzati a un elemento di progetto SharePoint tramite la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>, Visual Studio salva i dati nell'elemento **ExtensionData** nel file spdata per l'elemento del progetto.  Per ulteriori informazioni, vedere [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nome schema**|Schema dell'elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## Vedere anche  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  