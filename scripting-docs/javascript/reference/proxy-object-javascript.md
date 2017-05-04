---
title: "Oggetto Proxy (JavaScript) | Microsoft Docs"
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
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Oggetto Proxy (JavaScript)
Abilita il comportamento personalizzato per un oggetto.  
  
## Sintassi  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### Parametri  
 `target`  
 Obbligatorio.  Oggetto o funzione che deve essere virtualizzato dal proxy.  
  
 `handler`  
 Obbligatorio.  Oggetto contenente metodi \(trap\) che implementano il comportamento personalizzato.  
  
## Note  
 Gli oggetti `Proxy` vengono usati per intercettare le operazioni di basso livello interne su un altro oggetto.  Possono essere usati per l'intercettazione, la virtualizzazione di oggetti, la registrazione o il profiling e per altri scopi.  
  
 Se nel parametro handler del proxy non è stato definito un trap per un'operazione specifica, l'operazione viene inoltrata al parametro target.  
  
 L'oggetto handler definisce i metodi \(trap\) seguenti per implementare il comportamento personalizzato.  Gli esempi seguenti non sono esaustivi.  Per supportare il comportamento predefinito condizionale nel metodo dell'oggetto handler, usare metodi di [Oggetto Reflect](../../javascript/reference/reflect-object-javascript.md).  
  
|Sintassi del metodo \(trap\) di handler|Esempi di utilizzo|  
|---------------------------------------------|------------------------|  
|`apply: function(target, thisArg, args)`|Trap per una chiamata di funzione.|  
|`construct: function(target, args)`|Trap per un costruttore.|  
|`defineProperty: function(target, propertyName, descriptor)`|Trap per [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Trap per l'istruzione `delete`.|  
|`enumerate: function(target)`|Trap per l'istruzione [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), la funzione [Object.keys](../../javascript/reference/object-keys-function-javascript.md) e [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Trap per qualsiasi proprietà [getter](../../javascript/creating-objects-javascript.md).|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Trap per [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Trap per [Funzione Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Trap per l'operatore `in`, [Metodo hasOwnProperty \(Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md) e altri metodi.|  
|`isExtensible: function(target)`|Trap per [Funzione Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Trap per [Funzione Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Trap per [Funzione Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Trap per qualsiasi proprietà [setter](../../javascript/creating-objects-javascript.md).|  
|`setPrototypeOf: function(target, prototype)`|Trap per [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come creare un proxy per un valore letterale dell'oggetto con il trap `get`.  
  
```javascript  
var target = {};  
var handler = {  
  get: function (receiver, name) {  
    // This example includes a template string.  
    return `Hello, ${name}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## Esempio  
 Nell'esempio di codice seguente viene illustrato come creare un proxy per una funzione con il trap `apply`.  
  
```javascript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]