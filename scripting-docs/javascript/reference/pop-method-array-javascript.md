---
title: "Metodo pop (Array) (JavaScript) | Microsoft Docs"
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
  - "pop"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "pop (metodo)"
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Metodo pop (Array) (JavaScript)
Rimuove l'ultimo elemento da una matrice e lo restituisce.  
  
## Sintassi  
  
```  
  
arrayObj.pop( )  
```  
  
## Note  
 I metodi [push](../../javascript/reference/push-method-array-javascript.md) e `pop` consentono di simulare uno stack in cui viene utilizzato il principio LIFO \(Last In, First Out\) per archiviare i dati.  
  
 Il riferimento `arrayObj` obbligatorio è un oggetto `Array`.  
  
 Se la matrice è vuota, viene restituito il valore `undefined`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `pop`.  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Metodo push \(Array\)](../../javascript/reference/push-method-array-javascript.md)