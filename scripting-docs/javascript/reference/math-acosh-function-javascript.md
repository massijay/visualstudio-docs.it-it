---
title: "Funzione Math.acosh (JavaScript) | Microsoft Docs"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione Math.acosh (JavaScript)
Restituisce l'arcocoseno iperbolico \(o coseno iperbolico inverso\) di un numero.  
  
## Sintassi  
  
```  
Math.acosh(number)  
```  
  
#### Parametri  
 L'argomento `number` obbligatorio è un'espressione numerica.  
  
## Valore restituito  
 Coseno iperbolico inverso dell'argomento `number`, in radianti.  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come usare la funzione `acosh`.  
  
```javascript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## Note  
 **Si applica a**: [Oggetto Math](../../javascript/reference/math-object-javascript.md)  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## Vedere anche  
 [Funzione Math.acos](../../javascript/reference/math-acos-function-javascript.md)   
 [Funzione Math.asin](../../javascript/reference/math-asin-function-javascript.md)   
 [Funzione Math.atan](../../javascript/reference/math-atan-function-javascript.md)   
 [Funzione Math.cos](../../javascript/reference/math-cos-function-javascript.md)   
 [Funzione Math.sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Funzione Math.tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Oggetto Math](../../javascript/reference/math-object-javascript.md)