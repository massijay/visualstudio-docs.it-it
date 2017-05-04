---
title: "Operatore OR logico (||) (JavaScript) | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|| (operatore)"
  - "OR (operatore logico)"
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Operatore OR logico (||) (JavaScript)
Esegue una disgiunzione logica tra due espressioni.  
  
## Sintassi  
  
```  
  
result = expression1 || expression2  
```  
  
## Parametri  
 *result*  
 Qualsiasi variabile.  
  
 *expression1*  
 Qualsiasi espressione.  
  
 *expression2*  
 Qualsiasi espressione.  
  
## Note  
 Se una o entrambe le espressioni restituiscono **True**, *result* sarà **True**.  Nella tabella seguente viene illustrata la modalità di determinazione di *result*:  
  
|Se `expression1` è|Ed `expression2` è|`result` sarà|  
|------------------------|------------------------|-------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] si utilizzano le seguenti regole per la conversione di valori non booleani in valori booleani:  
  
-   Tutti gli oggetti sono considerati true.  
  
-   Le stringhe sono considerate false se, e solo se, sono vuote.  
  
-   `null` e undefined sono considerati false.  
  
-   I valori numerici sono false se, e solo se, sono uguali a 0.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)