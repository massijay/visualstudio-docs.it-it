---
title: "Funzione Object.preventExtensions (JavaScript) | Microsoft Docs"
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
  - "Object.preventExtensions (funzione) [JavaScript]"
  - "preventExtensions (funzione) [JavaScript]"
  - "impedimento nuove proprietà [JavaScript]"
  - "proprietà [JavaScript], impedimento nuova"
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Funzione Object.preventExtensions (JavaScript)
Impedisce l'aggiunta di nuove proprietà a un oggetto.  
  
## Sintassi  
  
```javascript  
Object.preventExtensions(object)  
```  
  
#### Parametri  
 `object`  
 Obbligatorio.  L'oggetto da rendere non estensibile.  
  
## Valore restituito  
 Oggetto passato alla funzione.  
  
## Eccezioni  
 Se l'argomento `object` non è un oggetto, viene generata un'eccezione `TypeError`.  
  
## Note  
 La funzione `Object.preventExtensions` rende un oggetto non estensibile, in modo che le nuove proprietà denominate non possano essere aggiunte.  Dopo che un oggetto viene reso non estensibile, non può essere reso estensibile.  
  
 Per informazioni sull'impostazione degli attributi della proprietà, vedere [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Funzioni correlate  
 Le seguenti funzioni correlate evitano la modifica degli attributi dell'oggetto.  
  
|Funzione|L'oggetto è reso non estendibile|`configurable` è impostato su `false` per ogni proprietà|`writable` è impostato su `false` per ogni proprietà|  
|--------------|--------------------------------------|--------------------------------------------------------------|----------------------------------------------------------|  
|`Object.preventExtensions`|Sì|No|No|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Sì|Sì|No|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sì|Sì|Sì|  
  
 Le seguenti funzioni restituiscono `true` se tutte le condizioni indicate nella tabella seguente sono vere.  
  
|Funzione|L'oggetto è estendibile?|`configurable` è `false` per tutte le proprietà?|`writable` è `false` per tutte le proprietà dei dati?|  
|--------------|------------------------------|------------------------------------------------------|-----------------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sì|No|No|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|No|Sì|No|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|No|Sì|Sì|  
  
## Esempio  
 Nel seguente esempio viene illustrato l'utilizzo della funzione `Object.preventExtensions`.  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Funzione Object.seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Funzione Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Funzione Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Funzione Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Funzione Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)