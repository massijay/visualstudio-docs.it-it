---
title: "Costanti Math (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "LN2 (costante) [JavaScript]"
  - "E (costante) [JavaScript]"
  - "LOG10E (costante) [JavaScript]"
  - "SQRT1_2 (costante) [JavaScript]"
  - "LOG2E (costante) [JavaScript]"
  - "Math.SQRT2 (costante) [JavaScript]"
  - "PI (costante) [JavaScript]"
  - "Math.LOG2E (costante) [JavaScript]"
  - "costanti [JavaScript], math"
  - "Math.E (costante) [JavaScript]"
  - "logarithm (costanti) [JavaScript]"
  - "Math.LOG10E (costante) [JavaScript]"
  - "Math.SQRT1_2 (costante) [JavaScript]"
  - "SQRT2 (costante) [JavaScript]"
  - "square root (costanti) [JavaScript]"
  - "Math.PI (costante) [JavaScript]"
  - "math (costanti) [JavaScript]"
  - "LN10 (costante) [JavaScript]"
  - "Math.LN2 (costante) [JavaScript]"
  - "Math.LN10 (costante) [JavaScript]"
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Costanti Math (JavaScript)
Le costanti matematiche restituiscono valori costanti che sono proprietà dell'oggetto `Math`.  
  
## Costanti dell'oggetto Math  
 Nella tabella seguente sono elencati i valori costanti che sono proprietà dell'[oggetto Math](../../javascript/reference/math-object-javascript.md).  
  
|Costante|Descrizione|Valore approssimativo|  
|--------------|-----------------|---------------------------|  
|`Math.E`|La costante matematica e.  Questo è il numero di Eulero, la base dei logaritmi naturali.|2.718|  
|`Math.LN2`|Logaritmo naturale di 2.|0.693|  
|`Math.LN10`|Logaritmo naturale di 10.|2.302|  
|`Math.LOG2E`|Logaritmo in base 2 di e.|1.443|  
|`Math.LOG10E`|Logaritmo in base 10 di e.|0.434|  
|`Math.PI`|Pi greco.  E' il rapporto tra la circonferenza del cerchio e il suo diametro.|3.14159|  
|`Math.SQRT1_2`|Radice quadrata di 0,5 o equivalentemente 1 diviso la radice quadrata di 2.|0.707|  
|`Math.SQRT2`|Radice quadrata di 2.|1.414|  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della costante `Math.PI`.  
  
```javascript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Math](../../javascript/reference/math-object-javascript.md)  
  
## Vedere anche  
 [Costanti Number](../../javascript/reference/number-constants-javascript.md)   
 [Costanti JavaScript](../../javascript/reference/javascript-constants.md)