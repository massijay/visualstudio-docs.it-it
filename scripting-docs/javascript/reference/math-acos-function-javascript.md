---
title: "Funzione Math.acos (JavaScript) | Microsoft Docs"
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
  - "acos"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "acos (metodo)"
  - "arcosine (metodo)"
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Funzione Math.acos (JavaScript)
Restituisce l'arcocoseno \(o coseno inverso\) di un numero.  
  
## Sintassi  
  
```  
Math.acos(number)  
```  
  
#### Parametri  
 L'argomento obbligatorio `number` è un'espressione numerica.  
  
## Valore restituito  
 L'arcocoseno dell'argomento `number`, in radianti.  
  
## Esempio  
 Nel codice riportato di seguito viene illustrato come utilizzare la funzione `acos`.  
  
```javascript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## Note  
 **Si applica a**: [Oggetto Math](../../javascript/reference/math-object-javascript.md)  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Funzione Math.asin](../../javascript/reference/math-asin-function-javascript.md)   
 [Funzione Math.atan](../../javascript/reference/math-atan-function-javascript.md)   
 [Funzione Math.cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Funzione Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Funzione Math.tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Oggetto Math](../../javascript/reference/math-object-javascript.md)