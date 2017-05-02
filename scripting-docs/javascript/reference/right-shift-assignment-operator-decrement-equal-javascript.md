---
title: "Operatore di assegnazione Right Shift (&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>= (operatore) [JavaScript]"
  - "operatori di assegnazione, JavaScript"
  - "right shift (operatori) [JavaScript]"
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operatore di assegnazione Right Shift (&gt;&gt;=) (JavaScript)
Sposta il valore di una variabile verso destra del numero di bit specificati nel valore di un'espressione, mantenendo il segno, e assegna il risultato alla variabile.  
  
## Sintassi  
  
```  
  
result >>= expression  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression*  
 Qualsiasi espressione.  
  
## Note  
 Utilizzare l'operatore **\>\>\=** equivale esattamente a specificare:  
  
```javascript  
result = result >> expression  
```  
  
 L'operatore **\>\>\=** sposta i bit di *result* verso destra del numero di bit specificati in *expression*.  Il bit del segno di *result* viene utilizzato per il riempimento delle cifre da sinistra.  Le cifre spostate verso destra vengono eliminate.  Dopo la valutazione del codice seguente, ad esempio, il valore di *temp* è \-4. Dopo lo spostamento a destra di due bit, infatti, il valore 14 \(11110010 in forma binaria\) risulta uguale a \-4 \(11111100 in forma binaria\).  
  
```javascript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore Left Shift bit per bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift bit per bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift senza segno \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)