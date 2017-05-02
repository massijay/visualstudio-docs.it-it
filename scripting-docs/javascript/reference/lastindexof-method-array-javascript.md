---
title: "Metodo lastIndexOf (Array) (JavaScript) | Microsoft Docs"
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
  - "matrici [JavaScript], lastIndexOf (metodo)"
  - "lastIndexOf (metodo) [JavaScript]"
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Metodo lastIndexOf (Array) (JavaScript)
Restituisce l'indice dell'ultima occorrenza di un valore specificato in una matrice.  
  
## Sintassi  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`array1`|Obbligatorio.  Oggetto matrice da cercare.|  
|`searchElement`|Obbligatorio.  Valore da individuare in `array1`.|  
|`fromIndex`|Facoltativo.  Indice di matrice da cui iniziare la ricerca.  Se `fromIndex` viene omesso, la ricerca inizia dall'ultimo indice nella matrice.|  
  
## Valore restituito  
 Indice dell'ultima occorrenza di `searchElement` nella matrice oppure \-1 se `searchElement` non viene trovato.  
  
## Note  
 Il metodo `lastIndexOf` cerca una matrice per un valore specificato.  Il metodo restituisce l'indice della prima occorrenza oppure \-1 se il valore specificato non viene trovato.  
  
 La ricerca viene eseguita in ordine di indice decrescente \(ultimo membro per primo\).  Per eseguire la ricerca in ordine crescente, utilizzare [Metodo indexOf \(Array\)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Gli elementi della matrice vengono confrontati con il valore `searchElement` tramite l'identità, simile al confronto eseguito dall'operatore `===`.  Per ulteriori informazioni, vedi [Operatori di confronto](../../javascript/reference/comparison-operators-javascript.md).  
  
 L'argomento `fromIndex` facoltativo specifica l'indice di matrice da cui iniziare la ricerca.  Se `fromIndex` è maggiore o uguale alla lunghezza della matrice, viene cercata l'intera matrice.  Se `fromIndex` è negativo, la ricerca inizia a partire dalla lunghezza della matrice più `fromIndex`.  Se l'indice calcolato è minore di 0, viene restituito \-1.  
  
## Esempio  
 Negli esempi seguenti viene illustrato l'utilizzo del metodo `lastIndexOf`.  
  
```javascript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Metodo indexOf \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)