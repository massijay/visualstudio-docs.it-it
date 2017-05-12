---
title: "Operatore AND bit per bit (&amp;) (JavaScript) | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operatori di assegnazione, bit per bit [JavaScript]"
  - "& (operatore), informazioni"
  - "AND (operatore)"
  - "& (operatore)"
  - "operatori bit per bit, operatore AND"
  - "& (operatore), operatori bit per bit"
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operatore AND bit per bit (&amp;) (JavaScript)
Esegue un'operazione AND bit per bit tra due espressioni a 32 bit.  
  
## Sintassi  
  
```  
  
result = expression1 & expression2  
```  
  
## Parametri  
 `result`  
 Risultato dell'operazione.  
  
 `expression1`  
 Qualsiasi espressione.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## Note  
 `&` esegue un'operazione AND bit per bit su ognuno dei bit di due espressioni a 32 bit.  Se entrambi i bit sono 1, il risultato è 1.  In caso contrario, il risultato è 0.  
  
|Bit1|Bit2|Valore restituito da AND|  
|----------|----------|------------------------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 Negli esempi seguenti viene illustrato l'utilizzo dell'operatore `&`.  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore di assegnazione AND bit per bit \(&\=\)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)