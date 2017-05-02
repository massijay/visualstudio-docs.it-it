---
title: "Metodo indexOf (Array) (JavaScript) | Microsoft Docs"
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
  - "matrici [JavaScript], indexOf (metodo)"
  - "indexOf (metodo) [JavaScript]"
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Metodo indexOf (Array) (JavaScript)
Restituisce l'indice della prima occorrenza di un valore incluso in una matrice.  
  
## Sintassi  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### Parametri  
  
|Parametro|Definizione|  
|---------------|-----------------|  
|`array1`|Obbligatorio.  Oggetto matrice.|  
|`searchElement`|Obbligatorio.  Valore da individuare in `array1`.|  
|`fromIndex`|Facoltativo.  Indice di matrice da cui iniziare la ricerca.  Se `fromIndex` viene omesso, la ricerca inizia in corrispondenza dell'indice 0.|  
  
## Valore restituito  
 Indice della prima occorrenza di `searchElement` nella matrice oppure \-1 se `searchElement` non viene trovato.  
  
## Note  
 Il metodo `indexOf` cerca una matrice per un valore specificato.  Il metodo restituisce l'indice della prima occorrenza oppure \-1 se il valore specificato non viene trovato.  
  
 La ricerca viene eseguita in ordine di indice crescente.  
  
 Gli elementi della matrice vengono confrontati con il valore `searchElement` tramite l'identità, simile all'operatore `===`.  Per ulteriori informazioni, vedi [Operatori di confronto](../../javascript/reference/comparison-operators-javascript.md).  
  
 L'argomento `fromIndex` facoltativo specifica l'indice di matrice da cui iniziare la ricerca.  Se `fromIndex` è maggiore o uguale alla lunghezza della matrice, viene restituito \-1.  Se `fromIndex` è negativo, la ricerca inizia a partire dalla lunghezza della matrice più `fromIndex`.  
  
## Esempio  
 Negli esempi seguenti viene illustrato l'utilizzo del metodo `indexOf`.  
  
```javascript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Vedere anche  
 [Metodi JavaScript](../../javascript/reference/javascript-methods.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)