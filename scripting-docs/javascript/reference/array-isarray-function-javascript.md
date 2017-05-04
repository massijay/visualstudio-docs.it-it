---
title: "Funzione Array.isArray (JavaScript) | Microsoft Docs"
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
  - "Array.isArray (funzione) [JavaScript]"
  - "isArray (funzione) [JavaScript]"
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Funzione Array.isArray (JavaScript)
Determina se l'oggetto è una matrice.  
  
## Sintassi  
  
```  
Array.isArray(object)   
```  
  
#### Parametri  
 `object`  
 Obbligatorio.  Oggetto da testare.  
  
## Valore restituito  
 `true` se `object` è una matrice, altrimenti `false`.  Se l'argomento `object` non è un oggetto, viene restituito `false`.  
  
## Esempio  
 L'esempio seguente illustra l'uso della funzione `Array.isArray`.  
  
```javascript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)   
 [Operatore typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)