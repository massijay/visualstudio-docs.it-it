---
title: "Operatore typeof (JavaScript) | Microsoft Docs"
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
  - "typeof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "typeof (operatore)"
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operatore typeof (JavaScript)
Restituisce una stringa che identifica il tipo di dati di un'espressione.  
  
## Sintassi  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## Note  
 L'argomento *espressione* rappresenta qualsiasi espressione per la quale è stata trovata l'informazione del tipo.  
  
 Mediante l'operatore `typeof` vengono restituite le informazioni sul tipo in formato stringa.  I sei possibili valori restituiti da `typeof` sono: "number", "string", "boolean", "object", "function" e "undefined".  
  
 Le parentesi indicate nella sintassi di `typeof` sono facoltative.  
  
## Esempio  
 Nell'esempio verifica il tipo di dati delle variabili.  
  
```javascript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## Esempio  
 Il seguente esempio consente di verificare il tipo di dati di `undefined` per le variabili dichiarate e implicite.  
  
```javascript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Funzione Array.isArray](../../javascript/reference/array-isarray-function-javascript.md)   
 [Funzione Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Costante undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [Operatori di confronto](../../javascript/reference/comparison-operators-javascript.md)   
 [Riepilogo dei tipi di dati](../../javascript/data-types-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)