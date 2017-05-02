---
title: "Funzione Object.defineProperties (JavaScript) | Microsoft Docs"
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
  - "Object.defineProperties (funzione) [JavaScript]"
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Funzione Object.defineProperties (JavaScript)
Aggiunge una o più proprietà ad un oggetto e\/o modifica gli attributi delle proprietà esistenti.  
  
## Sintassi  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## Parametri  
 `object`  
 Necessario.  L'oggetto sul quale aggiungere o modificare proprietà.  Può essere un oggetto nativo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] o un oggetto DOM.  
  
 `descriptors`  
 Necessario.  Un oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che contiene uno o più oggetti descrittori.  Ogni oggetto descrittore descrive una proprietà dei dati o una proprietà di funzione di accesso.  
  
## Valore restituito  
 L'oggetto che viene passato alla funzione.  
  
## Note  
 L'argomento `descriptors` è un oggetto che contiene uno o più oggetti descrittori.  
  
 Una *proprietà dei dati* è una proprietà che può archiviare e recuperare un valore.  Un descrittore per le proprietà dei dati contiene un attributo `value`, un attributo `writable`, o entrambi.  Per ulteriori informazioni, vedere [Proprietà dei dati e proprietà di accesso](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 Una *proprietà di funzione di accesso* chiama una funziona fornita dall'utente ogni volta che il valore della proprietà viene impostato o recuperato.  Un descrittore per le proprietà di funzione di accesso contiene un attributo `set`, un attributo `get`, o entrambi.  
  
 Se l'oggetto dispone già di una proprietà con quel nome, gli attributi della proprietà vengono modificati.  Per ulteriori informazioni, vedere [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Per creare un oggetto e aggiungere proprietà al nuovo oggetto, è possibile utilizzare [Funzione Object.create](../../javascript/reference/object-create-function-javascript.md).  
  
## Aggiunta di proprietà  
 Nell'esempio seguente, la funzione `Object.defineProperties` aggiunge una proprietà dei dati e una proprietà di funzione di accesso a un oggetto definito dall'utente.  
  
 Nell'esempio viene utilizzato un valore letterale di oggetto per creare l'oggetto `descriptors` con gli oggetti descrittori `newAccessorProperty` e `newDataProperty`.  
  
```javascript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 Come nell'esempio precedente, nell'esempio seguente si aggiungono dinamicamente le proprietà anziché con un valore letterale di oggetto.  
  
```javascript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## Modifica di proprietà  
 Per modificare gli attributi di proprietà per l'oggetto, aggiungere il codice seguente.  La funzione `Object.defineProperties` modifica l'attributo `writable` di `newDataProperty` e modifica l'attributo `enumerable` di `newAccessorProperty`.  Aggiunge `anotherDataProperty` all'oggetto poiché quel nome della proprietà non esiste.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## Requisiti  
 Supportato negli standard di Internet Explorer 9, negli standard di Internet Explorer 10 e nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Supportato in Internet Explorer 8 solo per gli oggetti DOM, altrimenti non supportato.  
  
## Vedere anche  
 [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Funzione Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Funzione Object.create](../../javascript/reference/object-create-function-javascript.md)   
 [Oggetto Object](../../javascript/reference/object-object-javascript.md)