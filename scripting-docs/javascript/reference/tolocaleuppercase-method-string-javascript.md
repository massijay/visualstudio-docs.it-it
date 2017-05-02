---
title: "Metodo toLocaleUpperCase (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleUpperCase (metodo)"
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Metodo toLocaleUpperCase (String) (JavaScript)
Restituisce una stringa in cui tutti i caratteri alfabetici sono stati convertiti in maiuscolo a seconda delle impostazioni locali correnti dell'ambiente host.  
  
## Sintassi  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## Note  
 Il riferimento di `stringVar` obbligatorio è un oggetto `String` o un valore letterale stringa.  
  
 Il metodo `toLocaleUpperCase` converte i caratteri in una stringa, considerando le impostazioni locali correnti dell'ambiente host.  Nella maggior parte dei casi, il risultato è identico a quello del metodo `toUpperCase`.  I risultati sono diversi se le regole per una lingua sono in conflitto con i normali mapping di maiuscole e minuscole Unicode.  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo toLocaleLowerCase \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [Metodo toUpperCase \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)