---
title: "Gli operatori devono essere dichiarati &#39;Public&#39; | Microsoft Docs"
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
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gli operatori devono essere dichiarati &#39;Public&#39;
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) non include la parola chiave [Public](/dotnet/visual-basic/language-reference/modifiers/public).  
  
 Una routine `Operator` richiede le parole chiave `Public` e [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) e anche un operatore di conversione richiede la parola chiave [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) o [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 **ID errore:** BC33011  
  
### Per correggere l'errore  
  
-   Aggiungere la parola chiave `Public` all'istruzione `Operator`.  
  
## Vedere anche  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)