---
title: "Operatore di assegnazione OR bit per bit (|=) (JavaScript) | Microsoft Docs"
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
  - "|="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|= (operatore)"
  - "operatori di assegnazione, bit per bit [JavaScript]"
  - "bit per bit (operatori), operatore OR"
  - "operatore OR"
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operatore di assegnazione OR bit per bit (|=) (JavaScript)
Esegue un'operazione OR bit per bit tra il valore di una variabile e il valore di un'espressione e assegna il risultato alla variabile.  
  
## Sintassi  
  
```  
  
result |= expression  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression*  
 Qualsiasi espressione.  
  
## Note  
 Utilizzare questo operatore equivale esattamente a specificare:  
  
```javascript  
result = result | expression  
```  
  
 L'operatore **&#124;\=** esamina la rappresentazione binaria dei valori di *result* ed *expression* ed esegue un'operazione OR bit per bit.  Il risultato di questa operazione viene valutato nel modo seguente:  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 È sufficiente che uno dei bit nella stessa posizione abbia valore 1 perché si abbia 1 nella corrispondente posizione nel risultato.  In caso contrario, nel risultato tale bit sarà 0.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore OR bit per bit \(&#124;\)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)