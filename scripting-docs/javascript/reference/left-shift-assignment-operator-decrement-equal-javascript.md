---
title: "Operatore di assegnazione left shift (&lt;&lt;=) (JavaScript) | Microsoft Docs"
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
  - "<<="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<<= (operatore) [JavaScript]"
  - "operatore di assegnazione left shift (<<=) [JavaScript]"
  - "left shift (operatori) [JavaScript]"
  - "operatori di assegnazione, JavaScript"
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operatore di assegnazione left shift (&lt;&lt;=) (JavaScript)
Sposta il numero specificato di bit a sinistra e assegna il risultato a `result`.  I bit spostati dall'operazione sono riempiti di 0.  
  
## Sintassi  
  
```  
  
result <<= expression  
```  
  
## Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression`  
 Numero di bit da spostare.  
  
## Note  
 Utilizzare l'operatore `<<=` equivale a specificare `result = result << expression`  
  
 Nell'esempio seguente viene illustrato come utilizzare l'operatore `<<=`.  
  
```javascript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore Left Shift bit per bit \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift bit per bit \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatore Right Shift senza segno \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)