---
title: "Funzione Array.of (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione Array.of (Array) (JavaScript)
Restituisce una matrice dagli argomenti passati.  
  
## Sintassi  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### Parametri  
 `element0,...,elementN`  
 Facoltativo.  Elementi da inserire nella matrice.  Crea una matrice con n \+ 1 elementi e una lunghezza pari a n \+ 1.  
  
## Note  
 Questa funzione è simile a una chiamata a `new Array(args)`, ma `Array.of` non include un comportamento speciale quando viene passato un argomento.  
  
## Esempio  
 L'esempio seguente crea una matrice dai numeri passati.  
  
```javascript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1  
  
```  
  
## Esempio  
 L'esempio seguente illustra la differenza tra l'uso di `Array.of` e `new Array`.  
  
```javascript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]