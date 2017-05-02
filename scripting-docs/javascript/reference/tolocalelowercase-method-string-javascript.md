---
title: "Metodo toLocaleLowerCase (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "toLocaleLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleLowerCase (metodo)"
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Metodo toLocaleLowerCase (String) (JavaScript)
Converte tutti i caratteri alfabetici in lettere minuscole tenendo in considerazione le impostazioni locali correnti dell'ambiente host.  
  
## Sintassi  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## Note  
 Il riferimento di `stringVar` obbligatorio è un oggetto `String` o un valore letterale stringa.  
  
 Il metodo `toLocaleLowerCase` converte i caratteri in una stringa, considerando le impostazioni locali correnti dell'ambiente host.  Nella maggior parte dei casi, il risultato è identico a quello del metodo `toLowerCase`.  I risultati sono diversi se le regole per una lingua sono in conflitto con i normali mapping di maiuscole e minuscole Unicode.  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo toLocaleUpperCase \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Metodo toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)