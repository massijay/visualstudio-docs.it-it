---
title: "Funzione Math.min (JavaScript) | Microsoft Docs"
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
  - "min"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "min (metodo)"
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Funzione Math.min (JavaScript)
Restituisce la minore di un set di espressioni numeriche.  
  
## Sintassi  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## Note  
 Gli argomenti `number1, number2, ..., numberN` facoltativi sono espressioni numeriche da valutare.  
  
 Se non è specificato alcun argomento, il valore restituito sarà uguale a [Number.POSITIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Se un argomento è `NaN`, anche il valore restituito sarà `NaN`.  
  
## Esempio  
 Nel codice seguente viene illustrato come ottenere la minore di due espressioni.  
  
```javascript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Funzione Math.max](../../javascript/reference/math-max-function-javascript.md)