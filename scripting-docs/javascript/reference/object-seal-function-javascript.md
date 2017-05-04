---
title: "Funzione Object.seal (JavaScript) | Microsoft Docs"
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
  - "Object.seal (funzione)"
  - "seal (funzione)"
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione Object.seal (JavaScript)
Impedisce la modifica degli attributi delle proprietà esistenti e impedisce l'aggiunta di nuove proprietà.  
  
## Sintassi  
  
```javascript  
Object.seal(object)  
```  
  
#### Parametri  
 `object`  
 Obbligatorio.  Oggetto sul quale bloccare gli attributi.  
  
## Valore restituito  
 Oggetto passato alla funzione.  
  
## Eccezioni  
 Se l'argomento `object` non è un oggetto, viene generata un'eccezione `TypeError`.  
  
## Note  
 La funzione `Object.seal` esegue entrambe le operazioni di seguito riportate:  
  
-   Rende l'oggetto non estendibile, in modo che non possano essere aggiunte nuove proprietà.  
  
-   Imposta l'attributo `configurable` su `false` per tutte le proprietà dell'oggetto.  
  
 Quando l'attributo `configurable` è `false`, gli attributi della proprietà non possono essere modificati e la proprietà non può essere eliminata.  Quando `configurable` è `false` e `writable` è `true`, gli attributi `writable` e `value` possono essere modificati.  
  
 La funzione `Object.seal` non modifica l'attributo `writable`.  
  
 Per maggiori informazioni sull'impostazione degli attributi della proprietà, vedere [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  Per ottenere gli attributi di una proprietà, puoi utilizzare [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Funzioni correlate  
 Le seguenti funzioni correlate evitano la modifica degli attributi dell'oggetto.  
  
|Funzione|L'oggetto è reso non estendibile|`configurable` è impostato su `false` per ogni proprietà|`writable` è impostato su `false` per ogni proprietà|  
|--------------|--------------------------------------|--------------------------------------------------------------|----------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sì|No|No|  
|`Object.seal`|Sì|Sì|No|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sì|Sì|Sì|  
  
 Le seguenti funzioni restituiscono `true` se tutte le condizioni indicate nella tabella seguente sono vere.  
  
|Funzione|L'oggetto è estendibile?|`configurable` è `false` per tutte le proprietà?|`writable` è `false` per tutte le proprietà dei dati?|  
|--------------|------------------------------|------------------------------------------------------|-----------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sì|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sì|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sì|Sì|  
  
## Esempio  
 Nel seguente esempio viene illustrato l'utilizzo della funzione `Object.seal`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Funzione Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Funzione Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Funzione Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Funzione Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Funzione Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)