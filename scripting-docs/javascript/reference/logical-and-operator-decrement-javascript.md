---
title: "Operatore AND logico (&amp;&amp;) (JavaScript) | Microsoft Docs"
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
  - "&&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&& (operatore)"
  - "AND (operatore logico)"
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operatore AND logico (&amp;&amp;) (JavaScript)
Esegue una congiunzione logica tra due espressioni.  
  
## Sintassi  
  
```  
  
result = expression1 && expression2   
```  
  
## Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression1`  
 Qualsiasi espressione.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## Note  
 Se `expression1` viene valutato in `false`, `result` è `expression1`.  In caso contrario, `result` sarà `expression2`.  Di conseguenza, l'operazione restituisce `true` se entrambi gli operandi sono true; in caso contrario, verrà restituito `false`.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilizza le regole seguenti per la conversione di valori non booleani in valori booleani:  
  
-   Tutti gli oggetti sono considerati `true`.  
  
-   Le stringhe sono considerate `false` se sono vuote.  
  
-   `null` e `undefined` sono considerati `false`.  
  
-   Un numero è `false` se è zero.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)