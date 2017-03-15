---
title: "Non &#232; possibile combinare &#39;Widening&#39; e &#39;Narrowing&#39; | Microsoft Docs"
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
  - "bc33001"
  - "vbc33001"
helpviewer_keywords: 
  - "BC33001"
ms.assetid: 1c576344-083c-45ad-bc71-0489bd3976be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Non &#232; possibile combinare &#39;Widening&#39; e &#39;Narrowing&#39;
Un'[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) specifica sia [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) che [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing).  
  
 Quando si definisce un operatore di conversione, è necessario dichiararlo come `Widening` o `Narrowing`. Queste caratteristiche si escludono a vicenda, quindi non è possibile specificarle entrambe.  
  
 **ID errore:** BC33001  
  
### Per correggere l'errore  
  
-   Rimuovere la parola chiave `Widening` o `Narrowing` dall'istruzione `Operator`. È necessario specificare una o l'altra.  
  
## Vedere anche  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)