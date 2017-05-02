---
title: "Metodo apply (Function) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "apply"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "apply (metodo)"
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Metodo apply (Function) (JavaScript)
Chiama la funzione, sostituendo l'oggetto specificato per il valore `this` della funzione e la matrice specificata con gli argomenti della funzione.  
  
## Sintassi  
  
```  
apply([thisObj[,argArray]])  
```  
  
## Parametri  
 `thisObj`  
 Facoltativo.  Oggetto da utilizzare come oggetto `this`.  
  
 `argArray`  
 Facoltativo.  Set di argomenti da passare alla funzione.  
  
## Note  
 Se `argArray` non è un oggetto valido, si verifica un errore "Previsto oggetto".  
  
 Se non viene fornito né l'argomento `argArray` né `thisObj`, l'oggetto `this` originale verrà utilizzato come `thisObj` e non verrà passato alcun argomento.  
  
## Esempio  
 Nel codice seguente viene illustrato come utilizzare il metodo apply.  
  
```javascript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)