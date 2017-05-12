---
title: "Funzione Object.keys (JavaScript) | Microsoft Docs"
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
  - "keys (metodo) [JavaScript]"
  - "Object.keys (metodo) [JavaScript]"
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione Object.keys (JavaScript)
Restituisce i nomi delle proprietà e dei metodi enumerabili di un oggetto.  
  
## Sintassi  
  
```javascript  
Object.keys(object)  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`object`|Obbligatorio.  Oggetto contenente le proprietà e i metodi.  Può trattarsi di un oggetto creato o di un oggetto DOM \(Document Object Model\) esistente.|  
  
## Valore restituito  
 Matrice contenente i nomi delle proprietà e dei metodi enumerabili dell'oggetto.  
  
## Eccezioni  
 Se il valore fornito per l'argomento `object` non è il nome di un oggetto, viene generata un'eccezione `TypeError`.  
  
## Note  
 Il metodo `keys` restituisce solo i nomi delle proprietà e dei metodi enumerabili.  Per restituire i nomi delle proprietà e dei metodi enumerabili e non enumerabili, è possibile utilizzare [Funzione Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Per informazioni sull'attributo `enumerable` di una proprietà, vedere [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md) e [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## Esempio  
 Nell'esempio seguente viene creato un oggetto contenente tre proprietà e un metodo.  Viene quindi utilizzato il metodo `keys` per ottenere le proprietà e i metodi dell'oggetto.  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## Esempio  
 Nell'esempio seguente vengono visualizzati i nomi di tutte le proprietà enumerabili che iniziano con la lettera "g" nell'oggetto Pasta.  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Funzione Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)