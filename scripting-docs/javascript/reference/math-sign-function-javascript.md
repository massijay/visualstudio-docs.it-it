---
title: "Funzione Math.sign (JavaScript) | Microsoft Docs"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione Math.sign (JavaScript)
Restituisce il segno di un numero, indicante se il numero è positivo, negativo o 0.  
  
## Sintassi  
  
```  
Math.sign(number)  
```  
  
## Note  
 L'argomento `number` obbligatorio è un'espressione numerica per la quale è necessario il segno.  
  
 Il valore restituito è uno dei seguenti:  
  
-   `NaN`, se `number` è `NaN`.  
  
-   \-0, se `number` è \-0.  
  
-   \+0, se `number` è \+0.  
  
-   \-1, se `number` è negativo e diverso da \-0.  
  
-   \+1, se `number` è positivo e diverso da \+0.  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]