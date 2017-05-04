---
title: "Operatore Right Shift bit per bit (&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">> (operatore)"
  - ">> (operatore), informazioni sull'operatore >>"
  - ">> (operatore), bitsets"
  - "bit per bit (operatori), operatore right shift"
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operatore Right Shift bit per bit (&gt;&gt;) (JavaScript)
Sposta i bit di un'espressione verso destra conservando il segno esistente.  
  
## Sintassi  
  
```  
  
result = expression1 >> expression2  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## Note  
 L'operatore \>\> sposta i bit di *expression1* verso destra del numero di bit specificati in *expression2*.  Il bit del segno di *expression1* viene utilizzato per il riempimento delle cifre da sinistra.  Le cifre spostate verso destra vengono eliminate.  Dopo la valutazione del codice seguente, ad esempio, il valore di *temp* è \-4. Dopo lo spostamento a destra di due bit, infatti, il valore \-14 \(11110010 in un binario del complemento a due\) risulta uguale a \-4 \(11111100 in un binario del complemento a due\).  
  
```javascript  
var temp  
temp = -14 >> 2  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore Left Shift bit per bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore di assegnazione Right Shift \(\>\>\=\)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operatore Right Shift senza segno \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)