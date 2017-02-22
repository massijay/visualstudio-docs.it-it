---
title: "Elemento VSIXLanguagePack (VSIX Language Pack Schema) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento VSIXLanguagePack (VSIX Language Pack Schema)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obbligatorio. Fornisce l'elemento radice per un language pack VSIX. Il language pack VSIX fornisce informazioni sull'installazione localizzata per un pacchetto VSIX.  
  
## Sintassi  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`xmlns`|Lo spazio dei nomi XML in cui è definito lo schema di Language Pack VSIX.|  
  
## Attributo xmlns  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Obbligatorio. Il percorso del file che definisce lo schema per i language pack.|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Obbligatorio. Il nome localizzato dell'estensione da installare.|  
|[Elemento LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Obbligatorio. La descrizione localizzata dell'estensione da installare.|  
|[Elemento URL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Facoltativo. Un collegamento a informazioni localizzate sull'estensione.|  
|[Elemento License](../extensibility/license-element-vsix-language-pack-schema.md)|Facoltativo. Il percorso di una versione localizzata del file di licenza per l'estensione.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Nessuna||  
  
## Informazioni sull'elemento  
  
|||  
|-|-|  
|Spazio dei nomi|http:\/\/schemas.microsoft.com\/Developer\/VSX\-schema\-LP\/2010|  
|Nome di schema|Schema Language Pack VSIX|  
|File di convalida|VSIXLanguagePackSchema.xsd|  
|Può essere vuoto|No|  
  
## Vedere anche  
 [Riferimento allo Schema VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)   
 [Riferimento dello Schema 1.0 estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)