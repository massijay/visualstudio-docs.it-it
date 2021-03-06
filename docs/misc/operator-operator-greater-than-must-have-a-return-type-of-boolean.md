---
title: "L&#39;operatore &#39;&lt;operatore&gt;&#39; deve avere come tipo restituito un valore booleano | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33023"
  - "bc33023"
helpviewer_keywords: 
  - "BC33023"
ms.assetid: 18e066f4-d71e-4e38-b0bc-8af9145f6015
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L&#39;operatore &#39;&lt;operatore&gt;&#39; deve avere come tipo restituito un valore booleano
Un operatore di confronto o logico è dichiarato con un tipo restituito diverso dal [Boolean Data Type](/dotnet/visual-basic/language-reference/data-types/boolean-data-type).  
  
 Il risultato di un operatore di confronto \(`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `IsFalse`, `IsTrue`, `Like`, `TypeOf`\) può essere solo `True` o `False`. Per altre informazioni, vedere [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators).  
  
 Gli operatori logici \(`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`\) funzionano interamente all'interno del dominio di valori booleani. Per altre informazioni, vedere [Logical and Bitwise Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators).  
  
 **ID errore:** BC33023  
  
### Per correggere l'errore  
  
-   Sostituire il tipo restituito dell'operatore di confronto o logico con `Boolean`.  
  
## Vedere anche  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)