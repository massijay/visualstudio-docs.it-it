---
title: "Metodo push (Array) (JavaScript) | Microsoft Docs"
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
  - "push"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Push (metodo)"
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo push (Array) (JavaScript)
Aggiunge nuovi elementi a una matrice e restituisce la nuova lunghezza della matrice.  
  
## Sintassi  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## Parametri  
 `arrayObj`  
 Obbligatorio.  Oggetto `Array`.  
  
 `item, item2,. . ., itemN`  
 Facoltativo.  Nuovi elementi dell'oggetto `Array`.  
  
## Note  
 I metodi `push` e `pop` consentono di simulare uno stack LIFO.  
  
 Il metodo `push` aggiunge elementi nell'ordine in cui vengono riportati.  Se uno degli argomenti è una matrice, verrà aggiunto come elemento singolo.  Utilizzare il metodo `concat` per unire gli elementi di due o più matrici.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `push`.  
  
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
  
// Output:  
// 9 8 7 6 5  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Metodo concat \(Array\)](../../javascript/reference/concat-method-array-javascript.md)   
 [Metodo pop \(Array\)](../../javascript/reference/pop-method-array-javascript.md)