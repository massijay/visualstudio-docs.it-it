---
title: "ExtensionDataItem Element | Microsoft Docs"
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
  - "ExtensionDataItem element"
ms.assetid: 6a5fe7eb-b433-42dc-bd50-4882b780e2fb
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ExtensionDataItem Element
  Rappresenta un elemento dati personalizzato associato all'elemento di progetto SharePoint, nel formato chiave\/valore.  Sia la chiave che il valore devono essere stringhe.  
  
## Sintassi  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Key**|Attributo **xs:string** obbligatorio.<br /><br /> Chiave utilizzata per archiviare e recuperare gli elementi dati.|  
|**Value**|Attributo **xs:string** obbligatorio.<br /><br /> Il valore dell'elemento di dati.|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Rappresenta una raccolta di elementi dati personalizzati associati all'elemento di progetto SharePoint.|  
  
## Note  
 Quando si associano dati personalizzati a un elemento di progetto SharePoint tramite la proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>, Visual Studio salva i dati in un nuovo elemento **ExtensionDataItem** nel file spdata per l'elemento del progetto.  Per ulteriori informazioni, vedere [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Informazioni sull'elemento  
  
|||  
|-|-|  
|**Spazio dei nomi**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Nome schema**|Schema dell'elemento di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## Vedere anche  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  