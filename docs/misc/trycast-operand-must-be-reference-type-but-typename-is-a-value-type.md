---
title: "L&#39;operando &#39;TryCast&#39; deve essere un tipo riferimento, ma &#39;&lt;nometipo&gt;&#39; &#232; un tipo valore | Microsoft Docs"
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
  - "BC30792"
  - "vbc30792"
helpviewer_keywords: 
  - "BC30792"
ms.assetid: 3325fce5-dbc0-4d1d-9530-31f4720bfe6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L&#39;operando &#39;TryCast&#39; deve essere un tipo riferimento, ma &#39;&lt;nometipo&gt;&#39; &#232; un tipo valore
L'operatore `TryCast` è usato con un tipo valore per almeno uno degli argomenti.  
  
 `TryCast` esegue un test per individuare una relazione di ereditarietà o implementazione tra i due argomenti. Pertanto, consente solo tipi riferimento per gli argomenti. Per altre informazioni, vedere [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types).  
  
 **ID errore:** BC30792  
  
### Per correggere l'errore  
  
-   Usare `DirectCast` o `CType` per eseguire la conversione. Entrambi consentono tipi valore.  
  
## Vedere anche  
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [Funzione CType](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)