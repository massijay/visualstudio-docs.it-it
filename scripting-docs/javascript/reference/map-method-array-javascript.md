---
title: "Metodo map (Array) (JavaScript) | Microsoft Docs"
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
  - "matrici [JavaScript], map (metodo)"
  - "map (metodo) [JavaScript]"
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Metodo map (Array) (JavaScript)
Chiama la funzione di callback specificata in ogni elemento di una matrice e restituisce una matrice contenente i risultati.  
  
## Sintassi  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`array1`|Obbligatorio.  Oggetto matrice.|  
|`callbackfn`|Obbligatorio.  Funzione che accetta fino a tre argomenti.  Il metodo `map` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice.|  
|`thisArg`|Facoltativa.  Oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`.  Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.|  
  
## Valore restituito  
 Nuova matrice in cui ogni elemento rappresenta il valore restituito della funzione di callback per l'elemento della matrice originale associato.  
  
## Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## Note  
 Il metodo `map` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice, in ordine di indice crescente.  La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Oltre agli oggetti matrice, il metodo `map` può essere utilizzato da qualsiasi oggetto con una proprietà `length` e con nomi delle proprietà indicizzati numericamente.  
  
## Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, index, array1)`  
  
 È possibile dichiarare la funzione di callback utilizzando fino a tre parametri.  
  
 Nella tabella seguente sono elencati i parametri della funzione di callback.  
  
|Argomento di callback|Definizione|  
|---------------------------|-----------------|  
|`value`|Valore dell'elemento della matrice.|  
|`index`|Indice numerico dell'elemento della matrice.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## Modifica dell'oggetto matrice  
 L'oggetto matrice può essere modificato dalla funzione di callback.  
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `map`.  
  
|Condizione dopo l'avvio del metodo `map`|Elemento passato alla funzione di callback?|  
|----------------------------------------------|-------------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `map`.  
  
```javascript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'argomento `thisArg`, che specifica un oggetto a cui la parola chiave `this` può fare riferimento.  
  
```javascript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## Esempio  
 Nell'esempio seguente un metodo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] incorporato viene utilizzato come funzione di callback.  
  
```javascript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## Esempio  
 Il metodo `map` può essere applicato a una stringa.  Questa condizione è illustrata nell'esempio seguente.  
  
```javascript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Metodi JavaScript](../../javascript/reference/javascript-methods.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)   
 [Metodo filter \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Metodo forEach \(Array\)](../../javascript/reference/foreach-method-array-javascript.md)   
 [Applicazione di esempio JavaScript Hilo \(Windows Store\)](http://hilojs.codeplex.com/SourceControl/latest)