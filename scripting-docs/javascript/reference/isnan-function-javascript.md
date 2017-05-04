---
title: "Funzione isNaN (JavaScript) | Microsoft Docs"
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
  - "isNaN"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isNaN (metodo)"
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Funzione isNaN (JavaScript)
Restituisce un valore booleano che indica se un valore è il valore riservato `NaN` \(Not a Number\).  
  
## Sintassi  
  
```  
isNaN(numValue)   
```  
  
## Valore restituito  
 `true` se il valore convertito al tipo `Number` è `NaN`, altrimenti `false`.  
  
## Note  
 Il parametro richiesto `numValue` è il valore sui cui eseguire il test con `NaN`.  
  
 Questo metodo viene in genere utilizzato per verificare i valori restituiti dai metodi `parseInt` e `parseFloat`.  
  
 In alternativa, è possibile stabilire un confronto di una variabile contenente `NaN` o un altro valore con se stessa.  Se il confronto indica una differenza, significa che la variabile è uguale al valore `NaN`.  `NaN` è infatti l'unico valore che non risulta mai uguale a se stesso.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Global](../../javascript/reference/global-object-javascript.md)  
  
## Esempio  
  
```javascript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## Vedere anche  
 [Funzione isFinite](../../javascript/reference/isfinite-function-javascript.md)   
 [Costante NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Funzione parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Funzione parseInt](../../javascript/reference/parseint-function-javascript.md)