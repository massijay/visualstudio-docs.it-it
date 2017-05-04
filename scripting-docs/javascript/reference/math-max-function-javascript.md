---
title: "Funzione Math.max (JavaScript) | Microsoft Docs"
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
  - "max"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "max (metodo)"
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Funzione Math.max (JavaScript)
Restituisce la maggiore di un set di espressioni numeriche specificate.  
  
## Sintassi  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## Note  
 Gli argomenti `number1, number2, ..., numberN` facoltativi sono espressioni numeriche da valutare.  
  
 Se non è specificato alcun argomento, il valore restituito sarà uguale a [Number.NEGATIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md).  Se un argomento è `NaN`, anche il valore restituito sarà `NaN`.  
  
## Esempio  
 Nel codice seguente viene illustrato come ottenere la maggiore di due espressioni.  
  
```javascript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Funzione Math.min](../../javascript/reference/math-min-function-javascript.md)