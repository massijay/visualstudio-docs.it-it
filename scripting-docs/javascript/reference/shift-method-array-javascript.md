---
title: "Metodo shift (Array) (JavaScript) | Microsoft Docs"
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
  - "shift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "shift (metodo)"
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo shift (Array) (JavaScript)
Rimuove il primo elemento di una matrice e lo restituisce.  
  
## Sintassi  
  
```  
  
arrayObj.shift( )  
```  
  
#### Parametri  
 Il riferimento `arrayObj` richiesto è un oggetto `Array`.  
  
## Valore restituito  
 Viene restituito l'elemento rimosso dalla matrice.  
  
## Note  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `shift`.  
  
```javascript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Metodo unshift \(Array\)](../../javascript/reference/unshift-method-array-javascript.md)