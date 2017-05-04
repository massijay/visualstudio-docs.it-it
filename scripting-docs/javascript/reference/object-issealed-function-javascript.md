---
title: "Funzione Object.isSealed (JavaScript) | Microsoft Docs"
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
  - "isSealed (funzione) [JavaScript]"
  - "Object.isSealed [JavaScript]"
  - "proprietà [JavaScript], blocco degli attributi"
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Funzione Object.isSealed (JavaScript)
Restituisce `true` se gli attributi delle proprietà esistenti non possono essere modificati in un oggetto e non possono essere aggiunte nuove proprietà all'oggetto.  
  
## Sintassi  
  
```javascript  
Object.isSealed(object)  
```  
  
#### Parametri  
 `object`  
 Obbligatorio.  Oggetto da verificare.  
  
## Valore restituito  
 `true` se entrambe le condizioni seguenti vengono soddisfatte:  
  
-   L'oggetto non è estendibile, ovvero non possono essere aggiunte nuove proprietà.  
  
-   L'attributo `configurable` è `false` per tutte le proprietà esistenti.  
  
 Se l'oggetto non contiene alcuna proprietà, la funzione restituisce `true` se l'oggetto non è estendibile.  
  
## Eccezioni  
 Se l'argomento `object` non è un oggetto, viene generata un'eccezione `TypeError`.  
  
## Note  
 Quando l'attributo `configurable` di una proprietà è `false`, gli attributi della proprietà non possono essere modificati e la proprietà non può essere eliminata.  Quando `writable` è `false`, il valore della proprietà dei dati non può essere modificato.  Quando `configurable` è `false` e `writable` è `true`, gli attributi `writable` e `value` possono essere modificati.  
  
 La funzione `Object.isSealed` non utilizza l'attributo `writable` delle proprietà per determinarne il valore restituito.  
  
 Per informazioni sull'impostazione degli attributi della proprietà, vedere [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  Per ottenere gli attributi di una proprietà, è possibile utilizzare [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Funzioni correlate  
 Le seguenti funzioni correlate evitano la modifica degli attributi dell'oggetto.  
  
|Funzione|L'oggetto è reso non estendibile|`configurable` è impostato su `false` per ogni proprietà|`writable` è impostato su `false` per ogni proprietà|  
|--------------|--------------------------------------|--------------------------------------------------------------|----------------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sì|No|No|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Sì|Sì|No|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sì|Sì|Sì|  
  
 Le seguenti funzioni restituiscono `true` se tutte le condizioni indicate nella tabella seguente sono vere.  
  
|Funzione|L'oggetto è estendibile?|`configurable` è `false` per tutte le proprietà?|`writable` è `false` per tutte le proprietà dei dati?|  
|--------------|------------------------------|------------------------------------------------------|-----------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sì|No|No|  
|`Object.isSealed`|No|Sì|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sì|Sì|  
  
## Esempio  
 Nel seguente esempio viene illustrato l'utilizzo della funzione `Object.isSealed`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
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
 [Funzione Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Funzione Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Funzione Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Funzione Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)