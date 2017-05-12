---
title: "Funzione parseFloat (JavaScript) | Microsoft Docs"
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
  - "parseFloat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseFloat (metodo)"
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Funzione parseFloat (JavaScript)
Converte una stringa in un numero a virgola mobile.  
  
## Sintassi  
  
```  
parseFloat(numString)   
```  
  
## Note  
 L'argomento `numString` obbligatorio è una stringa contenente un numero a virgola mobile.  
  
 La funzione `parseFloat` restituisce un valore numerico uguale al numero contenuto in `numString`.  Se non è possibile analizzare correttamente alcun prefisso di `numString` in un numero a virgola mobile, viene restituito `NaN` \(Non numerico\).  
  
```javascript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Per verificare la presenza del valore `NaN`, è possibile utilizzare la funzione `isNaN`.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Global](../../javascript/reference/global-object-javascript.md)  
  
## Vedere anche  
 [Funzione isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Funzione parseInt](../../javascript/reference/parseint-function-javascript.md)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)