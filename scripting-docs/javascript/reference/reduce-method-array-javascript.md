---
title: "Metodo reduce (Array) (JavaScript) | Microsoft Docs"
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
  - "matrici [JavaScript], reduce (metodo)"
  - "funzione di callback, reduce (metodo) [JavaScript]"
  - "reduce (metodo) [JavaScript]"
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Metodo reduce (Array) (JavaScript)
Chiama la funzione di callback specificata per tutti gli elementi in una matrice.  Il valore restituito della funzione di callback è il risultato accumulato e viene fornito come argomento nella chiamata successiva alla funzione di callback.  
  
## Sintassi  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`array1`|Obbligatorio.  Oggetto matrice.|  
|`callbackfn`|Obbligatorio.  Funzione che accetta fino a quattro argomenti.  Il metodo `reduce` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice.|  
|`initialValue`|Facoltativo.  Se specificato, `initialValue` viene utilizzato come valore iniziale per avviare l'accumulo.  La prima chiamata alla funzione `callbackfn` fornisce questo valore come argomento invece di un valore di matrice.|  
  
## Valore restituito  
 Risultato accumulato dall'ultima chiamata alla funzione di callback.  
  
## Eccezioni  
 Un'eccezione `TypeError` viene generata quando si verifica una delle seguenti condizioni:  
  
-   L'argomento `callbackfn` non è un oggetto funzione.  
  
-   La matrice non contiene elementi e non viene fornito `initialValue`.  
  
## Note  
 Se viene fornito `initialValue`, il metodo `reduce` chiama la funzione `callbackfn` una volta per ogni elemento presente nella matrice, in ordine di indice crescente.  Se `initialValue` non viene fornito, il metodo `reduce` chiama la funzione `callbackfn` in ogni elemento, a partire dal secondo.  
  
 Il valore restituito della funzione di callback viene fornito come argomento `previousValue` nella chiamata successiva alla funzione di callback.  Il valore restituito dell'ultima chiamata alla funzione di callback è il valore restituito del metodo `reduce`.  
  
 La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
> [!NOTE]
>  [Metodo reduceRight \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md) elabora gli elementi in ordine di indice decrescente.  
  
## Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 È possibile dichiarare la funzione di callback utilizzando fino a quattro parametri.  
  
 Nella tabella seguente sono elencati i parametri della funzione di callback.  
  
|Argomento di callback|Definizione|  
|---------------------------|-----------------|  
|`previousValue`|Valore dalla chiamata precedente alla funzione di callback.  Se `initialValue` viene fornito al metodo `reduce`, `previousValue` è `initialValue` alla prima chiamata alla funzione.|  
|`currentValue`|Valore dell'elemento della matrice corrente.|  
|`currentIndex`|Indice numerico dell'elemento della matrice corrente.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## Prima chiamata alla funzione di callback  
 La prima volta che la funzione di callback viene chiamata, i valori forniti come argomenti variano a seconda che il metodo `reduce` contenga un argomento `initialValue`.  
  
 Se `initialValue` viene fornito al metodo reduce:  
  
-   Il valore dell'argomento `previousValue` è `initialValue`.  
  
-   L'argomento `currentValue` è il valore del primo elemento presente nella matrice.  
  
 Se `initialValue` non viene fornito:  
  
-   L'argomento `previousValue` è il valore del primo elemento presente nella matrice.  
  
-   L'argomento `currentValue` è il valore del secondo elemento presente nella matrice.  
  
## Modifica dell'oggetto matrice  
 L'oggetto matrice può essere modificato dalla funzione di callback.  
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `reduce`.  
  
|Condizione dopo l'avvio del metodo `reduce`|Elemento passato alla funzione di callback?|  
|-------------------------------------------------|-------------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## Esempio  
 Nell'esempio seguente i valori della matrice vengono concatenati in una stringa, che separa i valori con "::".  Poiché non viene fornito alcun valore iniziale al metodo `reduce`, la prima chiamata alla funzione di callback presenta "abc" come argomento `previousValue` e "def" come argomento `currentValue`.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## Esempio  
 Nell'esempio seguente vengono aggiunti i valori di una matrice dopo l'arrotondamento.  Il metodo `reduce` viene chiamato con un valore iniziale di 0.  
  
```javascript  
// Define the callback function.  
function addRounded (previousValue, currentValue) {  
    return previousValue + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## Esempio  
 Nell'esempio seguente vengono aggiunti i valori in una matrice.  I parametri `currentIndex` e `array1` vengono utilizzati nella funzione di callback.  
  
```javascript  
function addDigitValue(previousValue, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return previousValue + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## Esempio  
 Nell'esempio seguente si ottiene una matrice contenente solo i valori compresi tra 1 e 10 in un'altra matrice.  Il valore iniziale fornito al metodo `reduce` è una matrice vuota.  
  
```javascript  
function Process(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Metodo reduceRight \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md)