---
title: "Propriet&#224; arguments (Function) (JavaScript) | Microsoft Docs"
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
  - "arguments"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "argomenti, proprietà arguments"
  - "Arguments (proprietà)"
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Propriet&#224; arguments (Function) (JavaScript)
Ottiene gli argomenti per l'oggetto `Function` attualmente in esecuzione.  
  
## Sintassi  
  
```  
  
function.arguments  
```  
  
## Note  
 L'argomento `function` è il nome della funzione attualmente in esecuzione e può essere omesso.  
  
 Questa proprietà consente a una funzione di gestire un numero variabile di argomenti.  La proprietà **length** dell'oggetto `arguments` contiene il numero di argomenti passati alla funzione.  È possibile accedere ai singoli argomenti contenuti nell'oggetto `arguments` nello stesso modo degli elementi di una matrice.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della proprietà `arguments`:  
  
```javascript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vedere anche  
 [Oggetto Arguments](../../javascript/reference/arguments-object-javascript.md)   
 [Istruzione function](../../javascript/reference/function-statement-javascript.md)