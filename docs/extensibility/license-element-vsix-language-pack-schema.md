---
title: "Elemento License (Schema VSIX Language Pack) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Elemento License (Schema VSIX Language Pack)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Facoltativo. Il percorso di una versione localizzata del file di licenza per l'estensione.  
  
## Sintassi  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|None||  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|None||  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento Language Pack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obbligatorio. Fornisce l'elemento radice per un language pack VSIX.|  
  
## Valore di testo  
 Il percorso relativo del file di licenza localizzato da visualizzare.  
  
## Note  
 Se il `License` elemento è definito, quindi viene visualizzato il testo del file di licenza definito durante l'installazione e l'utente deve accettare la licenza per continuare.  
  
## Informazioni sull'elemento  
  
|||  
|-|-|  
|Spazio dei nomi|http:\/\/schemas.microsoft.com\/Developer\/VSX\-schema\-LP\/2010|  
|Nome di schema|Schema Language Pack VSIX|  
|File di convalida|VSIXLanguagePackSchema.xsd|  
|Può essere vuoto|Non applicabile|  
  
## Vedere anche  
 [Riferimento allo Schema VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)   
 [Riferimento dello Schema 1.0 estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)