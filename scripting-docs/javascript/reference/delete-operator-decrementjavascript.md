---
title: "Operatore delete (JavaScript) | Microsoft Docs"
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
  - "delete_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "elementi di matrice, eliminazione"
  - "proprietà, eliminazione"
  - "Operatore delete"
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Operatore delete (JavaScript)
Elimina una proprietà da un oggetto o rimuove un elemento da una matrice.  
  
## Sintassi  
  
```  
delete expression  
```  
  
## Note  
 L'argomento `expression` è un'espressione [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valida che genera solitamente un nome della proprietà o un elemento della matrice.  
  
 Se il risultato di `expression` è un oggetto, la proprietà specificata in `expression` esiste e l'oggetto non ne consente l'eliminazione, viene restituito `false`.  
  
 In tutti gli altri casi, viene restituito `true`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come rimuovere un elemento da una matrice.  
  
```javascript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato come eliminare le proprietà da un oggetto.  
  
```javascript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vedere anche  
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)