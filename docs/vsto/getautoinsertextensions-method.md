---
title: "Metodo GetAutoInsertExtensions"
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
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo GetAutoInsertExtensions
  Ottiene informazioni sulle applicazioni per Office che devono essere inserite automaticamente durante il debug.  
  
 Tale metodo è riservato per utilizzi futuri.  
  
## Sintassi  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*psaExtensionNames*|I nomi di estensione di applicazioni per Office.|  
  
## Valore restituito  
 Valore HRESULT indicante se il metodo è stato eseguito correttamente.  
  
## Note  
 Ogni applicazione di Office sia inserita viene restituita come nome dell'estensione dell'applicazione di Office, che corrisponde a un valore in HKEY\_CURRENT\_USER \\ software \\ Microsoft \\ Microsoft \\ \\ WEF sviluppatore.  L'host deve trovare questi valori nel Registro di sistema e quindi inserire automaticamente le estensioni.  
  
  