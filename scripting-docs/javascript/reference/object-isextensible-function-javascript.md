---
title: "Funzione Object.isExtensible (JavaScript) | Microsoft Docs"
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
  - "isExtensible (funzione) [JavaScript]"
  - "Object.isExtensible (funzione) [JavaScript]"
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Funzione Object.isExtensible (JavaScript)
Restituisce un valore che indica se è possibile aggiungere nuove proprietà a un oggetto.  
  
## Sintassi  
  
```javascript  
Object.isExtensible(object)  
```  
  
#### Parametri  
 `object`  
 Obbligatorio.  Oggetto da verificare.  
  
## Valore restituito  
 `true` se l'oggetto è estendibile, ovvero possono essere aggiunte nuove proprietà; in caso contrario, `false`.  
  
## Eccezioni  
 Se l'argomento `object` non è un oggetto, viene generata un'eccezione `TypeError`.  
  
## Note  
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
|`Object.isExtensible`|Sì|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sì|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sì|Sì|  
  
## Esempio  
 Nel seguente esempio viene illustrato l'utilizzo della funzione `Object.isExtensible`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Funzione Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Funzione Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Funzione Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Funzione Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Funzione Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)