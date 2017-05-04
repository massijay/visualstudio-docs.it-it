---
title: "Operatore virgola (,) (JavaScript) | Microsoft Docs"
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
  - "%2C"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "comma (operatore)"
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Operatore virgola (,) (JavaScript)
Provoca l'esecuzione in sequenza di due espressioni.  
  
## Sintassi  
  
```  
  
expression1, expression2  
```  
  
## Parametri  
 `expression1`  
 Qualsiasi espressione.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## Note  
 L'operatore `,` determina l'esecuzione delle espressioni nell'ordine da sinistra a destra.  L'operatore `,` viene in genere utilizzato nelle espressioni di incremento dei cicli `for`.  Di seguito è riportato un esempio:  
  
```javascript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 L'istruzione `for` consente di eseguire una sola espressione alla fine di ogni iterazione di un ciclo.  L'operatore `,` consente di considerare più espressioni come un'unica espressione, in modo che tutte le variabili possano essere incrementate.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione for](../../javascript/reference/for-statement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)