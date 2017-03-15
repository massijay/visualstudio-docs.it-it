---
title: "Solo gli operatori di conversione possono essere dichiarati come &#39;&lt;parolachiave&gt;&#39; | Microsoft Docs"
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
  - "bc33019"
  - "vbc33019"
helpviewer_keywords: 
  - "BC33019"
ms.assetid: 946266fe-a909-41b1-aad4-f85dc8050b88
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Solo gli operatori di conversione possono essere dichiarati come &#39;&lt;parolachiave&gt;&#39;
Un'[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) specifica [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) o [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) quando l'operatore non è un operatore di conversione.  
  
 Ogni operatore deve essere dichiarato sia come [Public](/dotnet/visual-basic/language-reference/modifiers/public) che come [Shared](/dotnet/visual-basic/language-reference/modifiers/shared). Un operatore di conversione, invece, può essere dichiarato con [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) o [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) ma non entrambi.  
  
 Una definizione di operatore può includere facoltativamente le parole chiave [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) e [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows). Non sono consentite altre parole chiave in un'[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement).  
  
 **ID errore:** BC33019  
  
### Per correggere l'errore  
  
1.  Rimuovere la parola chiave `Widening` o `Narrowing` dalla definizione dell'operatore. Queste parole chiave non sono applicabili perché non viene eseguita alcuna conversione di tipi.  
  
## Vedere anche  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)