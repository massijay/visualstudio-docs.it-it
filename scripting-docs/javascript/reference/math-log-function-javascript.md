---
title: "Funzione Math.log (JavaScript) | Microsoft Docs"
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
  - "log"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "log (metodo)"
  - "Math (oggetto)"
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Funzione Math.log (JavaScript)
Restituisce il logaritmo naturale \(base `e`\) di un numero.  
  
## Sintassi  
  
```  
Math.log(number)   
```  
  
#### Parametri  
 numero  
 Numero.  
  
## Valore restituito  
 Se `number` è positivo, la funzione restituisce il logaritmo naturale del numero.  Se `number` è negativo, la funzione restituisce `NaN`.  Se `number` è 0, la funzione restituisce `-Infinity`.  
  
## Esempio  
 Nel codice seguente viene illustrato come utilizzare questa funzione:  
  
```javascript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto Math](../../javascript/reference/math-object-javascript.md)  
  
## Vedere anche  
 [Funzione Math.sqrt](../../javascript/reference/math-sqrt-function-javascript.md)