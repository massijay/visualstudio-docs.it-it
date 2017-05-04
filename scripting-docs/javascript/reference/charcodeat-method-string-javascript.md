---
title: "Metodo charCodeAt (String) (JavaScript) | Microsoft Docs"
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
  - "charCodeAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "charCodeAt (metodo)"
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Metodo charCodeAt (String) (JavaScript)
Restituisce il valore Unicode del carattere nella posizione specificata.  
  
## Sintassi  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## Parametri  
 `strObj`  
 Obbligatorio.  Qualsiasi oggetto `String` o valore letterale stringa.  
  
 `index`  
 Obbligatorio.  Indice in base zero del carattere desiderato.  Se non è presente alcun carattere in corrispondenza dell'indice specificato, viene restituito `NaN`.  
  
## Note  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `charCodeAt`.  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Funzione String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)