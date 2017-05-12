---
title: "Funzione Object.getOwnPropertyNames (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyNames (metodo) [JavaScript]"
  - "Object.getOwnPropertyNames (metodo) [JavaScript]"
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Funzione Object.getOwnPropertyNames (JavaScript)
Restituisce i nomi delle proprietà personalizzate di un oggetto.  Le proprietà personalizzate di un oggetto sono definite direttamente nell'oggetto e non vengono ereditate dal prototipo dell'oggetto.  Le proprietà di un oggetto comprendono sia i campi \(oggetti\) sia le funzioni.  
  
## Sintassi  
  
```javascript  
Object.getOwnPropertyNames(object)  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`object`|Obbligatorio.  Oggetto contenente le proprietà personalizzate.|  
  
## Valore restituito  
 Matrice contenente i nomi delle proprietà personalizzate dell'oggetto.  
  
## Eccezioni  
 Se il valore fornito per l'argomento `object` non è il nome di un oggetto, viene generata un'eccezione `TypeError`.  
  
## Note  
 Il metodo `getOwnPropertyNames` restituisce i nomi delle proprietà e dei metodi enumerabili e non enumerabili.  Per restituire solo i nomi delle proprietà e dei metodi enumerabili, è possibile utilizzare [Funzione Object.keys](../../javascript/reference/object-keys-function-javascript.md).  
  
## Esempio  
 Nell'esempio seguente viene creato un oggetto contenente tre proprietà e un metodo.  Viene quindi utilizzato il metodo `getOwnPropertyNames` per ottenere le proprietà personalizzate, incluso il metodo, dell'oggetto.  
  
```javascript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## Esempio  
 Nell'esempio seguente vengono visualizzati i nomi delle proprietà che iniziano con la lettera 's' in un oggetto spaghetti costruito con il costruttore Pasta.  
  
```javascript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Funzione Object.keys](../../javascript/reference/object-keys-function-javascript.md)