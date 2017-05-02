---
title: "Funzione Object.defineProperty (JavaScript) | Microsoft Docs"
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
  - "defineProperty (funzione) [JavaScript]"
  - "Object.defineProperty (funzione) [JavaScript]"
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: 74
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 74
---
# Funzione Object.defineProperty (JavaScript)
Aggiunge una proprietà a un oggetto o modifica gli attributi di una proprietà esistente.  
  
## Sintassi  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## Parametri  
 `object`  
 Obbligatorio.  Oggetto su cui si desidera aggiungere o modificare la proprietà.  Può essere un oggetto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nativo \(ovvero, un oggetto definito dall'utente o un oggetto incorporato\) o un oggetto DOM.  
  
 `propertyname`  
 Obbligatorio.  Stringa contenente il nome della proprietà.  
  
 `descriptor`  
 Obbligatorio.  Descrittore della proprietà.  Può essere una proprietà di dati o una proprietà di accesso.  
  
## Valore restituito  
 Oggetto modificato.  
  
## Note  
 È possibile usare la funzione `Object.defineProperty` per effettuare le operazioni seguenti:  
  
-   Aggiungere una nuova proprietà a un oggetto.  Ciò si verifica quando per l'oggetto non è specificato il nome della proprietà.  
  
-   Modificare gli attributi di una proprietà esistente.  Ciò si verifica quando per l'oggetto è già specificato il nome della proprietà.  
  
 La definizione della proprietà è disponibile in un oggetto descrittore, che descrive gli attributi di una proprietà di dati o di una proprietà di accesso.  L'oggetto descrittore è un parametro della funzione `Object.defineProperty`.  
  
 Per aggiungere più proprietà a un oggetto o per modificare più proprietà esistenti, è possibile usare la [Funzione Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md).  
  
## Eccezioni  
 Viene generata un'eccezione `TypeError` quando si verifica una delle seguenti condizioni:  
  
-   L'argomento `object` non è un oggetto.  
  
-   L'oggetto non è [estensibile](../../javascript/reference/object-isextensible-function-javascript.md) e il nome della proprietà specificato non esiste.  
  
-   `descriptor` ha un attributo `value` o `writable` e un attributo `get` o `set`.  
  
-   `descriptor` ha un attributo `get` o `set` che non è una funzione o non è definito.  
  
-   Il nome della proprietà specificato esiste già, la proprietà esistente ha un attributo `configurable` di  `false` e `descriptor` contiene uno o più attributi diversi da quelli della proprietà esistente  Tuttavia, quando la proprietà esistente ha un attributo `configurable` di `false` e un attributo `writable` di `true`, l'attributo `value` o `writable` può essere diverso.  
  
## Aggiunta di una proprietà di dati  
 Nell'esempio seguente la funzione `Object.defineProperty` aggiunge una proprietà dei dati a un oggetto definito dall'utente  Per aggiungere invece la proprietà a un oggetto DOM esistente, rimuovere il commento dalla riga `var = window.document`.  
  
```javascript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 Per elencare le proprietà dell'oggetto, aggiungere il codice seguente a questo esempio.  
  
```javascript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## Modifica di una proprietà di dati  
 Per modificare un attributo di proprietà per l'oggetto, aggiungere il codice seguente alla funzione `addDataProperty` illustrata in precedenza.  Il parametro `descriptor` contiene solo un attributo `writable`.  Gli altri attributi della proprietà dei dati rimangono invariati.  
  
```javascript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## Aggiunta di una proprietà della funzione di accesso  
 Nell'esempio seguente la funzione `Object.defineProperty` aggiunge una proprietà della funzione di accesso a un oggetto definito dall'utente.  
  
```javascript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
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
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 Per elencare le proprietà dell'oggetto, aggiungere il codice seguente a questo esempio.  
  
```javascript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## Modifica di una proprietà della funzione di accesso  
 Per modificare un attributo di proprietà per l'oggetto, aggiungere il codice seguente al codice illustrato in precedenza.  Il parametro `descriptor` contiene solo una definizione della funzione di accesso `get`.  Gli altri attributi della proprietà rimangono invariati.  
  
```javascript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## Modifica di una proprietà di un elemento DOM  
 Nell'esempio seguente viene illustrato come personalizzare le proprietà incorporate DOM usando la funzione `Object.getOwnPropertyDescriptor` per ottenere e modificare il descrittore della proprietà.  Per questo esempio, deve essere presente un elemento DIV con un ID di "div".  
  
```javascript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## Requisiti  
 La modalità standard di Internet Explorer 9 e Internet Explorer 10 e le applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] supportano tutte le funzionalità.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] supporta gli oggetti DOM ma non gli oggetti definiti dall'utente.  Gli attributi `enumerable` e `configurable` possono essere specificati, ma non vengono usati.  
  
## Vedere anche  
 [Prototipi di Document Object Model Prototypes, parte 2: supporto delle funzioni di accesso \(getter\/setter\) Support](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Funzione Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Funzione Object.create](../../javascript/reference/object-create-function-javascript.md)   
 [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Funzione Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)