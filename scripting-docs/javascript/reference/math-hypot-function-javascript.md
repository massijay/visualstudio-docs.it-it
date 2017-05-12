---
title: "Funzione Math.hypot (JavaScript) | Microsoft Docs"
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Funzione Math.hypot (JavaScript)
Restituisce la radice quadrata della somma dei quadrati degli argomenti.  
  
## Sintassi  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### Parametri  
 `value1`  
 Obbligatorio.  Primo numero.  
  
 `value2`  
 Facoltativo.  Secondo numero.  
  
 `values`  
 Facoltativo.  Uno o più numeri.  
  
## Note  
 Se un argomento è NaN, la funzione restituisce NaN.  Se non vengono forniti argomenti, la funzione restituisce 0.  
  
## Esempio  
 Di seguito è illustrato un esempio di uso della funzione `Math.hypot`.  
  
```javascript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]