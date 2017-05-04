---
title: "Metodo reduceRight (Array) (JavaScript) | Microsoft Docs"
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
  - "matrici [JavaScript], reduceRight (metodo)"
  - "reduceRight (metodo) [JavaScript]"
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Metodo reduceRight (Array) (JavaScript)
Chiama la funzione di callback specificata per tutti gli elementi in una matrice, in ordine decrescente.  Il valore restituito della funzione di callback è il risultato accumulato e viene fornito come argomento nella chiamata successiva alla funzione di callback.  
  
## Sintassi  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`array1`|Obbligatorio.  Oggetto matrice.|  
|`callbackfn`|Obbligatorio.  Funzione che accetta fino a quattro argomenti.  Il metodo `reduceRight` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice.|  
|`initialValue`|Facoltativo.  Se specificato, `initialValue` viene utilizzato come valore iniziale per avviare l'accumulo.  La prima chiamata alla funzione `callbackfn` fornisce questo valore come argomento invece di un valore di matrice.|  
  
## Valore restituito  
 Oggetto contenente il risultato accumulato dall'ultima chiamata alla funzione di callback.  
  
## Eccezioni  
 Un'eccezione `TypeError` viene generata quando si verifica una delle seguenti condizioni:  
  
-   L'argomento `callbackfn` non è un oggetto funzione.  
  
-   La matrice non contiene elementi e non viene fornito `initialValue`.  
  
## Note  
 Se viene fornito `initialValue`, il metodo `reduceRight` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice, in ordine di indice decrescente.  Se `initialValue` non viene fornito, il metodo `reduceRight` chiama la funzione `callbackfn` in ogni elemento, a partire dal secondo all'ultimo, in ordine di indice decrescente.  
  
 Il valore restituito della funzione di callback viene fornito come argomento `previousValue` nella chiamata successiva alla funzione di callback.  Il valore restituito dell'ultima chiamata alla funzione di callback è il valore restituito del metodo `reduceRight`.  
  
 La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Per accumulare un risultato in ordine di indice crescente, utilizzare [Metodo reduce \(Array\)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 È possibile dichiarare la funzione di callback utilizzando fino a quattro parametri.  
  
 Nella tabella seguente sono elencati i parametri della funzione di callback.  
  
|Argomento di callback|Definizione|  
|---------------------------|-----------------|  
|`previousValue`|Valore dalla chiamata precedente alla funzione di callback.  Se `initialValue` viene fornito al metodo `reduceRight`, `previousValue` è `initialValue` alla prima chiamata alla funzione.|  
|`currentValue`|Valore dell'elemento della matrice corrente.|  
|`currentIndex`|Indice numerico dell'elemento della matrice corrente.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## Prima chiamata alla funzione di callback  
 La prima volta che la funzione di callback viene chiamata, i valori forniti come argomenti variano a seconda che il metodo `reduceRight` contenga un argomento `initialValue`.  
  
 Se `initialValue` viene fornito al metodo `reduceRight`:  
  
-   Il valore dell'argomento `previousValue` è `initialValue`.  
  
-   L'argomento `currentValue` è il valore dell'ultimo elemento presente nella matrice.  
  
 Se `initialValue` non viene fornito:  
  
-   L'argomento `previousValue` è il valore dell'ultimo elemento presente nella matrice.  
  
-   L'argomento `currentValue` è il valore del secondo all'ultimo elemento presente nella matrice.  
  
## Modifica dell'oggetto matrice  
 L'oggetto matrice può essere modificato dalla funzione di callback.  
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `reduceRight`.  
  
|Condizione dopo l'avvio del metodo `reduceRight`|Elemento passato alla funzione di callback?|  
|------------------------------------------------------|-------------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## Esempio  
 Nell'esempio seguente i valori della matrice vengono concatenati in una stringa, che separa i valori con "::".  Poiché non viene fornito alcun valore iniziale al metodo `reduceRight`, la prima chiamata alla funzione di callback presenta 456 come argomento `previousValue` e 123 come argomento `currentValue`.  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## Esempio  
 Nell'esempio seguente viene trovata la somma dei quadrati degli elementi della matrice.  Il metodo `reduceRight` viene chiamato con un valore iniziale di 0.  
  
```javascript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## Esempio  
 L'esempio seguente consente di ottenere gli elementi di una matrice i cui valori sono compresi tra 1 e 10.  Il valore iniziale fornito al metodo `reduceRight` è una matrice vuota.  
  
```javascript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## Esempio  
 Il metodo `reduceRight` può essere applicato a una stringa.  Nell'esempio seguente viene illustrato come utilizzare il metodo per invertire i caratteri in una stringa.  
  
```javascript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Metodo reduce \(Array\)](../../javascript/reference/reduce-method-array-javascript.md)