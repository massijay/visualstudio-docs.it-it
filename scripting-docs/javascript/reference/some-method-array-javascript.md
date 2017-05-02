---
title: "Metodo some (Array) (JavaScript) | Microsoft Docs"
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
  - "matrici [JavaScript], some (metodo)"
  - "some (metodo) [JavaScript]"
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Metodo some (Array) (JavaScript)
Determina se la funzione di callback specificata restituisce `true` per tutti gli elementi di una matrice.  
  
## Sintassi  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`array1`|Obbligatorio.  Oggetto matrice.|  
|`callbackfn`|Obbligatorio.  Funzione che accetta fino a tre argomenti.  Il metodo `some` chiama la funzione `callbackfn` per ogni elemento in `array1` fino a quando `callbackfn` non restituisce `true` o fino alla fine della matrice.|  
|`thisArg`|Facoltativo.  Oggetto a cui la parola chiave `this` può fare riferimento nella funzione `callbackfn`.  Se `thisArg` viene omesso, si utilizza `undefined` come valore `this`.|  
  
## Valore restituito  
 `true` se la funzione `callbackfn` restituisce `true` per qualsiasi elemento della matrice; in caso contrario, `false`.  
  
## Eccezioni  
 Se l'argomento `callbackfn` non è un oggetto funzione, viene generata un'eccezione `TypeError`.  
  
## Note  
 Il metodo `some` chiama la funzione `callbackfn` su ogni elemento della matrice, in ordine di indice crescente, fino a quando la funzione `callbackfn` non restituisce `true`.  Se viene rilevato un elemento che fa in modo che `callbackfn` restituisca `true`, il metodo `some` restituisce immediatamente `true`.  Se il callback non restituisce `true` su alcun elemento, il metodo `some` restituisce `false`.  
  
 La funzione di callback non viene chiamata per gli elementi mancanti della matrice.  
  
 Oltre agli oggetti matrice, il metodo `some` può essere utilizzato da qualsiasi oggetto con una proprietà `length` e con nomi delle proprietà indicizzati numericamente.  
  
> [!NOTE]
>  È possibile utilizzare [Metodo every \(Array\)](../../javascript/reference/every-method-array-javascript.md) per verificare se la funzione di callback restituisce `true` per tutti gli elementi di una matrice.  
  
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
  
 Nella tabella seguente vengono descritti i risultati della modifica dell'oggetto matrice dopo l'avvio del metodo `some`.  
  
|Condizione dopo l'avvio del metodo `some`|Elemento passato alla funzione di callback?|  
|-----------------------------------------------|-------------------------------------------------|  
|L'elemento viene aggiunto oltre la lunghezza originale della matrice.|No.|  
|L'elemento viene aggiunto per inserire un elemento mancante della matrice.|Sì, se tale indice non è stato ancora passato alla funzione di callback.|  
|L'elemento è stato modificato.|Sì, se tale elemento non è stato ancora passato alla funzione di callback.|  
|L'elemento viene eliminato dalla matrice.|No, a meno che tale elemento non sia già stato passato alla funzione di callback.|  
  
## Esempio  
 Nell'esempio seguente viene utilizzato il metodo `some` per verificare se gli elementi di una matrice sono uguali.  
  
```javascript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il parametro `thisArg`, che specifica un oggetto a cui la parola chiave `this` può fare riferimento.  Controlla se uno dei numeri in una matrice non rientra nell'intervallo specificato da un oggetto passato.  
  
```javascript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Metodo every \(Array\)](../../javascript/reference/every-method-array-javascript.md)   
 [Metodo filter \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Metodo map \(Array\)](../../javascript/reference/map-method-array-javascript.md)