---
title: "Istruzione const (JavaScript) | Microsoft Docs"
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
  - "const_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dichiarazione di variabili, istruzione const"
  - "const (istruzione)"
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Istruzione const (JavaScript)
Dichiara una variabile con ambito di blocco con un valore costante.  
  
## Sintassi  
  
```  
const constant1 = value1  
```  
  
#### Parametri  
 `constant1`  
 Nome della variabile che si sta dichiarando.  
  
 `value1`  
 Valore iniziale assegnato alla variabile.  
  
## Note  
 Utilizzare l'istruzione `const` per dichiarare una variabile con un valore costante, l'ambito della quale è limitato al blocco in cui è dichiarata.  Il valore della variabile non può essere modificato.  
  
 Una variabile dichiarata utilizzando `const` deve essere inizializzata al momento della dichiarazione.  
  
## Esempio  
 Nel codice seguente viene illustrato l'utilizzo dell'istruzione `const`.  
  
```javascript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Istruzione let](../../javascript/reference/let-statement-javascript.md)   
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Oggetto Array](../../javascript/reference/array-object-javascript.md)   
 [Variabili](../../javascript/variables-javascript.md)