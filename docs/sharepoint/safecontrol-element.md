---
title: "SafeControl Element"
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
  - "SafeControl element"
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControl Element
  Rappresenta un controllo ASPX o una Web part definita come sicura per l'accesso di un utente in qualsiasi pagina ASPX del sito di SharePoint.  
  
## Sintassi  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|**Assembly**|Attributo **xs:string** facoltativo.<br /><br /> Il nome dell'assembly in cui è definito il controllo ASPX o Web part.  Per impostazione predefinita, questo attributo utilizza il parametro sostituibile **$SharePoint.Project.AssemblyFullName$** per il nome dell'assembly.  Per ulteriori informazioni, vedere [Parametri sostituibili](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Attributo **xs:boolean** facoltativo.<br /><br /> Specifica se il controllo ASPX o il Web part è sicuro affinché utenti non attendibili accedano.|  
|**IsSafeAgainstScript**|Attributo **xs:boolean** facoltativo.<br /><br /> Specifica se utenti non attendibili possono visualizzare o modificare le proprietà del controllo ASPX o Web part.|  
|**Name**|Attributo **xs:string** facoltativo.<br /><br /> Il nome della voce di controllo sicura nella raccolta.|  
|**Namespace**|Attributo **xs:string** facoltativo.<br /><br /> Lo spazio dei nomi del controllo ASPX o Web part.|  
|**TypeName**|Attributo **xs:string** facoltativo.<br /><br /> Lo spazio dei nomi del controllo ASPX o Web part.|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Rappresenta una raccolta di controlli ASPX e Web part definite come sicure per l'accesso di un utente in qualsiasi pagina ASPX del sito di SharePoint.|  
  
## Note  
 Per ulteriori informazioni sui controlli sicuri, vedere [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
  
  