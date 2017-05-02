---
title: "Operatore condizionale ternario (?:) (JavaScript) | Microsoft Docs"
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
  - "?:"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Operatore condizionale ternario"
  - "condizionali (operatori)"
  - "ternario"
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operatore condizionale ternario (?:) (JavaScript)
Restituisce una di due espressioni a seconda che una condizione risulti vera o falsa.  
  
## Sintassi  
  
```  
  
test ? expression1 : expression2  
```  
  
## Parametri  
 `test`  
 Espressione booleana qualsiasi.  
  
 `expression1`  
 Espressione restituita se `test` è `true`.  Può essere un'espressione delimitata da virgole.  
  
 `expression2`  
 Espressione restituita se `test` è `false`.  Un'espressione delimitata da virgole può collegare più espressioni.  
  
## Note  
 L'operatore `?:` può essere utilizzato come alternativa rapida all'istruzione `if...else`.  Viene infatti utilizzato come parte di un'espressione più ampia in cui l'utilizzo dell'istruzione `if...else` risulterebbe più complesso.  Di seguito è riportato un esempio.  
  
```javascript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 In questo esempio viene creata una stringa contenente "Good evening.", se l'orario è successivo alle 18.00.  Il codice equivalente utilizzando un'istruzione `if...else` sarebbe analogo al seguente:  
  
```javascript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Applicazione di esempio per un widget di configurazione Script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)