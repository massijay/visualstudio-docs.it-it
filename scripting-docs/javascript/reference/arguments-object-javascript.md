---
title: "Oggetto Arguments (JavaScript) | Microsoft Docs"
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
  - "arguments (oggetto)"
  - "argomenti, arguments (oggetto)"
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Oggetto Arguments (JavaScript)
Un oggetto che rappresenta gli argomenti della funzione attualmente in esecuzione e la funzione che lo ha chiamato.  
  
## Sintassi  
  
```  
[function.]arguments[n]  
```  
  
## Parametri  
 *funzione*  
 Opzionale.  Nome dell'oggetto `Function` correntemente in esecuzione.  
  
 *n*  
 Necessario.  L'indice in base zero dei valori degli argomenti passati all'oggetto `Function`.  
  
## Note  
 Non è possibile creare in modo esplicito un oggetto **arguments**.  L'oggetto **arguments** diventa disponibile solo quando una funzione inizia l'esecuzione.  Benché l'oggetto **arguments** della funzione non sia una matrice, la modalità di accesso ai singoli argomenti è analoga a quella degli elementi di una matrice.  L'indice *n* è in realtà un riferimento a una proprietà **0** ***n*** dell'oggetto **arguments**.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'oggetto **arguments**:  
  
```javascript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Proprietà 0...n \(arguments\)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [Proprietà callee \(arguments\)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [Proprietà length \(arguments\)](../../javascript/reference/length-property-arguments-javascript.md)