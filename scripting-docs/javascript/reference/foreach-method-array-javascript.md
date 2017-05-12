---
title: "Metodo forEach (Array) (JavaScript) | Microsoft Docs"
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
  - "matrici [JavaScript], forEach (metodo)"
  - "funzione di callback, forEach (metodo) [JavaScript]"
  - "forEach (metodo) [JavaScript]"
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# Metodo forEach (Array) (JavaScript)
Esegue l'azione specificata per ogni elemento in una matrice.  
  
## Sintassi  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`array1`|Obbligatorio.  Oggetto matrice.|  
|`callbackfn`|Obbligatorio.  Funzione che accetta fino a tre argomenti.  `forEach` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice.|  
|`thisArg`|Facoltativa.  Oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`.  Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.|  
  
## Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## Note  
 Il metodo `forEach` chiama la funzione `callbackfn` una volta per ogni elemento presente nella matrice, in ordine di indice crescente.  La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Oltre agli oggetti matrice, il metodo `forEach` può essere utilizzato da qualsiasi oggetto con una proprietà `length` e con nomi delle proprietà indicizzati numericamente.  
  
## Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, index, array1)`  
  
 È possibile dichiarare la funzione di callback utilizzando fino a tre parametri.  
  
 I parametri della funzione di callback sono i seguenti.  
  
|Argomento di callback|Definizione|  
|---------------------------|-----------------|  
|`value`|Valore dell'elemento della matrice.|  
|`index`|Indice numerico dell'elemento della matrice.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## Modifica dell'oggetto matrice  
 Il metodo `forEach` non modifica direttamente la matrice originale, mentre la funzione di callback può modificarla.  Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `forEach`.  
  
|Condizione dopo l'avvio del metodo `forEach`|Elemento passato alla funzione di callback?|  
|--------------------------------------------------|-------------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `forEach`.  
  
```javascript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## Esempio  
 Nell'esempio seguente, l'argomento `callbackfn` include il codice della funzione di callback.  
  
```javascript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'argomento `thisArg`, che specifica un oggetto a cui la parola chiave `this` può fare riferimento.  
  
```javascript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Metodo filter \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Metodo map \(Array\)](../../javascript/reference/map-method-array-javascript.md)   
 [Metodo some \(Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)   
 [Applicazione di esempio JavaScript Hilo \(Windows Store\)](http://hilojs.codeplex.com/SourceControl/latest)