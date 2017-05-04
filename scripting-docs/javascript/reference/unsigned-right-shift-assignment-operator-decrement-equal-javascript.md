---
title: "Operatore di assegnazione Right Shift senza segno (&gt;&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>>= (operatore)"
  - "operatori di assegnazione, JavaScript"
  - "operatore di assegnazione right shift senza segno (>>>=)"
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Operatore di assegnazione Right Shift senza segno (&gt;&gt;&gt;=) (JavaScript)
Sposta il valore di una variabile verso destra del numero di bit specificati nel valore di un'espressione, ignorando il segno, e assegna il risultato alla variabile.  
  
## Sintassi  
  
```  
  
result >>>= expression  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression*  
 Qualsiasi espressione.  
  
## Note  
 Utilizzare l'operatore \>\>\>\= equivale esattamente a specificare quanto segue:  
  
```javascript  
result = result >>> expression  
```  
  
 L'operatore **\>\>\>\=** sposta i bit di *result* verso destra del numero di bit specificati in *expression*.  Gli zeri di riempimento vengono inseriti da sinistra.  Le cifre spostate verso destra vengono eliminate.  Di seguito è riportato un esempio:  
  
```javascript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 La variabile *temp* ha un valore iniziale di \-14 \(11111111 11111111 11111111 11110010 in un binario del complemento a due\).  Dopo lo spostamento a destra di due bit, il valore è pari a 1073741820 \(00111111 11111111 11111111 11111100 in formato binario\).  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore Right Shift senza segno \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operatore Left Shift bit per bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift bit per bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)