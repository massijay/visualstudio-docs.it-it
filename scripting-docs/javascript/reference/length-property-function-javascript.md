---
title: "Propriet&#224; length (Function) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length (proprietà)"
  - "length (proprietà) (function)"
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Propriet&#224; length (Function) (JavaScript)
Ottiene il numero di argomenti definiti per una funzione.  
  
## Sintassi  
  
```  
  
functionName.length  
```  
  
## Note  
 L'argomento *functionName* richiesto è il nome della funzione.  
  
 La proprietà **length** di una funzione viene inizializzata dal motore di scripting sul numero di argomenti inclusi nella definizione della funzione stessa, quando viene creata un'istanza della funzione.  
  
 L'azione eseguita quando una funzione viene richiamata con un numero di argomenti diverso dal valore della proprietà **length** dipende dalla funzione.  
  
## Esempio  
 Nel codice seguente viene illustrato l'utilizzo della proprietà **length**:  
  
```javascript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vedere anche  
 [Proprietà arguments \(Function\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Proprietà length \(Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [Proprietà length \(String\)](../../javascript/reference/length-property-string-javascript.md)