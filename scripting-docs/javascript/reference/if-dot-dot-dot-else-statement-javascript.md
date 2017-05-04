---
title: "Istruzione if...else (JavaScript) | Microsoft Docs"
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
  - "else_JavaScriptKeyword"
  - "if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "if (istruzione), if...else"
  - "cicli (strutture), istruzioni if...else"
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Istruzione if...else (JavaScript)
Esegue un gruppo di istruzioni in base a determinate condizioni, a seconda del valore di un espressione.  
  
## Sintassi  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## Parametri  
 `condition1`  
 Obbligatorio.  Espressione booleana.  Se `condition1` è `null` o `undefined`, `condition1` viene considerato come `false`.  
  
 `statement1`  
 Facoltativo.  Istruzione da eseguire se `condition1` è **true**.  Può trattarsi di un'istruzione composta.  
  
 `condition2`  
 Condizione da valutare.  
  
 `statement2`  
 Facoltativo.  Istruzione da eseguire se `condition2` è `true`.  Può trattarsi di un'istruzione composta.  
  
 `statement3`  
 Se `condition1` e `condition2` sono `false`, viene eseguita questa istruzione.  
  
## Esempio  
 Nel codice seguente viene illustrato come utilizzare `if`, `if else` e `else`.  
  
 Per motivi di chiarezza e per evitare errori involontari, è buona norma racchiudere `statement1` e `statement2` tra parentesi graffe \({}\).  
  
```javascript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore condizionale ternario \(?:\)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)