---
title: "Operatore di assegnazione XOR bit per bit (^=) (JavaScript) | Microsoft Docs"
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
  - "^="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "^= (operatore)"
  - "^= (operatore), informazioni sull'operatore ^="
  - "operatori di assegnazione, bit per bit [JavaScript]"
  - "bit per bit (operatori), XOR (operatore)"
  - "XOR (operatore)"
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operatore di assegnazione XOR bit per bit (^=) (JavaScript)
Esegue un'operazione OR esclusiva bit per bit tra una variabile e un'espressione e assegna il risultato alla variabile.  
  
## Sintassi  
  
```  
  
result ^= expression  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression*  
 Qualsiasi espressione.  
  
## Note  
 Utilizzare l'operatore **^\=** equivale esattamente a specificare:  
  
```javascript  
result = result ^ expression  
```  
  
 L'operatore **^\=** esamina la rappresentazione binaria dei valori delle due espressioni ed esegue un'operazione OR esclusiva bit per bit.  Il risultato di questa operazione viene valutato nel modo seguente:  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 È sufficiente anche un solo bit con valore 1 nella stessa posizione per avere 1 anche nel risultato.  In caso contrario, nel risultato tale bit sarà 0.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore XOR bit per bit \(^\)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)