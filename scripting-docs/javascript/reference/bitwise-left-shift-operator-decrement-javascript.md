---
title: "Operatore Left Shift bit per bit (&lt;&lt;) (JavaScript) | Microsoft Docs"
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
  - "<<"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<< (operatore)"
  - "<< (operatore), informazioni sull'operatore <<"
  - "bit per bit (operatori), operatore Left Shift"
  - "left shift (operatori)"
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operatore Left Shift bit per bit (&lt;&lt;) (JavaScript)
Sposta verso sinistra i bit di un'espressione.  
  
## Sintassi  
  
```  
  
result = expression1 << expression2  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## Note  
 L'operatore **\<\<** sposta i bit di *expression1* verso sinistra del numero di bit specificati in *expression2*.  Di seguito è riportato un esempio:  
  
```javascript  
var temp  
temp = 14 << 2  
```  
  
 Il valore della variabile *temp* è 56 in quanto, dopo uno spostamento a sinistra di due bit, il valore 14 \(00001110 in formato binario\) risulta uguale a 56 \(00111000 in formato binario\).  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore di assegnazione Left Shift \(\<\<\=\)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operatore Right Shift bit per bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift senza segno \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)