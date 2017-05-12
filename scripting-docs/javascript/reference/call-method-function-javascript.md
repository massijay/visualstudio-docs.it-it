---
title: "Metodo call (Function) (JavaScript) | Microsoft Docs"
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
  - "call"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "call (metodo)"
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Metodo call (Function) (JavaScript)
Chiama un metodo di un oggetto, sostituendo l'oggetto corrente con un altro oggetto.  
  
## Sintassi  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## Parametri  
 `thisObj`  
 Opzionale.  Oggetto da utilizzare come oggetto corrente.  
  
 `arg1, arg2, , argN`  
 Opzionale.  Elenco di argomenti da passare al metodo.  
  
## Note  
 Il metodo `call` viene utilizzato per chiamare un metodo per conto di un altro oggetto.  Consente di modificare l'oggetto `this` di una funzione del contesto originale nel nuovo oggetto specificato da `thisObj`.  
  
 Se non si specifica il parametro `thisObj`, in sostituzione verrà utilizzato l'oggetto `global`.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare il metodo `call`.  
  
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
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Metodo apply \(Function\)](../../javascript/reference/apply-method-function-javascript.md)