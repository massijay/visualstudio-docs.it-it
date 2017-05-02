---
title: "Istruzione for...in (JavaScript) | Microsoft Docs"
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
  - "iterazione (istruzioni), istruzione for...in"
  - "cicli (strutture), istruzioni for...in"
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Istruzione for...in (JavaScript)
Esegue una o più istruzioni per ogni proprietà di un oggetto o per ogni elemento di una matrice.  
  
## Sintassi  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## Parametri  
 `variable`  
 Obbligatorio.  Variabile che può essere il nome di qualsiasi proprietà di `object` o l'indice di qualsiasi elemento di `array`.  
  
 `object`, `array`  
 Facoltativo.  Oggetto o matrice su cui eseguire l'iterazione.  
  
 `statements`  
 Facoltativo.  Una o più istruzioni da eseguire per ogni proprietà di `object` o per ogni elemento di `array`.  Può trattarsi di un'istruzione composta.  
  
## Note  
 All'inizio di ogni iterazione di un ciclo, il valore di `variable` è il nome della proprietà successiva di `object` o l'indice dell'elemento successivo di `array`.  Si può quindi utilizzare `variable` in qualsiasi istruzione all'interno del ciclo per fare riferimento alla proprietà di `object` o all'elemento di `array`.  
  
 Le proprietà di un oggetto non vengono assegnate in modo specifico.  Non si può specificare una determinata proprietà in base al relativo indice, ma solo in base al nome della proprietà.  
  
 Lo scorrimento di una matrice viene eseguito nell'ordine dell'elemento, ovvero 0, 1, 2.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'istruzione `for...in` con un oggetto utilizzato come matrice associativa.  
  
```javascript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## Esempio  
 In questo esempio viene illustrato l'utilizzo dell'istruzione `for ... in` per scorrere un oggetto `Array` che include proprietà expando.  
  
```javascript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Utilizzare l'oggetto `Enumerator` per scorrere i membri di una raccolta.  
  
## Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vedere anche  
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Istruzione while](../../javascript/reference/while-statement-javascript.md)