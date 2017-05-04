---
title: "Operatore XOR bit per bit (^) (JavaScript) | Microsoft Docs"
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
  - "^"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "bit per bit (operatori), XOR (operatore)"
  - "XOR (operatore)"
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operatore XOR bit per bit (^) (JavaScript)
Esegue un'operazione OR esclusiva bit per bit tra due espressioni.  
  
## Sintassi  
  
```  
  
result = expression1 ^ expression2  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## Note  
 L'operatore **^** esamina la rappresentazione binaria dei valori delle due espressioni ed esegue un'operazione OR esclusiva bit per bit.  Il risultato di questa operazione viene valutato nel modo seguente:  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 È sufficiente anche un solo bit con valore 1 nella stessa posizione per avere 1 anche nel risultato.  In caso contrario, nel risultato tale bit sarà 0.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore di assegnazione XOR bit per bit \(^\=\)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)