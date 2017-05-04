---
title: "Metodo includes (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo includes (String) (JavaScript)
Restituisce un valore booleano che indica se la stringa passata è contenuta nell'oggetto string.  
  
## Sintassi  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### Parametri  
 `stringObj`  
 Obbligatorio.  Oggetto string da testare.  
  
 `substring`  
 Obbligatorio.  Stringa da testare.  
  
 `position`  
 Facoltativo.  Posizione del primo carattere da testare nell'oggetto string, partendo da 0.  
  
## Valore restituito  
 Se la stringa passata è contenuta nell'oggetto string, il metodo `includes` restituisce `true`; in caso contrario, restituisce `false`.  
  
## Note  
  
## Esempio  
  
```javascript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]