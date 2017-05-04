---
title: "Funzione Object.create (JavaScript) | Microsoft Docs"
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
  - "create (funzione) [JavaScript]"
  - "Object.create (funzione) [JavaScript]"
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Funzione Object.create (JavaScript)
Crea un oggetto che ha il prototipo specificato e che può contenere eventualmente le proprietà specificate.  
  
## Sintassi  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### Parametri  
 `prototype`  
 Necessario.  Oggetto da utilizzare come prototipo.  Può essere `null`.  
  
 `descriptors`  
 Opzionale.  Oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] contenente uno o più descrittori di proprietà.  
  
 Una *proprietà dei dati* è una proprietà che può ottenere e impostare un valore.  Un descrittore di proprietà dei dati contiene un attributo `value`, oltre agli attributi `writable`, `enumerable` e `configurable`.  Se gli ultimi tre attributi non sono specificati, viene utilizzato come valore predefinito `false`.  Una *proprietà di funzione di accesso* chiama una funzione fornita dall'utente ogni volta che il valore viene recuperato o impostato.  Un descrittore per le proprietà di funzione di accesso contiene un attributo `set`, un attributo `get`, o entrambi.  Per ulteriori informazioni, vedere [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## Valore restituito  
 Nuovo oggetto con il prototipo interno specificato e contenente le proprietà specificate, se disponibili.  
  
## Eccezioni  
 Un'eccezione `TypeError` viene generata se una delle seguenti condizioni è vera:  
  
-   L'argomento `prototype` non è un oggetto e non è `null`.  
  
-   Un descrittore nell'argomento `descriptors` presenta un attributo `value` o `writable` e un attributo `get` o `set`.  
  
-   Un descrittore nell'argomento `descriptors` presenta un attributo `get` o `set` che non rappresenta una funzione.  
  
## Note  
 È possibile utilizzare questa funzione mediante un parametro `prototype` `null` per arrestare la catena di prototipi.  L'oggetto creato non avrà alcun prototipo.  
  
## Esempio  
 Nell'esempio seguente viene creato un oggetto utilizzando un prototipo `null` e vengono aggiunte due proprietà enumerabili.  
  
```javascript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## Esempio  
 Nell'esempio seguente viene creato un oggetto contenente lo stesso prototipo interno dell'oggetto Object.  È possibile osservare che presenta lo stesso prototipo dell'oggetto creato utilizzando un valore letterale dell'oggetto.  La funzione [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) ottiene il prototipo dell'oggetto originale.  Per ottenere il descrittore di proprietà dell'oggetto, è possibile utilizzare [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```javascript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## Esempio  
 Nell'esempio seguente viene creato un oggetto contenente lo stesso prototipo interno dell'oggetto Shape.  
  
```javascript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Funzione Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Metodo isPrototypeOf \(Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Creazione di oggetti](../../javascript/creating-objects-javascript.md)