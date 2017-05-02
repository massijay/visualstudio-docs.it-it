---
title: "Metodo toLowerCase (JavaScript) | Microsoft Docs"
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
  - "toLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLowerCase (metodo)"
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo toLowerCase (JavaScript)
Converte tutti i caratteri alfabetici di una stringa in lettere minuscole.  
  
## Sintassi  
  
```  
  
      strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## Note  
 Il metodo `toLowerCase` non ha alcun effetto sui caratteri non alfabetici.  
  
 Nell'esempio seguente viene illustrato il risultato ottenuto con il metodo `toLowerCase`.  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo toLocaleLowerCase \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [Metodo toUpperCase \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)