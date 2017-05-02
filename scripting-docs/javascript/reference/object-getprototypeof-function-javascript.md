---
title: "Funzione Object.getPrototypeOf (JavaScript) | Microsoft Docs"
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
  - "getPrototypeOf (funzione) [JavaScript]"
  - "Object.getPrototypeOf (funzione) [JavaScript]"
ms.assetid: 1c59cd7a-a7e2-4c5c-83ec-e6bd2b104d9f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Funzione Object.getPrototypeOf (JavaScript)
Restituisce il prototipo di un oggetto.  
  
## Sintassi  
  
```javascript  
Object.getPrototypeOf(object)  
```  
  
#### Parametri  
 `object`  
 Obbligatorio.  Oggetto che fa riferimento al prototipo.  
  
## Valore restituito  
 Prototipo dell'argomento `object`.  Il prototipo è anche un oggetto.  
  
## Eccezioni  
 Se l'argomento `object` non è un oggetto, viene generata un'eccezione `TypeError`.  
  
## Esempio  
 Nel seguente esempio viene illustrato l'utilizzo della funzione `Object.getPrototypeOf`:  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width) {  
    this.grain = grain;  
    this.width = width;  
}  
// Create an object from the pasta constructor.  
var spaghetti = new Pasta("wheat", 0.2);  
  
// Obtain the prototype from the object.  
var proto = Object.getPrototypeOf(spaghetti);  
  
// Add a property to the prototype and validate that  
// the original object has the property.  
proto.foodgroup = "carbohydrates";  
document.write(spaghetti.foodgroup + " ");  
  
// Verify that the prototype obtained from the object  
// is the same as the prototype of the constructor.  
var result = (proto === Pasta.prototype);  
document.write(result + " ");  
  
// Verify that prototype obtained from the object  
// is a prototype of the original object.  
var result = proto.isPrototypeOf(spaghetti);  
document.write(result);  
  
// Output: carbohydrates true true  
```  
  
## Esempio  
 Nell'esempio seguente viene utilizzata la funzione `Object.getPrototypeOf` per convalidare i tipi di dati.  
  
```javascript  
var reg = /a/;  
var result = (Object.getPrototypeOf(reg) === RegExp.prototype);  
document.write(result + " ");  
  
var err = new Error("an error");  
var result = (Object.getPrototypeOf(err) === Error.prototype);  
document.write(result);  
  
// Output: true true  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Proprietà prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)   
 [Metodo isPrototypeOf \(Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)