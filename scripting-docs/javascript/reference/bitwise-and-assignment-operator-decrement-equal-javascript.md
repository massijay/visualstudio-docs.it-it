---
title: "Operatore di assegnazione AND bit per bit (&amp;=) (JavaScript) | Microsoft Docs"
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
  - "&="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&= (operatore)"
  - "operatori di assegnazione, bit per bit [JavaScript]"
  - "AND (operatore)"
  - "operatori bit per bit, operatore AND"
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operatore di assegnazione AND bit per bit (&amp;=) (JavaScript)
Imposta il risultato di un'operazione AND bit per bit sul valore di una variabile e sul valore di un'espressione.  La variabile e l'espressione vengono considerate degli interi a 32 bit.  
  
## Sintassi  
  
```  
  
result &= expression  
```  
  
## Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression`  
 Qualsiasi espressione.  
  
## Note  
 Utilizzare questo operatore equivale a specificare:  
  
```javascript  
result = result & expression  
```  
  
 L'[Operatore AND bit per bit \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) esamina la rappresentazione binaria dei valori di `result` e `expression` ed esegue un'operazione AND bit per bit su questi valori.  L'output di questa operazione viene valutato nel modo seguente:  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
  
```  
  
 Ogni volta che in entrambe le espressioni i bit nella stessa posizione hanno valore 1, il bit corrispondente avrà valore 1 anche nel risultato.  In caso contrario, nel risultato tale bit sarà 0.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore AND bit per bit \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)