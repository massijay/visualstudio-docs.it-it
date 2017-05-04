---
title: "Istruzione let (JavaScript) | Microsoft Docs"
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
  - "let_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "let (istruzione)"
  - "dichiarazione di variabili, istruzione let"
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Istruzione let (JavaScript)
Dichiara una variabile con ambito di blocco.  
  
## Sintassi  
  
```  
let variable1 = value1  
```  
  
#### Parametri  
 `variable1`  
 Nome della variabile che si sta dichiarando.  
  
 `value1`  
 Valore iniziale assegnato alla variabile.  
  
## Note  
 Utilizzare l'istruzione `let` per dichiarare una variabile, l'ambito della quale è limitato al blocco in cui è dichiarata.  È possibile assegnare valori alle variabili nel momento in cui vengono dichiarate o più avanti nello script.  
  
 Una variabile dichiarata con `let` non può essere utilizzata prima della dichiarazione. In caso contrario verrà restituito un errore.  
  
 Se non si inizializza la variabile nell'istruzione `let`, viene automaticamente assegnato il valore `undefined` [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `let`.  
  
```javascript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Istruzione const](../../javascript/reference/const-statement-javascript.md)   
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Variabili](../../javascript/variables-javascript.md)