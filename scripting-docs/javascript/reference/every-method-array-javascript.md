---
title: "Metodo every (Array) (JavaScript) | Microsoft Docs"
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
  - "matrici [JavaScript], every (metodo)"
  - "every (metodo)"
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo every (Array) (JavaScript)
Determina se tutti i membri di una matrice soddisfano la condizione specificata.  
  
## Sintassi  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`array1`|Obbligatorio.  Oggetto matrice.|  
|`callbackfn`|Obbligatorio.  Funzione che accetta fino a tre argomenti.  Il metodo `every` chiama la funzione `callbackfn` per ogni elemento in `array1` fino a quando `callbackfn` non restituisce `false` o fino alla fine della matrice.|  
|`thisArg`|Facoltativo.  Oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`.  Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.|  
  
## Valore restituito  
 `true` se la funzione di `callbackfn` restituisce `true` per tutti gli elementi di matrice, in caso contrario, `false`.  Se la matrice non dispone di elementi, il metodo `every` restituisce `true`.  
  
## Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## Note  
 Il metodo `every` chiama la funzione `callbackfn` una volta per ogni elemento nella matrice, in ordine di indice crescente, fino a che la funzione `callbackfn` restituisce `false`.  Se viene rilevato un elemento che fa in modo che `callbackfn` restituisca `false`, il metodo `every` restituisce immediatamente `false`.  In caso contrario, il metodo `every` restituisce `true`.  
  
 La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Oltre agli oggetti matrice, il metodo `every` può essere utilizzato da qualsiasi oggetto con una proprietà `length` e con nomi delle proprietà indicizzati numericamente.  
  
> [!NOTE]
>  Puoi utilizzare [Metodo some \(Array\)](../../javascript/reference/some-method-array-javascript.md) per verificare se la funzione di chiamata restituisce `true` per un elemento di una matrice.  
  
## Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, index, array1)`  
  
 È possibile dichiarare la funzione di callback utilizzando fino a tre parametri.  
  
 Nella tabella seguente sono elencati i parametri della funzione di callback.  
  
|Parametro di callback|Definizione|  
|---------------------------|-----------------|  
|`value`|Valore dell'elemento della matrice.|  
|`index`|Indice numerico dell'elemento della matrice.|  
|`array1`|Oggetto matrice contenente l'elemento.|  
  
## Modifica dell'oggetto matrice  
 L'oggetto matrice può essere modificato dalla funzione di callback.  
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `every`.  
  
|Condizione dopo l'avvio del metodo `every`|Elemento passato alla funzione di callback?|  
|------------------------------------------------|-------------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo `every`.  
  
```javascript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'argomento `thisArg`, che specifica un oggetto a cui la parola chiave `this` può fare riferimento.  
  
```javascript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Metodo some \(Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [Metodo filter \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)