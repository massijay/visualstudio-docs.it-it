---
title: "Metodo toUpperCase (String) (JavaScript) | Microsoft Docs"
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
  - "toUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUpperCase (metodo)"
ms.assetid: 4fd4ccc3-e794-498a-9db1-baf48fc1dda1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo toUpperCase (String) (JavaScript)
Converte tutti i caratteri alfabetici di una stringa in lettere maiuscole.  
  
## Sintassi  
  
```  
  
      strVariable.toUpperCase()  
"String Literal".toUpperCase()   
```  
  
## Note  
 Il metodo `toUpperCase` non ha alcun effetto sui caratteri non alfabetici.  
  
## Esempio  
 Nell'esempio seguente viene illustrato il risultato ottenuto con il metodo `toUpperCase`.  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1.toUpperCase();  
document.write(str2);  
  
// Output: THIS IS A STRING.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Metodo toLocaleUpperCase \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Metodo toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)