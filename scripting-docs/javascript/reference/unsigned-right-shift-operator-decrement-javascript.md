---
title: "Operatore Right Shift senza segno (&gt;&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>> (operatore)"
  - "operatore right Shift senza segno (>>>)"
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operatore Right Shift senza segno (&gt;&gt;&gt;) (JavaScript)
Consente di spostare verso destra i bit di un'espressione ignorando il segno.  
  
## Sintassi  
  
```  
  
result = expression1 >>> expression2  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## Note  
 L'operatore **\>\>\>** sposta i bit di *expression1* verso destra del numero di bit specificati in *expression2*.  Gli zeri di riempimento vengono inseriti da sinistra.  Le cifre spostate verso destra vengono eliminate.  Di seguito è riportato un esempio:  
  
```javascript  
var temp  
temp = -14 >>> 2  
```  
  
 La variabile *temp* ha un valore iniziale \-14 \(11111111 11111111 11111111 11110010 in un binario del complemento a due\).  Dopo lo spostamento a destra di due bit, il valore è pari a 1073741820 \(00111111 11111111 11111111 11111100 in formato binario\).  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore di assegnazione Right Shift senza segno \(\>\>\>\=\)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operatore Left Shift bit per bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift bit per bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)