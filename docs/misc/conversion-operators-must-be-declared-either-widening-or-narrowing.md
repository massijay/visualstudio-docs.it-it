---
title: "Gli operatori di conversione devono essere dichiarati &#39;Widening&#39; o &#39;Narrowing&#39; | Microsoft Docs"
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
  - "vbc33017"
  - "bc33017"
helpviewer_keywords: 
  - "BC33017"
ms.assetid: 5972d955-ce1d-4348-a021-167eecb3a507
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gli operatori di conversione devono essere dichiarati &#39;Widening&#39; o &#39;Narrowing&#39;
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) non specifica [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) o [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 Quando si definisce un operatore di conversione, è necessario dichiararlo come `Widening` o `Narrowing`. Queste caratteristiche si escludono a vicenda, quindi non è possibile specificarle entrambe.  
  
 **ID errore:** BC33017  
  
### Per correggere l'errore  
  
-   Decidere se l'operatore di conversione deve essere `Widening` o `Narrowing` e includere la parola chiave appropriata nell'istruzione `Operator`. È necessario specificare una o l'altra.  
  
## Vedere anche  
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)