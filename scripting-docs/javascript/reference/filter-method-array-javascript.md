---
title: "Metodo filter (Array) (JavaScript) | Microsoft Docs"
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
  - "matrici [JavaScript], filter (metodo)"
  - "filter (metodo) [JavaScript]"
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# Metodo filter (Array) (JavaScript)
Restituisce gli elementi di una matrice che soddisfano la condizione specificata in una funzione di callback.  
  
## Sintassi  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`array1`|Obbligatorio.  Oggetto matrice.|  
|`callbackfn`|Obbligatorio.  Funzione che accetta fino a tre argomenti.  Il metodo `filter` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice.|  
|`thisArg`|Facoltativo.  Oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`.  Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.|  
  
## Valore restituito  
 Nuova matrice contenente tutti i valori per i quali la funzione di callback restituisce `true`.  Se la funzione di callback restituisce `false` per tutti gli elementi di `array1`, la lunghezza della nuova matrice sarà 0.  
  
## Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## Note  
 Il metodo `filter` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice, in ordine di indice crescente.  La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Oltre agli oggetti matrice, il metodo `filter` può essere utilizzato da qualsiasi oggetto con una proprietà `length` e con nomi delle proprietà indicizzati numericamente.  
  
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
 Il metodo `filter` non modifica direttamente la matrice originale, mentre la funzione di callback può modificarla.  Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `filter`.  
  
|Condizione dopo l'avvio del metodo `filter`|Elemento passato alla funzione di callback?|  
|-------------------------------------------------|-------------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `filter`.  
  
```javascript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## Esempio  
 Nell'esempio seguente, l'argomento `callbackfn` include il codice della funzione di callback.  
  
```javascript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## Esempio  
 Nell'esempio seguente vengono visualizzati i nomi delle proprietà che iniziano con la lettera "css" nell'oggetto DOM `window`.  
  
```javascript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'argomento `thisArg`, che specifica un oggetto a cui la parola chiave `this` può fare riferimento.  
  
```javascript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## Esempio  
 Il metodo `filter` può essere applicato a una stringa invece di una matrice.  Nell'esempio seguente viene illustrato come eseguire questa operazione.  
  
```javascript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)   
 [Metodo map \(Array\)](../../javascript/reference/map-method-array-javascript.md)   
 [Metodo forEach \(Array\)](../../javascript/reference/foreach-method-array-javascript.md)