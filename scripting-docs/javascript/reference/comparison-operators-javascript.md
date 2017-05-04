---
title: "Operatori di confronto (JavaScript) | Microsoft Docs"
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
  - "Comparison"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operatori di confronto, script"
  - "operatore maggiore di"
  - "operatori di confronto"
  - "operatore maggiore o uguale a"
  - "operatore di disuguaglianza"
  - "operatore di identità"
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Operatori di confronto (JavaScript)
Restituisce un valore booleano che indica il risultato del confronto.  
  
## Sintassi  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## Parametri  
 `expression1`  
 Qualsiasi espressione.  
  
 `comparisonoperator`  
 Qualsiasi operatore di confronto.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## Note  
 Nel confronto di stringhe in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], viene utilizzato il valore del carattere Unicode dell'espressione stringa.  
  
 Di seguito viene descritto il comportamento dei vari gruppi di operatori a seconda del tipo e del valore di `expression1` e `expression2`:  
  
 Operatori relazionali: `<`, `>`, `<=`, `>=`  
  
-   Viene eseguito il tentativo di convertire sia `expression1` sia `expression2` in numeri.  
  
-   Se entrambe le espressioni sono stringhe, viene eseguito un confronto delle stringhe.  
  
-   Se una delle espressioni è `NaN`, viene restituito `false`.  
  
-   Lo zero negativo equivale allo zero positivo.  
  
-   Un infinito negativo è minore di qualsiasi altro valore, compreso se stesso.  
  
-   Un infinito positivo è maggiore di qualsiasi altro valore, compreso se stesso.  
  
 Operatori di uguaglianza: `==`, `!=`  
  
-   Se i tipi delle due espressioni sono diversi, viene eseguito un tentativo di convertirli in stringa, numero o booleano.  
  
-   Il valore `NaN` è diverso da qualsiasi altro valore, compreso se stesso.  
  
-   Lo zero negativo equivale allo zero positivo.  
  
-   `null` equivale sia a `null` sia a `undefined`.  
  
-   I valori sono considerati uguali se sono stringhe identiche, valori numerici equivalenti, oggetti identici, valori booleani identici oppure se, quando di tipo diverso, è possibile assegnarli forzatamente a uno dei tipi precedenti.  
  
-   Qualsiasi altro confronto viene considerato diverso.  
  
 Operatore di identità: `===`, `!==`  
  
 Questi operatori si comportano allo stesso modo degli operatori di uguaglianza, eccetto per il fatto che non viene eseguita alcuna conversione del tipo.  Se i tipi di entrambe le espressioni sono diversi, queste espressioni restituiscono sempre `false`.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)